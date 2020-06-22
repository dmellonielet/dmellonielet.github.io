---
layout: post
title: "Under the hood of a data-intensive application"
date: 2020-06-19 03:00:00 -0000
author: "Nielet D'mello"
tags: technical
---

![Under the hood of data intensive systems](/images/ddia.jpg  "Photo by h heyerlein on Unsplash")


Data is one of the most important assets right now and it is established that '*The Future is Data-Driven*'.

Some time back, I started reading the brilliant book '***Designing Data-Intensive Applications***' by Martin Kleppman. The book impressed me as a modern-day textbook for anyone who wants to understand in-depth what it takes to design, build, and maintain a data-intensive application.
  

In this writeup, I will summarize the interesting learnings from the 1st chapter of the book and some of my notes.

  

## Umm...Data-intensive what?


Today, applications tend to be data-intensive owing to the amount, complexity, and speed of change for the data it handles. Taking a quick look at the apps on our devices and the sheer volume of data it produces/consumes at every interaction, it is evident that there are a lot of blocks that comprise the application to make such a thing possible. 
These standard building blocks are:


- Databases

- Caches

- Search indexes

- Stream processors

- Batch processors

Each of these warrant a separate detailed discussion owing to their unique characteristics. There are various approaches one can take for working with these blocks. These approaches are driven and dependent on the requirements which vary for each application.

  

## Foundational Concerns


In my experience building systems that are data-intensive, the common questions that arise are- how to maintain the accuracy and consistency of the data over its entire life-cycle, how to provide performance to clients when parts of the system have an outage, can the system scale under load, how good is the system interface (API), etc.
The team's skills and experience as well as time to market matter as well.

  

However, three nonfunctional requirements stand out as crucial:


### ***Reliability***


Reliability is an important pillar and a system is considered reliable if it continues to work correctly even when things go wrong. How well the system anticipates faults and copes with them determines it resiliency or fault-tolerance ability. Bugs in applications take a hit on productivity, cost, and reputation owing to the impact on customers.

Reliability is so important that we now have dedicated teams consisting of Site Reliability Engineers, Resilience Engineers, and Performance Engineers solely focused and responsible for ensuring the system is reliable as a whole.

Hardware faults, Software errors, Human errors can contribute to unreliable systems, and some ways to ensure reliability are:

- Minimize the opportunity for errors by leveraging well-designed abstractions and APIs. There is a balance that needs to be met given restrictive interfaces cause engineers to work around them.

- Utilize non-production sandbox environments to explore and experiment safely, using real data, without affecting real users.

- Automate as much as possible to cover corner cases and test thoroughly at all levels ranging from unit tests to system-wide integration tests and manual tests.

- To minimize the impact of failure, allow quick and easy recovery.

- Monitoring is key as it allows a clear picture of early warning signs and provides metrics for diagnostics.

  

### ***Scalability***


A big blocker for system reliability is its ability to scale in times of increased load. Scalability is the system's ability to cope with increased load.

The load can be described as an increase in the number of concurrent users or the volume of data being processed. It is best described using load parameters which highly depend on the system's architecture ranging from web server’s requests/second, the read: write for database, hit rate on cache, etc.

To assess the impact of load on performance, consider the following:

- If load parameters increase and system resources are unchanged, how is system performance affected?

  

- If load parameters increase, how much increase in system resources is required to keep performance unchanged?


Performance measurement can differ based on the nature of processing the system does. If it is a batch processing system, throughput is an important metric and if the system is a real-time online one, the response time is a good measure.

Twitter for example does load testing, dark traffic testing in staging and canary deployments, stress testing in production to ensure reliability and scalability.

There is no *magic scaling sauce*- there is no generic, one size fits all scalable architecture.

  
  

### ***Maintainability***


Maintenance activities like fixing bugs, investigating failures, adapting to new platforms, modifying to new use cases, repaying technical debt, and adding new features are costly.

However, a well-designed system can utilize the following three design principles for minimizing maintenance pain:


-  *Operability*- A good operation can work around bad software but not the vice versa. Good operation practice includes monitoring system health and service restoration, triaging failures, keeping the system up-to-date (especially security patches). Good documentation can make a huge difference as it aids in understanding the system better.

-  *Simplicity* - Avoiding the notorious ball of mud(A software project mired in complexity) by avoiding tight coupling, tangled dependencies, inconsistent naming, and terminologies, etc. Complex systems are more vulnerable to bugs when changes are made to it.

-  *Evolvability*- There is no system immune to changes. Simple and easy-to-understand systems are easy to modify than complex ones.

 

## Conclusion


There is no easy fix for ensuring a system is reliable, scalable, and maintainable. To understand how to achieve this goal requires understanding the patterns and techniques that keep appearing in various such applications.