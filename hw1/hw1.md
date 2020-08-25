---
layout: page
title: "HW1: Parallel Sum"
permalink: /hw1/
---

> Deadline: TBD
> GitHub Repo Setup: TBD
> 
> This assignment must be completed **individually**. You **MAY NOT** share your code for this assignment with any other student. It is acceptable to provide high level advice about relevant go libraries and tools, but you should not be explaining to other students how to solve the problem, nor should you be searching the internet for solutions.


## Overview 
In this assignment you will solve a simple problem to familiarize you with golang, especially with Goroutine, http, and RPC. The Go web site contains lots of tutorial information and this might be helpful to you if you are new with Golang. https://tour.golang.org/

### Go Setup and Dev Environment

We recommend that you work on the assignment on your own machine so that you can use the tools, text editors, etc. that you are already familiar with. 
If you haven’t installed Golang on your own machine, visit here to install it https://golang.org/doc/install. 

We will grade your labs using Go version 1.14; you should use 1.14 too. You can check your Go version by running `go version` -- if you have a more recent version that is OK too.

We recommend writing your code in [Visual Studio Code](https://code.visualstudio.com/). In order to get help from the course instructors, you must be using Visual Studio Code and have the [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) plugin installed which will allow you to share your environment.

### GitHub

We will use GitHub Classrooms to manage your repositories and submit code. You must create a (free) GitHub account if you do not already have one. Use [this link](#) to create your repository.

You should also use this assignment to practice using git and GitHub. *You must create at least one commit and push your code to GitHub for each of the phases listed below to receive full credit.*

---

## Parallel Sum
You will write code to parallelize the task of summing up a list of numbers stored in a large file. Summation is not very computationally intensive, but you can imagine replacing this with a more complicated task such as performing image recognition on a large set of files, or performing sentiment analysis on a large number of tweets. We will solve this problem in three phases of increasing complexity. You must solve all of them for full credit.

> **Output:** Your programs can display any debugging output you need, but the final line of output must be `SUM XXXX` where `XXXX` is the sum of all lines in the input file. You can assume that the input file is formatted correctly.

## Phase 1: Sequential Sum
To start with, you must complete our starter code to correctly sum a list of numbers from a file without using any parallelism.

You are provided three files in the  `sequential_sum/` starter code:
  - `main.go` - contains the main entrance to your program. It should determine the file to be processed as a command line argument such as `-f test1.txt`. It then should invoke a function in the `sum.go` file to perform the sum.
  - `sum.go` - implements the core `Sum(fileName string)` function which must return . You should fill in your code here, but should not change the signature of this function. The file also contains a `readInts` function which you should use to turn a file into an array of integers for processing by your Sum function.
  - `sum_test.go` - includes several test cases to validate that your program works correctly. You can extend this file if you would like to add more test cases. 

You can build, run, and test your program with:
```
go build

./seq -f test1.txt -g 4
SUM -83

go test
```

> **IMPORTANT:** At this point you should be sure to commit your code and push it to github. As you make progress on the following phases you should commit and push your code regularly. Failure to do so may cause you to lose points.

## Phase 2: Goroutines
Summing numbers is fairly trivial to implement in a sequential way, so next you must make it parallel. This will help you understand concurrency and communication mechanisms in Golang which are fundamental in future more complicated assignments.

Next work on the files in `parallel/`. Your new program should extend the files in the following ways:
  - `main.go` - should now accept a second argument `-g` which specifies how many goroutines should be started to execute the summation in parallel.
  - `sum.go` - modifies the `Sum()` function to accept the number of goroutines to use. You should still use the `readInts` function to sequentially read the file, but then you must split up the sum across the specified number of threads.
  - `sum_test.go` - similar to above

You can build, run, and test your program with:
```
go build

./parallel -f test1.txt -g 4
SUM -83

go test
```

## Phase 3: HTTP/RPC + Goroutines
Finally, we will make our summation program accessible over a remote interface. HTTP is the standard interface used in the web to allow external clients to communicate with a service. Remote Procedure Calls (RPC) are another form of communication which offers more flexibility to the programmer. In this phase you will extend your program to run an HTTP Server which accepts client requests from a web browser; the server then uses RPC to pass the request to the go program which will compute the sum. This is a common 2-tier web application architecture with a web frontend and an application server backend.

In a real implementation, the HTTP frontend would allow users to upload files to be processed. For simplicity, we will just have the user access a URL that specifies the file name to be processed, e.g., `http://localhost:8000/sum/test1.txt`. We will assume the RPC backend has access to this file.

You will work on the files in `http_parallel/` for this phase. You are provided starter code for the two servers:
  - `http_front/` - contains the files for running an HTTP server that listens on port 8080. The sample code starts a simple HTTP server and displays the requested URL. You must extend this to make an RPC to the backend specifying the file to be analyzed. After the sum is complete it should output the result such as `???XXXXXXXX???`
  - `rpc_back/` - contains the files for the RPC server backend that listens on port 8083. It should receive RPC requests indicating the file to be processed and and the number of goroutines to perform the sum. It should then return the summation result to the frontend.

You can build and start your program using *two* terminals:
```
## HTTP Server -- Teriminal 1
cd http_front/
go build
./http
HTTP Listening on port 8080
...

## RPC Server -- Terminal 2
cd rcp_back/
go build
./rpc
RPC Listening on port 8083
```

You can then test your servers by accessing them with a web browser: [http://localhost:8080/file_name=test1.txt&grn=10](http://localhost:8080/file_name=test1.txt&grn=10)

Or you can test using the curl command line utility:
```
curl .... TODO FILL IN
```