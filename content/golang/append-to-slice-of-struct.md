---
title: Append to slice of struct
# slug: "golang-variables"
url: append-to-slice-of-struct

date: 2022-08-16
description: Lets append more struct-type to our slice of struct.
lead: Implement append, to a slice of structs.
# date: 2022-08-15T14:00:00.000Z
# series: ['Golang', 'Beginner']
categories:
  - "Golang"
tags:
  - "Golang"
#   - "Structs"

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


Lets append more values to a slice of struct, or an array of struct
<!--more-->

## Append values to a slice


```go

type Key struct {
    Name string
}

type Keyboard struct {
    Keys []Key
}

func (kboard *Keyboard) AddKey(k Key) []Key {
	kboard.Keys = append(kboard.Keys, k)
	return kboard.Keys
}
func main() {

	// myKey1 := Key{Name: "Test Key 1", Role: "Upper"}
	myKey1 := Key{Name: "Test Key 1"}
    myKeyboard := Keyboard{}
	myKeyboard.AddKey(myKey1)
	myKeyboard.AddKey(Key{Name: "Test Key 2"})

    fmt.Println(len(myKeyboard.Keys))
	fmt.Println(myKeyboard.Keys)
}
```
To print out
> 2
>
> [{Test Key 1 } {Test Key 2 }]

## Append values to an array


```go
type Key struct {
	Name string
}

type EnKeyboard struct {
	Keys [5]Key
}

func (kboard *EnKeyboard) AddKeyToEn(k Key) []Key {
	for i, v := range kboard.Keys {
		if v.Name == "" || len(v.Name) < 1 {
			kboard.Keys[i] = k
			return kboard.Keys[:]
		}
	}
	return kboard.Keys[:]
}
func main (){
    func main() {
	myKey1 := Key{Name: "En Key 1"}
	myEnKeyboard := EnKeyboard{}

	myEnKeyboard.AddKeyToEn(myKey1)
	myEnKeyboard.AddKeyToEn(Key{Name: "En Key 2"})

	fmt.Println(len(myEnKeyboard.Keys))
	fmt.Println(myEnKeyboard.Keys)
}
```
> 5
>
> [{En Key 1} {En Key 2} {} {} {}]
