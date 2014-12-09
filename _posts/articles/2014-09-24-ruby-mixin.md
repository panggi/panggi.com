---
layout: post
title: "Ruby Mixin"
modified:
categories: articles
excerpt: "Ruby class can inherit from only one parent, called a *superclass* and it does not support multiple inheritance (inherit features from more than one parent class), but Ruby has a powerful feature called *mixin*."
tags: [ruby]
image:
  feature: featured/ruby.jpg
date: 2014-09-24T21:12:17+07:00
comments: true
---

Ruby class can inherit from only one parent, called a *superclass* and it does not support multiple inheritance (inherit features from more than one parent class), but Ruby has a powerful feature called *mixin*.

**Mixin** is a class that is mixed with a module so the implementation of the class and module are combined. In Ruby, a **module** is a collection of functions and constants. When we include a module in a class, the behaviours and constants of the module become part of the class.

Let me give you an example:

{% highlight ruby %}

module Randomize
  def generate
    "#{prefix}_#{rand(1000)}"
  end
end

class SerialNumber
  include Randomize
  attr_accessor :code

  def initialize(code)
    @code = code
  end

  def prefix
    code
  end
end

SerialNumber.new("c3p0").generate

{% endhighlight ruby %}

The sample output is "c3p0_391", and the interesting part is the intimacy between class and module in this mixin relationship. We can see that *prefix* is used in module but implemented in the class. We can add more mixins to the SerialNumber class and create subclasses of it and then each subclass will have functionality of all the mixins. **So in Ruby we can use single inheritance to define a class and attach additional functionalities with modules**.

**References:**

* [Ruby Modules and Mixins](http://www.tutorialspoint.com/ruby/ruby_modules.htm)
* [Ruby Mixin Tutorial](http://juixe.com/techknow/index.php/2006/06/15/mixins-in-ruby/)

