---
layout: post
title: "Get list of Tor exit IP addresses using Ruby"
modified:
categories: articles
excerpt:
tags: [ruby, tor, privacy, security]
image:
  feature: featured/ruby.jpg
date: 2015-06-18T00:11:18+07:00
comments: true
---

You know [Tor](https://www.torproject.org), and i don't have to explain it to you about this cool opensource project. In this post i'm going to show you how to get list of all near real time IP addresses of Tor exit nodes using Ruby.

Basically there are three simple steps in this implementation:

* Get the newest Tor exit nodes data from [https://check.torproject.org/exit-addresses](https://check.torproject.org/exit-addresses)
* Get all the ip addresses from that data by using regex
* Store them to a file

And here is the implementation in Ruby:

{% highlight ruby %}

require 'net/http'
require 'uri'

tor_exits_url = 'https://check.torproject.org/exit-addresses'
start_time = Time.now
raw_tor_exits = Net::HTTP.get(URI.parse(tor_exits_url))

if raw_tor_exits
  ips = raw_tor_exits.scan(/\b(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\b/)
  if ips
    filename = "tor-list-#{Time.now.to_i}.txt"
    write_to_file = File.open(filename, 'w') { |file| file.write(ips) }
    end_time = Time.now
    if write_to_file
      puts "Successfully written to #{filename} with #{ips.count} IP addresses in #{end_time - start_time} sec(s)"
    else
      puts "Can't store IP addresses to #{filename}"
    end
  else
    puts "Can't extract IP addresses form raw data"
  end
else
  puts "Can't get raw Tor IPs"
end

{% endhighlight ruby %}

Run it:

   {% raw %}
    $ ruby get_tor_list.rb
    $ Successfully written to tor-list-1434561916.txt with 1180 IP addresses in 4.045044 sec(s)
   {% endraw %}

The file contains an array of IP addresses:

   {% raw %}
    $ cat tor-list-1434561916.txt
    $ ["162.247.72.201", "24.187.20.8", "162.248.160.151", "193.34.117.51",...]
   {% endraw %}

Now you can use these IP addresses for whatever you want like blocking the access of anyone with these IP addresses that visits your site.
