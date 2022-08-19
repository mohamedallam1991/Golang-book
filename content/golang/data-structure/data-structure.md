---
title: Data structure
# slug: "golang-variables"
url: data-structure-golang

date: 2022-08-16
description: Lets talk data structure in Golang
lead: Golang, Data structure is awesome, lets figure out how
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

Data Structure, and Algorithms, boring? now, this article shows you how
<!--more-->

## What is data structure?
[Data structure - Wiki](https://en.wikipedia.org/wiki/List_of_data_structures)
Its how we organize data in a cheap yet efficient way, As there different ways to handle the workload, Nonetheless, It dosen’t matter what programming language you write, it always boiles down to:
- Allocating memory of certain size or representation
- Reading memory
- Writing to memory

And the data structure we can wanna tackle:

| Linear  | Non-Linear       | Homogeneous   | Heterogeneous | Dynamic       |
| ------- | ---------------- | ------------- | ------------- | ------------- |
| Lists   | Trees            | 2D arrays     | Linked Lists    | Dictionaries |
| Sets    | Tables           | MultiDArrays  | Ordered Lists   | TreeSets     |
| Tuples  | Containers       |               | UnOrdered Lists | Sequences    |
| Queues  |                  |               |          |           |
| Stacks  |                  |               |           |           |
| Heaps   |                  |               |           |           |

## Linear

### Lists
[List (abstract data type) - Wiki](https://en.wikipedia.org/wiki/List_(abstract_data_type))

Back in 1956 [Allen Newell, Herbert A. Simon, and Cliff Shaw](https://en.wikipedia.org/wiki/Logic_Theorist). At [RAND Corporation](https://en.wikipedia.org/wiki/RAND_Corporation)
A list is a sequence of elements. Each element can be connected to another with a link in a forward or backward direction.
The element can have other payload properties. This data structure is a basic type of container. Lists have a variable length, we can add or remove an element easily than an array.
The data dont need to be contigious, wether in memory or on disk.

`numbers = [ 1, 2, 3, 4, 5]`


```go
package main

import (
	"container/list"
	"fmt"
)

func main() {
	var strList list.List
	myProfile := struct {
		Id   int
		Name string
	}{1, "Mohamed"}

	strList.PushBack("John Doe")
	strList.PushBack(myProfile)
	strList.PushBack(211)

	for element := strList.Front(); element != nil; element = element.Next() {
		fmt.Println(element.Value)
	}
}

```

>John Doe

>{1 Mohamed}

>211


### Tuples
[Tuple Wiki](https://en.wikipedia.org/wiki/Tuple)
A tuple is a finite sorted list of elements. It is a data structure that groups data.  Tuples are typically immutable sequential collections. The element has related fields of different datatypes. The only way to modify a tuple is to change the fields. Operators such as + and * can be applied to tuples. A database record is referred to as a tuple. In the following example, power series of integers are calculated and the square and cube of the integer is returned as a tuple:

```go
package main

import "fmt"

func powerSeries(a int) (square int, cube int, err error) {
	square = a * a
	cube = square * a
	//if we need to check for error, and return the error
	return square, cube, nil
}

func main() {
	var square int
	var cube int
	// The tuple
	square, cube, _ = powerSeries(3)

	fmt.Println("Square", square, "Cube", cube)
}
```
>
> Square 9 Cube 27
### Heaps
[Heaps - Wiki](https://en.wikipedia.org/wiki/Heap_(data_structure))

A heap is a data structure that is based on the heap property. The heap data structure is used in selection, graph, and k-way merge algorithms. Operations such as finding, merging, insertion, key changes, and deleting are performed on heaps. Heaps are part of the container/heap package in Go. According to the heap order (maximum heap) property, the value stored at each node is greater than or equal to its children.
If the order is descending, it is referred to as a maximum heap; otherwise, it's a minimum heap. The heap data structure was proposed by [J.W.J. Williams](https://en.wikipedia.org/wiki/J._W._J._Williams) in 1964 for a heap sorting algorithm. It is not a sorted data structure, but partially ordered. The following example shows how to use the `container/heap` package to create a heap data structure:
```go
package main

import (
	"container/heap"
	"fmt"
)

type IntegerHeap []int

// get the length of the heap
func (iheap IntegerHeap) Len() int {
	return len(iheap)
}

//Checks if i index is less than j index
func (iheap IntegerHeap) Less(i, j int) bool {
	return iheap[i] < iheap[j]
}

// Pushes the item to the heap
func (iheap *IntegerHeap) Push(heapInterface interface{}) {
	*iheap = append(*iheap, heapInterface.(int))
}

// Pops the item from the heap
func (iheap *IntegerHeap) Pop() interface{} {
	var n int
	var x1 int
	var previous IntegerHeap = *iheap
	n = len(previous)
	x1 = previous[n-1]
	*iheap = previous[0 : n-1]
	return x1
}

//Swaps the element of i index to j index
func (iheap IntegerHeap) Swap(i, j int) {
	iheap[i], iheap[j] = iheap[j], iheap[i]
}

func main() {
	var intHeap *IntegerHeap = &IntegerHeap{1, 4, 5}
	fmt.Println("the heap : ", *intHeap)
	heap.Init(intHeap)
	heap.Push(intHeap, 2)
	fmt.Printf("minimum: %d\n", (*intHeap)[0])
	fmt.Println()
	for intHeap.Len() > 0 {
		fmt.Printf("%d \n", heap.Pop(intHeap))
	}
}


```

## Adapter Pattern
One of the most commonly used structural patterns is the [Adapter patern](https://refactoring.guru/design-patterns/adapter)
Adapter is a structural design pattern that allows objects with incompatible interfaces to collaborate.
The Adapter pattern is very useful for example, an interface gets outdated and it's not possible to replace it easily or fast. Instead, you create a new interface to deal with the current needs of your application, which, under the hood, uses implementations of the old interface.
Adapter also helps us to maintain the [Open/Closed principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle) in our apps, making them more predictable too. They also allow us to write code which uses some base that we can't modify.

> The open/closed principle was first stated by [Bertrand Meyer](https://en.wikipedia.org/wiki/Bertrand_Meyer) in his book [Object-Oriented Software Construction](https://en.wikipedia.org/wiki/Object-Oriented_Software_Construction). He stated that code should be open to new functionality, but closed to modifications. What does it mean? Well, it implies a few things. On one hand, we should try to write code that is extensible and not only one that works. At the same time, we should try not to modify the source code (yours or other people's) as much as we can, because we aren't always aware of the implications of this modification. Just keep in mind that extensibility in code is only possible through the use of design patterns and interface-oriented programming.

The adpter pattern comprises:
- The adapter: Translates the incompatible interface of the adaptee into an interface that the client wants.
- The target: The interface that the client calls and invokques methods on the adapter and adaptee
- The adaptee: The old adapter, that we want to keep but use a newer adapter on top of.
- The client: Wants an incompatible interface implemented by the adapter
