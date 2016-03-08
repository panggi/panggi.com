---
layout: post
title: "Add Dynamic Environment Variable to Dockerfile"
modified:
categories: articles
excerpt:
tags: [docker, linux]
image:
  feature: featured/docker.jpg
date: 2016-03-08T16:40:52+07:00
comments: true
---

**Problem**

Let say your application has these environments (development, staging, sandbox and production) as the option to run with different configuration depends on current environment.

And you also want to deploy them using [docker](http://www.docker.com) and maintain the ability to use environment variable like NODE_ENV, RAILS_ENV etc.


**Solution**

Create script for docker build and modify Dockerfile to accept environment variable


**Code**

* create_docker_image

<script src="https://gist.github.com/panggi/cf68fcf43689ee134292.js"></script>

* Dockerfile

<script src="https://gist.github.com/panggi/bf61edb9ff1cca60e23e.js"></script>

**How to run**

    {% raw %}
    $ chmod +x create_docker_image
    $ ./create_docker_image sandbox
    {% endraw %}
