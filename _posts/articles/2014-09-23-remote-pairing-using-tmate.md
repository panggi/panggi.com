---
layout: post
title: "Remote pairing using tmate"
modified:
categories: articles
excerpt: "Do remote pairing using tmate and vim"
tags: [agile]
image:
  feature: featured/tmate.png
  credit: tmate.io
  creditlink: http://tmate.io
date: 2014-09-23T11:46:34+07:00
comments: true
---

##Pair programming

**Pair programming** is a method of programming in which two people work together at a single computer. One person as '**the driver**' and the other person as the '**observer**' who reviews each line of code as it is typed.

Pair programming has some benefits: fewer bugs (increased quality), improved skills, and faster delivery. With increased quality comes big savings later in the project. It takes time to get used to pair programming so don't worry if it feels awkward at first.

Based on my experience, the best way to pair program is to use 1 computer, 2 monitors, 2 keyboards and 2 mice just like what i've learned from [neo](http://www.neo.com) guys.

<figure>
	<a href="/images/post/2014-09-23-remote-pairing-using-tmate/pairing.jpg"><img src="/images/post/2014-09-23-remote-pairing-using-tmate/pairing.jpg" alt="image"></a>
	<figcaption><a href="http://weilu.github.io/reddot2012/" title="neo guys doing pair programming">neo guys doing pair programming</a>.</figcaption>
</figure>

But what happens when you want to pair with someone in another city or country? or when there is a time that you can't come to office but still want to do pair programming with your pair buddy? the answer is **Remote pairing**

##Remote pairing using tmate

Using [tmate](http://tmate.io) for remote pairing is easy:

* **Launch**: run tmate
* **Share**: share the session with your partner
* **Pair**: done! you can start pairing

<figure class="half">
  <img src="/images/post/2014-09-23-remote-pairing-using-tmate/01.png" alt="image">
  <img src="/images/post/2014-09-23-remote-pairing-using-tmate/02.png" alt="image">
  <figcaption>Create tmate session and copy the Remote session.</figcaption>
</figure>
<figure class="half">
  <img src="/images/post/2014-09-23-remote-pairing-using-tmate/05.png" alt="image">
  <figcaption>share to your partner and let them open the ssh session on their computer.</figcaption>
</figure>
<figure class="half">
  <img src="/images/post/2014-09-23-remote-pairing-using-tmate/04.png" alt="image">
  <img src="/images/post/2014-09-23-remote-pairing-using-tmate/07.png" alt="image">
  <figcaption>Now both of you can start pairing.</figcaption>
</figure>

##tmate installation and usage

You can see clear explanation on how to install it at [http://tmate.io](http://tmate.io)

Basically there are two types of usage after you finished installing tmate:

* **Using tmate.io server** : what you have to do is just run the tmate and it will give you tmate session using tmate.io server
* **Using your own hosted tmate server** : you need to install tmate-slave on your server and connect to it by setting up your ~/.tmate.conf file
