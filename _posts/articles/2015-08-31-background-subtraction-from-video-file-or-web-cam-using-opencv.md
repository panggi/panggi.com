---
layout: post
title: "Background Subtraction from Video File or Web Cam Using OpenCV"
modified:
categories: articles
excerpt: "Background Subtraction from video file of web cam using OpenCV and MOG algorithm"
tags: [python, opencv]
image:
  feature: featured/python.png
date: 2015-08-31T04:55:59+07:00
comments: true
---

This article is based on [OpenCV Documentation](http://docs.opencv.org/master/db/d5c/tutorial_py_bg_subtraction.html) with 2 additional features:

* Ability to get video source from argument
* Ability to capture video from webcam

I am using video files by [ISE Lab, CVC Barcelona](http://iselab.cvc.uab.es/silverage.php?q=cvc_zebra) and MOG as the algorithm.

Here is the source code:

{% highlight ruby %}

import cv2
import argparse

ap = argparse.ArgumentParser()
ap.add_argument("-v", "--video",
  help = "path to the (optional) video file")
args = vars(ap.parse_args())

if not args.get("video", False):
  cap = cv2.VideoCapture(0)
else:
  cap = cv2.VideoCapture(args["video"])

fgbg = cv2.BackgroundSubtractorMOG()

while True:
    ret, frame = cap.read()

    fgmask = fgbg.apply(frame)

    cv2.imshow('frame',fgmask)
    k = cv2.waitKey(30) & 0xff
    if k == 27:
        break

cap.release()
cv2.destroyAllWindows()

{% endhighlight ruby %}

**Result:**

Original frame sample:
<figure>
  <img src="/images/post/2015-08-31-background-subtraction-from-video-file-or-web-cam-using-opencv/real-video.png" alt="Original frame sample">
</figure>

BackgroundSubtractorMOG frame sample:
<figure>
  <img src="/images/post/2015-08-31-background-subtraction-from-video-file-or-web-cam-using-opencv/mog-subtracted-video.png" alt="BackgroundSubtractorMOG frame sample">
</figure>
