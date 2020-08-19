---
layout: page
title: "HW1: Parallel Sum"
permalink: /hw1/
---

> Deadline: TBD
> GitHub Repo Setup: TBD
> This assignment must be completed **individually**


## Overview 
In this assignment you will solve a simple problem to familiarize you with golang, especially with Goroutine, http, and RPC. The Go web site contains lots of tutorial information and this might be helpful to you if you are new with Golang. https://tour.golang.org/

### Go Setup and Dev Environment

We recommend that you work on the assignment on your own machine so that you can use the tools, text editors, etc. that you are already familiar with. 
If you haven’t installed Golang on your own machine, visit here to install it https://golang.org/doc/install. 

We will grade your labs using Go version 1.14; you should use 1.14 too. You can check your Go version by running `go version`.

We recommend writing your code in [Visual Studio Code](https://code.visualstudio.com/). In order to get help from the course instructors, you must be using Visual Studio Code and have the [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) plugin installed which will allow you to share your environment.

### GitHub

We will use GitHub Classrooms to manage your repositories and submit code. You must create a (free) GitHub account if you do not already have one. Use [this link](#) to create your repository.

You should also use this assignment to practice using git and GitHub. *You must create at least one commit and push your code to GitHub for each of the phases listed below to receive full credit.*

---

## Parallel Sum
You will write code to parallelize the task of summing up a list of numbers stored in a large file. Summation is not very computationally intensive, but you can imagine replacing this with a more complicated task such as performing image recognition on a large set of files, or performing sentiment analysis on a large number of tweets.


## Phase 1: Sequential Sum
To start with, you must complete our starter code to correctly sum a list of numbers from a file.

You are provided three files in the  `sequential_sum/` starter code:
  - `main.go` - contains the main entrance to your program. It should determine the file to be processed as a command line argument such as `-f test1.txt`.
  - `sum.go` - implements the core `Sum(fileName string)` function. You should fill in your code here, but should not change the signature of this function. The file also contains a `readInts` function which you should use to turn a file into an array of integers for processing by your Sum function.
  - `sum_test.go` - includes several test cases to validate that your program works correctly. You can extend this file if you would like to add more test cases. 


## Phase 2: Go Routines
Summing numbers is fairly trivial to implement in a sequential way, so next you must make it parallel. This will help you understand synchronization mechanisms in Golang which are fundamental in future more complicated assignments.

Your program should:
  - fds

## Phase 3: HTTP/RPC + Go Routines
Finally, we will make our summation program accessible over a remote interface.