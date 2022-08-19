---
title: Golang tricks
# slug: "golang-variables"
url: some-tricks-Golang

date: 2022-08-19
description: Some tricks you can sip in Golang
lead: Golang, is fun, and this are some tricks to use
# date: 2022-08-15T14:00:00.000Z
# series: ['Golang', 'Beginner']
categories:
  - "Golang"
tags:
  - "Golang"
  - "Tricks"

sidebar: true
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

Golang is a beautiful programming language, this tricks will make it even fun
<!--more-->


## mixed named and unnamed parameters
Is a known issue, where in a function you return same parameters with names, and you try to return the rest elements without a name for example, if you return the error here without giving it a name, you would run to the same problem
```go
func powerSeries(a int) (square int, cube int, error) {
	square = a * a
	cube = square * a
	//if we need to check for error, and return the error
	return square, cube, nil
}
```
So you have to chose one of those two
```go
func powerSeries(a int) (square int, cube int, someErrorName error) {
	square = a * a
	cube = square * a
	//if we need to check for error, and return the error
	return square, cube, nil
}
```
OR
```go
func powerSeries(a int) (int,int, error) {
	square = a * a
	cube = square * a
	//if we need to check for error, and return the error
	return square, cube, nil
}
```
