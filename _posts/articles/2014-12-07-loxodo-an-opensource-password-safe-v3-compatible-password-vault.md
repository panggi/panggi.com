---
layout: post
title: "Loxodo: an open source Password Safe V3 compatible password vault"
modified:
categories: articles
excerpt: "Loxodo is a multi-platform open source software written in python for managing your passwords securely and based on Bruce Schneier's Password Safe"
tags: [security, python]
image:
  feature: featured/security.jpg
  credit: wallpoper
  creditlink: http://wallpoper.com/wallpaper/cryptography-278319
date: 2014-12-07T19:17:25+07:00
comments: true
---

## Introduction

**Loxodo** is a multi-platform open source software written in python for managing your passwords securely and based on Bruce Schneier's "[Password Safe](https://www.schneier.com/passsafe.html)" that's also an open source software that runs on Windows and Linux for now.

<figure>
  <img src="/images/post/2014-12-07-loxodo-an-opensource-password-safe-v3-compatible-password-vault/loxodo.png" alt="loxodo">
</figure>

From the Schneier's blog we can see that this software is using Twofish encryption algorithm which was made by Schneier himself.

> Password Safe protects passwords with the Twofish encryption algorithm, a fast, free alternative to DES. The program's security has been thoroughly verified by Counterpane Labs under the supervision of Bruce Schneier, author of Applied Cryptography and creator of the Twofish algorithm. -- https://www.schneier.com/passsafe.html

## Installation on OSX

    {% raw %}
    
    $ brew install wxpython
    $ mkdir -p /Users/username/Library/Python/2.7/lib/python/site-packages
    $ echo 'import site; site.addsitedir("/usr/local/lib/python2.7/site-packages")' >> /Users/username/Library/Python/2.7/lib/python/site-packages/homebrew.pth
    $ wget https://github.com/sommer/loxodo/archive/master.tar.gz
    $ tar xvzf master.tar.gz
    $ cd loxodo-master
    $ ./setup.py py2app
    
    {% endraw %}

If all goes well, your **Loxodo.app** will be at **dist** directory inside **loxodo-master**. Move that file to **Applications** directory and you are good to go.

## Usage

* Open Loxodo.app
* Chose your file name and path for your new psafe3 database
* Fill the password with the password you want
* click "New"
* click "Save"
* Now you are ready to use it, click "Open"
* Enjoy!

## Tips

* You can use cloud storage such as **Dropbox** or **Copy** to store your password database so if somehow you can not access your computer for some reason, you still can get your password database through cloud.
* If you want more protection, you can double encrypt the database using software like [TrueCrypt](http://www.panggi.com/articles/secure-cloud-storage-using-truecrypt/)
