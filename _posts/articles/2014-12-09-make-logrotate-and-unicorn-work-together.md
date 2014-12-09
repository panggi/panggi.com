---
layout: post
title: "Make logrotate and unicorn work together"
modified:
categories: articles
excerpt: "Rotate Rails log and make sure that after log rotation happened, the production.log will be written normally."
tags: [ruby,linux]
image:
  feature: featured/ruby.jpg
date: 2014-12-09T16:48:59+07:00
comments: true
---

## Objective

Rotate Rails log and make sure that after log rotation happened, the **production.log** will be written normally.

## Solution

* Create init script for restarting rails app with unicorn as http server
* Create logrotate for rotating rails log in timeframe and restart rails app after log rotation finished

## Codes

    {% raw %}
    # touch /etc/init.d/rails
    # chmod +x /etc/init.d/rails
    # chown username:username /etc/init.d/rails
    {% endraw %}

**File: /etc/init.d/rails**

    {% raw %}
    #!/bin/sh
    set -e
    
    TIMEOUT=${TIMEOUT-60}
    RAILS_ENV=production
    APP_ROOT=/opt/username/current
    PID=$APP_ROOT/tmp/pids/unicorn.pid
    PATH=$PATH:/home/username/.rbenv/shims
    CMD="$APP_ROOT/bin/unicorn -D -c $APP_ROOT/config/unicorn.rb -E $RAILS_ENV"
    action="$1"
    set -u
    
    old_pid="$PID.oldbin"
    
    cd $APP_ROOT || exit 1
    
    sig () {
      test -s "$PID" && kill -$1 `cat $PID`
    }
    
    oldsig () {
      test -s $old_pid && kill -$1 `cat $old_pid`
    }
    
    case $action in
    start)
      sig 0 && echo >&2 "Already running" && exit 0
      $CMD
      ;;
    stop)
      sig QUIT && exit 0
      echo >&2 "Not running"
      ;;
    force-stop)
      sig TERM && exit 0
      echo >&2 "Not running"
      ;;
    restart|reload)
      sig HUP && echo reloaded OK && exit 0
      echo >&2 "Couldn't reload, starting '$CMD' instead"
      $CMD
      ;;
    upgrade)
      if sig USR2 && sleep 2 && sig 0 && oldsig QUIT
      then
        n=$TIMEOUT
        while test -s $old_pid && test $n -ge 0
        do
          printf '.' && sleep 1 && n=$(( $n - 1 ))
        done
        echo
    
        if test $n -lt 0 && test -s $old_pid
        then
          echo >&2 "$old_pid still exists after $TIMEOUT seconds"
          exit 1
        fi
        exit 0
      fi
      echo >&2 "Couldn't upgrade, starting '$CMD' instead"
      $CMD
      ;;
    reopen-logs)
      sig USR1
      ;;
    *)
      echo >&2 "Usage: $0 <start|stop|restart|upgrade|force-stop|reopen-logs>"
      exit 1
      ;;
    esac
    {% endraw %}

**File: /etc/logrotate.d/rails-logs**

    {% raw %}
    /opt/username/shared/log/*log {
        create 0644 username username
        su root username
        daily
        rotate 1
        compress
        missingok
        notifempty
        sharedscripts
        postrotate
            service rails restart > /dev/null 2>/dev/null || true
        endscript
    }
    {% endraw %}
