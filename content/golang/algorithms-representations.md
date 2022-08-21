---
title:  The 2 Algorithms representations
# slug: "golang-variables"
url: algorithms-representations

date: 2022-08-21
description: Two ways to represent an algorithm.
lead: Algorithms are generally represented in two ways
# date: 2022-08-15T14:00:00.000Z
# series: ['Golang', 'Beginner']
categories:
  - "Golang"
tags:
  - "Golang"
  - "Beginner"

sidebar: true
pager: false
toc: true
# weight: 2

authorbox: true # Enable authorbox for specific page
pager: false # Enable pager navigation (prev/next) for specific page
toc: true # Enable Table of Contents for specific page
comments: false # Enable Disqus comments for specific page
mathjax: false # Enable MathJax for specific page
widgets:
  - "search"
  - "recent"
  - "taglist"

---

An algorithm is a plan, a set of step-by-step instructions to resolve a problem. And there is two ways to represent that.

<!--more-->

## Pseudocode

A method of writing up a set of instructions for a computer program using plain English. This is a good way of planning a program before coding.

Pseudocode is a kind of structured english for describing algorithms. It allows the designer to focus on the logic of the algorithm without being distracted by details of language syntax.  At the same time, the pseudocode needs to be complete.  It describe the entire logic of the algorithm so that implementation becomes a rote mechanical task of translating line by line into source code.
In general the vocabulary used in the pseudocode should be the vocabulary of the problem domain, not of the implementation domain.  The pseudocode is a narrative for someone who knows the requirements (problem domain) and is trying to learn how the solution is organized.  E.g.,

Extract the next word from the line (good)
set word to get next token (poor)
Append the file extension to the name (good)
name = name + extension (poor)

FOR all the characters in the name (good)
FOR character = first to last (ok)


[Source](http://users.csc.calpoly.edu/~jdalbey/SWE/pdl_std.html)


## Flow chart

A diagram that shows a process, made up of boxes representing steps, decision, inputs and outputs. of an algorithm

[Flowchart](https://en.wikipedia.org/wiki/Flowchart) is the second type of representing an algorithm
