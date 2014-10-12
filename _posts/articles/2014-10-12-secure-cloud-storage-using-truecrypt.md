---
layout: post
title: "Secure Cloud Storage Using TrueCrypt"
modified:
categories: articles
excerpt: "Yes, I know that if you visit www.truecrypt.org, there is a warning not to use it anymore. But many people thought it’s weird and they do things to make sure the FOSS encryption tool will still be available for use."
tags: [security]
image:
  feature: featured/security.jpg
  credit: wallpoper
  creditlink: http://wallpoper.com/wallpaper/cryptography-278319
date: 2014-10-12T22:48:57+07:00
comments: true
---

<figure>
  <img src="/images/post/2014-10-12-secure-cloud-storage-using-truecrypt/truecrypt.png" alt="truecrypt">
</figure>
Yes, I know that if you visit [www.truecrypt.org](http://www.truecrypt.org), there is a warning not to use it anymore.

But many people thought it's weird and they do things to make sure the FOSS encryption tool will still be available for use.

One of them is ["Open Crypto Audit Project"](https://opencryptoaudit.org/) with [Bruce Schneier](https://opencryptoaudit.org/people) as one of it's Technical Advisory Board.

The Windows version of the tool had also been [audited](https://opencryptoaudit.org/reports/iSec_Final_Open_Crypto_Audit_Project_TrueCrypt_Security_Assessment.pdf) and from the report we can see the conclusion:

> Finally, iSEC found no evidence of backdoors or otherwise intentionally malicious code in the assessed areas. The vulnerabilities described later in this document all appear to be unintentional, introduced as the result of bugs rather than malice.

With that in mind, i'm still in faith using TrueCrypt as one of my security tool.

##Client side encryption for your cloud files

I don't trust any commercial cloud storage on the market for now, and this post is agnostic whether you use Dropbox, Copy or any other cloud storage.

So, basically what we're trying to do is to create *mountable encrypted file container*. It's like having an encrypted hard drive that you can access anywhere.

First thing first, you need to download TrueCrypt from the trusted source. My recommendation is to download the binaries from [github](https://github.com/AuditProject/truecrypt-verified-mirror?files=1) that is managed by Open Crypto Audit Project.

**After downloaded and installed, you can follow these steps:**

* Open TrueCrypt
* Click '**Create Volume**'
* Choose '**Create an encrypted file container**' and click '**Next**'
* Choose '**Standard TrueCrypt volume**' at the '**Volume Type**' section and click '**Next**'
* At '**Volume Location**' section, click '**Select File**' and choose the directory and file name for your container, you can directly chose the dropbox, copy or other directory to save the file. After done with it, click '**Next**'
* At '**Encryption Options**' you can chose the '**Encryption Algorithm**' and '**Hash Algorithm**', my recommendation for Encryption Algorithm is to use the multiple Algorithm such as *Serpent-Twofish-AES*. Click '**Next**' to continue.
* Now you can configure how big your file is at '**Volume Size**' section. Click '**Next**' to continue.
* Enter the password you like at '**Volume Password**' section, make sure it's a strong one. Again, click '**Next**' to continue.
* Choose the Filesystem type at '**Format Options**' section and click '**Next**' to continue
* At '**Cross Platform Support**', in my case choose between '**I will mount the volume on the other platforms**' or '**I will mount the volume only on Mac OS X**'. Clict '**Next**' to continue.
* Move your mouse as randomly as possible and as long as possible to increase the cryptographic strength of the encryption keys. Click '**Format**' if you think it's enough for cursor-moving thing.
* Done! you may exit the wizard.

Now the file is created and your cloud storage service is uploading it to their server.

**Storing files to the encrypted container**

* Open TrueCrypt
* Choose the empty slot of drive.
* Click '**Select File**' and choose your newly created file
* Click '**Mount**' and enter the password
* New drive is mounted and you can store your files to that drive and unmount it if it's done.

**Tip for you:**
Don't make the file size too big because everytime you modify the content of the container, you have to upload all over again because it will encrypt all the container file and dropbox or copy will think that the file is completely new.

