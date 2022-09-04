---
title: "Working with concurrency in Go"
date: 2022-09-04
tags: ["100daysofcode", "learning-journey", "golang", "concurrency"]
---

Today's challenge is about working with concurrency in Go - Goroutines, Channels, and Pipelines. The following exercise is from the book, “Mastering Go: Create Golang production applications using network libraries, concurrency, machine learning, and advanced data structures” by Mihalis Tsoukalos. The book not only contains a lot of useful examples and best practices but also helps you understand the capability of Go in depth via well-written descriptions. I highly recommend reading through this book to keep your Go journey going smoothly and advance your programming skill with Go.

Here is the task we would like our program to achieve
> Create a pipeline that reads text files, finds the number of occurrences of a given phrase in each text file, and calculate the total number of occurrences of the phrase in all files.

The first part of the code is the most straightforward one where we pass file paths and a phrase to the program as the command-line argument, so the program knows which files to look for for the given phrase. A `for` loop is used to iterate each file, and we are going to create goroutines to read and count the number of occurrences in each one. Finally, we will gather results from all goroutines and sum up the total.

For example:

```go 
package main

import (
	"bufio"
	"fmt"
	"os"
	"sync"
	"sync/atomic"
)

var wg sync.WaitGroup
var ops int32

func main() {
	if len(os.Args) < 2 {
		fmt.Println("Need at least one phrase and file parameters!")
		return
	}
	phrase := os.Args[1]
	for i := 2; i < len(os.Args); i++ {
		fn := os.Args[i]
		// TO-DO: Reads the file and finds the number of occurrences of a given phrase
	}
	// TO-DO: Calculate total numbers of occurrences
	fmt.Println("total occurrences:", total)
}
```
Before we go to the next stage, we need to figure out how goroutines communicate with each other.
Golang provides a communication mechanism called “Channel” where goroutines can exchange data with others. Therefore, we can leverage Channel to collect outcomes from other goroutines like the code segment below. It takes whatever inputs from the channel(chan keyword) `in`  and sums them up.
```go
func sum(in <-chan int) int {
	total := 0
	for x := range in {
		total += x
	}
	return total
}
```
The last thing is to read files and count the total occurrences of the given phrase. In the third part of the code, you can find a function `scanFile` that takes three arguments to specify file path(fn), given phrase(phrase) and channel(out). So far, you probably have an idea what Channel here is used for?  In order to communicate to other entities or goroutines, we need to send out messages to the channel. There is one tiny but very important thing to mention here which is the <- symbol found on the right of the `chan` keyword. It indicates a write-only channel where you can only send messages to it. On the contrary, if the <- symbol is found on the left side of the `chan` keyword, then it denotes that the channel can only be used for reading only like we did with the function `sum`. In the following code segment, we read all the words from the given file and count the numbers of occurrences of the given phrase. The total occurrences `count` will be sent to the `out` channel which indicates the `in` channel in function `sum`.
```go
func scanFile(fn, phrase string, out chan<- int) {
	f, err := os.Open(fn)
	if err != nil {
		fmt.Println(err)
		return
	}
	defer f.Close()
	scanner := bufio.NewScanner(f)
	scanner.Split(bufio.ScanWords)
	count := 0
	for scanner.Scan() {
		if phrase == scanner.Text() {
			count++
		}
	}
	fmt.Println("file:", f.Name(), ", occurrences:", count)
	// send to the channel
	out <- count
	if err := scanner.Err(); err != nil {
		fmt.Println(err)
		return
	}
}

```
Now, we can connect all the dots and finish our main function like the code snippet below.
Basically, we finish most of the logic and it should work as expected. However, if we attempt to execute this program, we will get an error message like: `fatal error: all goroutines are asleep - deadlock!`. This is because we forgot to close the channel where the function sum was reading messages from and because of that, the program doesn't know when to stop reading messages from the channel and then causes a deadlock.
```go
func main() {
	if len(os.Args) < 2 {
		fmt.Println("Need at least one phrase and file parameters!")
		return
	}
	phrase := os.Args[1]
	A := make(chan int)
	jobNumbers := len(os.Args) - 2
	for i := 2; i < len(os.Args); i++ {
		fn := os.Args[i]
		// Reads the file and finds the number of occurrences of a given phrase
		go scanFile(fn, phrase, A)
	}
	// Calculate total numbers of occurrences
	total := sum(A)
	fmt.Println("total occurrences:", total)
}
```
How do we resolve it and make sure that we close the channel properly when every goroutine finishes their jobs? It is worthwhile to mention that we cannot close a closed channel in golang, therefore, only the last goroutine which finishes its jobs can close the channel.
Let’s imagine that channels are serving stations where we hold food and goroutines are the staff who serve the food. Let's say we would like to close the cafeteria, those serving stations need to be properly closed. Therefore, we have to assure that only the last person who finishes the serving can close the serving station, otherwise - hypothetically - others might not be able to serve food in the future.

Let's get back to the `main` function here below to see how we can refine it. We would need a counter which can be accessed by multiple goroutines, so that we could keep track of how many goroutines are still working and will need to use the channel. However, how do we manage states between goroutines without causing race conditions? Well, this is where `sync/atomic` comes in handy. We can setup a new variable `ops` and leverage the package `atomic` to control our state across goroutines and prevent race conditions.
```go
var ops int32
func main() {
	if len(os.Args) < 2 {
		fmt.Println("Need at least one phrase and file parameters!")
		return
	}
	phrase := os.Args[1]
	A := make(chan int)
	jobNumbers := len(os.Args) - 2
	atomic.AddInt32(&ops, int32(jobNumbers)) // to keep track of total numbers of goroutines
	for i := 2; i < len(os.Args); i++ {
		fn := os.Args[i]
		// Reads the file and finds the number of occurrences of a given phrase
		go scanFile(fn, phrase, A)
	}
	// Calculate total numbers of occurrences
	total := sum(A)
	fmt.Println("total occurrences:", total)
}
```
The last part of the `scanFile` function is as follows:
```go
func scanFile(fn, phrase string, out chan<- int) {
	defer func() {
		atomic.AddInt32(&ops, -1)
		if atomic.LoadInt32(&ops) == 0 {
			close(out)
			return
		}
	}()
	f, err := os.Open(fn)
	if err != nil {
		fmt.Println(err)
		return
	}
	defer f.Close()
	scanner := bufio.NewScanner(f)
	scanner.Split(bufio.ScanWords)
	count := 0
	for scanner.Scan() {
		if phrase == scanner.Text() {
			count++
		}
	}
	fmt.Println("file:", f.Name(), ", occurrences:", count)
	// send to the channel
	out <- count
	if err := scanner.Err(); err != nil {
		fmt.Println(err)
		return
	}
}
```
Here we add an anonymous function to manage the counter `ops` we mentioned previously. Basically, what it does is to check whether it can close the channel or not after decreasing `ops` by 1. Furthermore, use the `defer` keyword to make sure that each goroutine will remember to manage the counter when it finishes its jobs, so we can keep `ops` in-sync across goroutines. As a result, only the last goroutine to finish can scan the document and close the channel.

Thank you for reading this article.