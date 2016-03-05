---
layout: post
title: "SMS Spam Filter using scikit-learn and TextBlob"
modified:
categories: articles
excerpt: "SMS Spam Filter using scikit-learn and TextBlob with Support Vector Machine and Naive Bayes Machine Learning Algorithm"
tags: [python, scikitlearn, textblob, nlp, machinelearning]
image:
  feature: featured/python.png
date: 2016-03-06T00:36:16+07:00
comments: true
---

Repository : [https://github.com/panggi/sms-spam-detector](https://github.com/panggi/sms-spam-detector)

Written in Python 2.7 using Naive Bayes and SVM for Classifier

## How to run
{% raw %}

    $ python sms-spam-detector.py -m "Hello, dude. what's up?"
    $ This message is predicted by SVM as ham and Naive Bayes as ham
    $ python sms-spam-detector.py -m "WINNER! Credit for free"
    $ This message is predicted by SVM as spam and Naive Bayes as spam

{% endraw %}
## TO DO
Don't load the models everytime the program get executed

## Credits
Dataset : [https://archive.ics.uci.edu/ml/datasets/SMS+Spam+Collection](https://archive.ics.uci.edu/ml/datasets/SMS+Spam+Collection)

Large portion of the codes are adapted from : [http://radimrehurek.com/data_science_python/](http://radimrehurek.com/data_science_python/)

<script src="https://gist.github.com/panggi/50b184e079d8fc5d7ad3.js"></script>

