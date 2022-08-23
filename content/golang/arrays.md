---
title: Golang arrays guide
# slug: "golang-variables"
url: arrays

date: 2022-08-16
description: This article teaches you everything you need to know about arrays in Golang
lead: Lets learn Golang arrays, how to declare them and how to use them.
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


After you finish this article you will start playing with arrays like pawns

<!--more-->

## Intro

Arrays are one of the most famous data structures in different programming languages. Different data types can be handled as elements in arrays such as int, float23, double and others The following code snippet shows the initialiazation of an array (array.go):

```go
var arr = [4]int{1,4,5,6}
```

An Array has a size or a length which can found by

```go
len(arr)
```

### Array elements

To access the array elements there is two different ways:

- We loop through the array, by figuring out its length
```go
var i int
for i =0; i<len(arr); i++{
    fmt.Println("priting elements ", arr(i))
}
```
- We range through the elements and assign, index value to the array
```go
for i,v := range arr{
    fmt.Println("priting elements ",i, v)
}
```
### Ignoring the index
If we need to ignore the index we can use the _ blank identifier
```go
for _,v := range arr{
    fmt.Println("priting elements ",i, v)
}
```


[https://go.dev/blog/slices-intro](https://go.dev/blog/slices-intro)
[Arrays, slices (and strings): The mechanics of 'append'](https://go.dev/blog/slices)
[https://stackoverflow.com/questions/33834742/remove-and-adding-elements-to-array-in-go-lang](https://stackoverflow.com/questions/33834742/remove-and-adding-elements-to-array-in-go-lang)
[Append to slice or array of struct page]({{< relref "/golang/append-to-slice-of-struct.md" >}} "Arrays article").
