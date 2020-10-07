---
layout: page
title: Final Project
permalink: /project/
---

For your final project you will investigate a research challenge in distributed systems. We will allow two types of projects:

**Research Focused:** Your group must pick a problem under active research, read papers in the area, and implement a solution to the problem. Your solution can be a re-implementation of an existing research project or a combination/extension of current approaches.  You will need to build and evaluate the performance of your system to compare it against prior research. If your focus is more algorithmic, you may want to build a simulator instead of a real platform so you have better control over the environment.

**Implementation Focused:** Your group must build a simplified version of an existing distributed system. You still will need to read research papers about the system you are implementing, but your effort will be focused more on implementing the system and less on evaluating and comparing it against other proposed approaches.

You have about two months to complete the project so it should be more significant than a standard programming assignment, while still being feasible to complete within that time frame. The project will be broken into milestones.

**Due Dates:**
  - [Milestone 0: Form a Team](#milestone-0-form-a-team) - 10/12
  - [Milestone 1: Select a Topic](#milestone-1-select-a-topic) - 10/19
  - Milestone 2: Literature Survey - 10/29
  - Milestone 3: Design Document - 11/5
  - Milestone 4: Final Presentation - 12/14

---

## Milestone 0: Form a team 

  - Due 10/12 - earlier if possible

You must form a team of 3-4 students. We suggest teams have 4 members if possible. All members are expected to contribute equally to the project, although different students may have specialized roles. However, all students should at least partially contribute to both the coding and writing portions of the project. One student should be selected as the team leader who will act as the main contact point of the group.

When you form a team you do not yet need to have selected a project idea, however it is best if you decide an area (or areas) you want to work in and be sure all team members agree. See the sample projects under Milestone 1 for more details.

---

## Milestone 1: Select a topic 
 
 - Due 10/19 - earlier if possible

> We strongly encourage you to complete Milestones 0 and 1 early. If you submit Milestone 1 at least 5 days early you will receive a 5 point bonus to your report grade.

For this milestone you will need to submit a 1-2 page report that answers the following questions:
  - What is the topic area of the project? (see examples below)
  - What are the main distributed systems challenges you will face?
  - What are some sample papers (at least 4) that will guide your work?

We will not permit two groups to work on the same project idea. Precedence will be given to whichever group submits their proposal first. Your project proposal for Milestone 1 must be approved by the professors before you can submit the following assignments! If you submit early we will try to approve your project early.

### Sample Project Ideas - Research Focused

*Linux CPU Scheduling*: Modify the Linux CPU scheduler and evaluate how your changes affect the performance of different types of applications. For example, you could reproduce the code from *[Fewer Cores, More Hertz (Usenix ATC 20)](https://www.usenix.org/conference/atc20/presentation/gouicern)* which proposed techniques for adjusting the scheduler to perform better when the CPU performs dynamic frequency scaling.
 - Similar ideas: VM CPU scheduling on a hypervisor like Xen; Dynamic resource allocation for containers using cgroups; etc

*Load Balancing*: Evaluate the performance of different load balancing algorithms under a variety of workloads and server conditions. To evaluate load balancing approaches at large scale, you could build a simulator to test the performance of different algorithms. You should focus on a particular challenge, for example reproducing the load balancing algorithm in Prof. Wood's [NetKV (ICAC 16)](http://faculty.cs.gwu.edu/~timwood/papers/16-ICAC-netkv.pdf) project which dealt with skewed workloads arriving at a memcached cluster.
  - Similar ideas: Task scheduling in Map Reduce; website load balancing; etc

*Consensus*: Consensus algorithms allow multiple nodes in a distributed system to reach agreement about a decision even if some nodes can fail. For example, [Raft (Usenix ATC 14)](http://nil.csail.mit.edu/6.824/2020/papers/raft-extended.pdf) provides an algorithm for ordering requests when nodes can crash or become disconnected. You could either implement Raft from scratch, or extend the official implementation in some way.
  - Similar ideas: Byzantine Fault Tolerance to handle arbitrary failures and malicious nodes

*Container Migration*: Virtual machine migration is a popular tool for managing data centers, yet container migration has not reached the same level of maturity. You could explore container migration approaches based on CRIU such as [Voyager (ICDCS 17)](https://ieeexplore.ieee.org/abstract/document/7980161) and evaluate how they perform in different environments.
  - Similar ideas: Optimizing container or VM migration by eliminating redundant data transfers; resource management algorithms to decide when to migrate or which host to migrate to

### Sample Project Ideas - Implementation Focused
These project ideas focus on implementing a simplified version of a distributed system "from scratch". Designing and building a full system like this is a lot of work, so you will need to limit your scope to a specific set of distributed systems problems.

*Distributed Database from Scratch*: Implement a basic distributed database. You should not spend a lot of effort on the database query engine (perhaps you can just reuse something simple like SQLite) and instead should focus on challenges such as supporting consistency and fault tolerance.
  - Similar ideas: Build a Distributed Hash Table like Chord or implement a simulation of a large scale P2P file sharing system.

*Serverless Platform from Scratch*: Implement a simplified Serverless / Function as a Service platform. A serverless platform dynamically starts and stops containers or VMs as requests arrive. The basic components include a gateway load balancer, a queueing system that can buffer requests, and an autoscaler that decides when to add or remove nodes.

*RPC from Scratch*: Implement your own RPC library. Your version of RPC could explore interesting distributed systems challenges like fault tolerance or scalability. For example, your RPC library could automatically load balance calls across several servers, or detect a server failure and reissue a request to a backup replica.

### Bad Project Ideas
Projects like the following will not be approved:

  - Building a web application that combines several cloud services (e.g., a meeting room reservation system). This is a distributed system, but we want you to focus on the underlying concepts, not an application.
  - Taking code from an existing research project and measuring its performance.  If code exists, you will be expected to modify / extend it in some way.  If no code is available, then it is acceptable to try to directly mimic an existing project.
