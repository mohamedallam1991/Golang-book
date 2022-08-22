---
title: "Algo: Complexity and Performance"
# slug: "golang-variables"
url: Concurency

date: 2022-08-16
description: This article teaches you everything you need to know about Concurency in Golang
lead: Lets learn Golang Concurency, how to declare them and how to use them.
# date: 2022-08-15T14:00:00.000Z
# series: ['Golang', 'Beginner']
categories:
  - "Golang"
tags:
  - "Golang"
  - "Algo"

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

The efficiency of an algorithm is measured through this parameters
<!--more-->

## Intro
The efficiency of an algorithm is measured through various parameters, such as CPU time, memory, disk, and network. The complexity is how the algorithm scales when the number of input parameters increases. Performance is a measure of time, space, memory, and other parameters. Algorithms are compared by their processing time and resource consumption. Complexity measures the parameters and is represented by the Big O notation.

## Complexity analysis of algorithms

The complexity of an algorithm is measured by the speed of the algorithm. Typically, the algorithm will perform differently based on processor speed, disk speed, memory, and other hardware parameters. Hence, asymptotical complexity is used to measure the complexity of an algorithm. An algorithm is a set of steps to be processed by different operations to achieve a task. The time taken for an algorithm to complete is based on the number of steps taken.
Let's say an algorithm iterates through an array, m, of size 10 and update the elements to the sum of index and 200. The computational time will be 10*t, where t is the time taken to add two integers and update them to an array. The next step will be printing them after iterating over an array. The t  time parameter will vary with the hardware of the computer used. Asymptotically, the computational time grows as a factor of 10, as shown in the following code:


### Linear

An algorithm is of linear complexity if the processing time or storage space is directly proportional to the number of input elements to be processed. In Big O notation, linear complexity is presented as O(n). String matching algorithms such as the Boyer-Moore and Ukkonen have linear complexity.
Linear complexity, O(n), is demonstrated in an algorithm as follows:

```go
func main() {
	var m [10]int
	var k int
	for k = 0; k < 10; k++ {
		m[k] = k * 200
		fmt.Printf("Element[%d] = %d\n", k, m[k])
	}
}
```
>>

### Quadratic

An algorithm is of quadratic complexity if the processing time is proportional to the square of the number of input elements. In the following case, the complexity of the algorithm is 10*10 = 100. The two loops have a maximum of 10. The quadratic complexity for a multiplication table of n elements is O(n2).
Quadratic complexity, O(n2), is shown in the following example:

```go
func main() {
	var k, l int
	for k = 1; k <= 10; k++ {
		fmt.Println("Multiplication table", k)
		for l = 1; l <= 10; l++ {
			var x int = l * k
			fmt.Println(x)
		}
	}
}
```
> 10 multiplication tables

### Cubic

In the case of cubic complexity, the processing time of an algorithm is proportional to the cube of the input elements. The complexity of the following algorithm is 10*10*10 = 1,000. The three loops have a maximum of 10. The cubic complexity for a matrix update is O(n3).
Cubic complexity O(n3) is explained in the following example:

```go

func main() {
	var k, l, m int
	var arr [10][10][10]int
	for k = 0; l < 10; k++ {
		for l = 0; l < 10; l++ {
			for m = 0; m < 10; m++ {
				arr[k][l][m] = l
				fmt.Println("Element value ", k, l, m, " is", arr[k][l][m])
			}
		}
	}
}
```
### Logarithmic

An algorithm is of logarithmic complexity if the processing time is proportional to the logarithm of the input elements. The logarithm base is typically 2. The following tree is a binary tree with LeftNode and RightNode. The insert operation is of O(log n) complexity, where n is the number of nodes.
Logarithmic complexity is presented as follows:
```go
func main() {
	var tree *Tree = &Tree{nil, 1, nil}
	print(tree)
	tree.insert(3)
	print(tree)
	tree.insert(5)
	print(tree)
	tree.LeftNode.insert(7)
	print(tree)
}

type Tree struct {
	LeftNode  *Tree
	Value     int
	RightNode *Tree
}

func (tree *Tree) insert(m int) {
	if tree != nil {
		if tree.LeftNode == nil {
			tree.LeftNode = &Tree{nil, m, nil}
		} else {
			if tree.RightNode == nil {
				tree.RightNode = &Tree{nil, m, nil}
			} else {
				if tree.LeftNode != nil {
					tree.LeftNode.insert(m)
				} else {
					tree.RightNode.insert(m)
				}
			}
		}
	} else {
		tree = &Tree{nil, m, nil}
	}
}

func print(tree *Tree) {
	if tree != nil {
		fmt.Println(" Value", tree.Value)
		fmt.Printf("Tree Node Left")
		print(tree.LeftNode)
		fmt.Printf("Tree Node Right")
		print(tree.RightNode)
	} else {
		fmt.Printf("Nil\n")
	}
}
```
