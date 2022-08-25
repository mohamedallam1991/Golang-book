---
title: Golang setup guide
# slug: "golang-variables"
url: enviroment

date: 2022-08-25
description: This is my Go setup
lead: This is how I am setting up Golang.
# series: ['Golang', 'Beginner']
categories:
  - "Golang"
tags:
  - "Golang"
  - "Beginner"
---

This the basic Golang setup for Mac Users.

<!--more-->

## Golang setup

This is a simple article to show you how to setup you Go enviroment properly, specailly if you are a homebrew user

If you installed Go, using home brew. `brew install golang`, you likely will have a slightly different setup than those installing Go from the original installation.
To map the actual GOROOT just use `brew --prefix golang` and then of course the libexec directory

Export bin, for both Goroot and Gopath.
```bash
# go working directory in my account and the bin
export GOPATH="/Users/mohamedallam/go"
export PATH="$PATH:$GOPATH/bin"

# You can instead # export GOPATH=/Users/$USER/go
# Or you can choose another directory  GOPATH=/Users/$USER/anotherDirectory

# go root directory (brew) with the bin
export GOROOT="$(brew --prefix golang)/libexec"
export PATH="$PATH:$GOROOT/bin"
```


Now you chould be able to

```bash
go version
go version go1.19 darwin/amd64
```

## Golang Godoc

Because Go is awesome, it does come with possibility to run the go documentation locally, which is called `godoc` to do so simply run this command
```bash
go install golang.org/x/tools/cmd/godoc@latest
```
Now to run it from anywhere
```bash
godoc -http=localhost:6060
```

Lunch your browser, visit `localhost:6060` and enjoy the beauty of Go.
