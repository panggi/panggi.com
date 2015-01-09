---
layout: post
title: "Matrix basic operations in Julia"
modified:
categories: articles
excerpt: "Julia provides easy way to play with Matrix"
tags: [julia, mathematics]
image:
  feature: featured/julia.png
  credit: julialang.org
  creditlink: http://julialang.org/images/gadfly-demo.png
date: 2015-01-09T12:29:49+07:00
comments: true
---

## Julia

Julia provides easy way to play with Matrix, you can see the full documentation at [http://docs.julialang.org/en/release-0.1-0/manual/arrays/](http://docs.julialang.org/en/release-0.1-0/manual/arrays/)

Below are some examples of basic operations of matrix in Julia.

**Addition**

    {% raw %}
    julia> A = [1 3 1; 1 0 0]
    2x3 Array{Int64,2}:
     1  3  1
     1  0  0
    
    julia> B = [0 0 5; 7 5 0]
    2x3 Array{Int64,2}:
     0  0  5
     7  5  0
    
    julia> +(A,B)
    2x3 Array{Int64,2}:
     1  3  6
     8  5  0
    {% endraw %}

**Scalar multiplication**

    {% raw %}
    julia> A = [1 8 -3; 4 -2 5]
    2x3 Array{Int64,2}:
     1   8  -3
     4  -2   5
    
    julia> 2.A
    2x3 Array{Float64,2}:
     2.0  16.0  -6.0
     8.0  -4.0  10.0
    {% endraw %}

**Transposition**

    {% raw %}
    julia> A = [1 2 3; 0 -6 7]
    2x3 Array{Int64,2}:
     1   2  3
     0  -6  7
    
    julia> A'
    3x2 Array{Int64,2}:
     1   0
     2  -6
     3   7
    {% endraw %}

**Matrix multiplication**

    {% raw %}
    julia> A = [2 3 4; 1 0 0]
    2x3 Array{Int64,2}:
     2  3  4
     1  0  0
    
    julia> B = [0 1000; 1 100; 0 10]
    3x2 Array{Int64,2}:
     0  1000
     1   100
     0    10
    
    julia> *(A,B)
    2x2 Array{Int64,2}:
     3  2340
     0  1000
    {% endraw %}
