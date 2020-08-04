---
layout: post
title: "The first steps to successful web API design"
date: 2020-08-03 03:00:00 -0000
author: "Nielet D'mello"
tags: ['backend engineering', 'technology']
---

![API Design!](/images/designcover.jpg  "Photo by Green Chameleon on Unsplash")



    Design is not just what it looks like and feels like. Design is how it works.
    -Steve Jobs 

APIs (application programming interfaces) are ubiquitous. More specifically, web APIs. :computer: Today, applications in smartphones as well as deeply hidden backend servers use them. APIs allow both internal and external developers to accomplish one of two things:

- access an application’s data
- use an application’s functionality

Therefore, how we design our APIs contributes to its success (or failure). 

As a backend engineer, I primarily deal with everything APIs day in, day out. In this article, I intend to share my learnings on some of the first steps in API design that make a good, usable and consistent API.

  

### Public APIs and Private APIs

Before we dive into the design fundamentals, let's understand the two types of APIs:

- **Public APIs**: 
  

Public APIs are exposed as services or products by companies meant to be consumed by external developers. Some companies (ex. GitHub) first create APIs for external stakeholders and then release them to internal stakeholders. 
GitHub’s API primary audience, in the beginning, were external developers who wanted to gain programmatic access to their data. 

Shortly after the initial release of their API, small businesses (who were creating developer tools and selling them to GitHub’s users) began to form around GitHub’s API. 
This is a very good example of how public APIs evolve beyond their initial scope.


- **Private APIs**:


Private APIs are the ones that are built for internal use for your apps, teams, company, etc. 
For example, Slack’s API started as an API for its web, native desktop, and mobile clients to display a messaging interface. Although created for its internal developers, the company's growth paved the way for a handful of “integrations” with important business software which became a pivotal piece of the puzzle for Slack’s growth and development as communication software. 

Slack then launched its Developer Platform along with a suite of products for third-party developers to build their apps, both at established companies and at new startups. This is a good example of how APIs evolve as a company grows.

Over the years, various API paradigms have emerged. Some of the most popular standards today are REST, RPC, GraphQL, WebHooks, and WebSockets.

#### Request–Response APIs

The Request–response APIs expose an interface through an HTTP-based web server. These APIs define a set of endpoints to which clients make HTTP requests for data and the server returns responses. The three common paradigms used by services to expose request-response APIs are _REST_, _RPC_, and _GraphQL_.

#### Event-Driven APIs

 For services with constantly changing data, the response can quickly become stale in case of request-response APIs. The event-driven APIs trigger certain functions on new event delivery thus eliminating the need to inherently wait for synchronous delivery or real-time communication.
There are three common mechanisms for real-time sharing of data about events: _WebHooks_, _WebSockets_, and _HTTP Streaming_.

With these common paradigms used in the industry, the biggest challenge is designing good APIs.

### Why design matters?

It is not about how an API is exposed but to whom. A typical API goes through multiple phases in its lifecycle- early discussions, development, evolution, retirement.
The simplicity of API matters because the consumer of the APIs is a developer who does not want to be overwhelmed by the underlying complexities of the system they interact with.  An easy to understand and an easy to use API design is simply the minimal goal. 


There are far more facets to the design. This includes understanding the complete context- *who will use the API? how? how is the API built? how will it evolve?*
Poorly designed APIs can cost time, money, effort, bugs, and most importantly security vulnerabilities.

For some companies like [Stripe](https://stripe.com/docs/api) (APIs for payment processing on the internet) or [Twilio](https://www.twilio.com/docs) (APIs for communication via SMS, voice, and messaging), the API is the product. For such companies, building an API is 100% aligned with a single-product audience. That is the reason their API design and documentation is one of the best out there. One from which we can draw many lessons to build successful APIs.

### Focus on the API user in the design process

Quite often APIs are designed based on the internal architecture of the application, sometimes leaking details of the implementation. This leads to confusion for third-party developers and results in bad developer experience.   
    That’s why it’s so important to focus not on exposing your company’s/service's internal infrastructure but on the experience that an outside developer should have when interacting with your API.

#### The API intent

APIs are built to serve an intent. It is important to focus on what the user can do rather than how the software operates to make the APIs easy to use and understand. Hence, when designing an API, it is fundamental to understand the below:

-   Who can use the API
-   What they can do
-   How they do it
-   What they need to do it
-   What they get in return

I find the whiteboard method very useful in the initial phase of API design.

A relatable template I found was in '_The Design of Web APIs_' book by Arnaud Lauret. It's a good way to ensure the the focus remains on the consumer's perspective and not on a provider's perspective in the design process.

![API Goals!](/images/apidesign.png  "Source: The Design of Web APIs")



### Usability

A usable API is a gamechanger because the lesser the effort to work with it, the more people choose to use it. Usability distinguishes awesome API from a mediocre one. It's almost a deja-vu feeling when using an API that is built with usability in mind.

A usable API is easy to understand and conforms to standards or common practices. It also has straightforward representations, interactions, and flows.

There are a few things to check when evaluating your API usability.

-   Are the representations (naming, data formats, inputs) easily understood by people and programs?
-   Is the representation as informative as possible?
-   Does the error feedback provide enough elements to understand and maybe fix the issue?
-   Does the success feedback describe what action has been completed?


### Consistency

Consistency is key when designing APIs. However, two things to be aware of: it’s hard to be consistent, and consistency must not be applied blindly. Being consistent in your design not only makes your API easier to use but also makes its design simpler.

The design of APIs should maintain four basic levels of consistency-

- Within an API:
an API must be consistent with itself—proposing consistent data, goals, and behaviors.

- Across an organization/company/team’s APIs:
an API must be consistent within its organization by sharing common features so that developers can easily understand and use any part of the API easily, once they have learned to work with a similar one.

- With the domain(s) of an API:
being consistent with the domain(s) of or used by an API by following standard or at least common practices that you must follow when working on a specific domain.

- With the rest of the world:
by enhancing your APIs interoperability with the rest of the world, make your APIs predictable for people who have never used any of your APIs before.

Consistency means that there are certain patterns and conventions repeated throughout your API, such that without seeing the documentation, developers can begin to predict how to use your API. This ranges from data access patterns to error handling to naming. Moreover, it reduces the cognitive load on developers who are trying to figure out your API.

Defining your design with rules in the “***API Design Guidelines***” or the “***API Design Style Guide***” document helps establish best practices within the team and the organization when designing APIs.

### Conclusion

Building a successful API comprises of many things- business analysis, architecture, development, documentation, support, marketing, and so on. It is an art. It is very crucial to focus on the design of the API and ensuring the API has attributes of good design. This article barely scratches the surface with the first steps. 

In the upcoming article, we will discuss more on API documentation, versioning, rate limiting, security, etc.

### Book recommendations

There are a lot of good resources available on the topic of designing good web APIs. I particularly read the following books and felt they had some good topics to get an in-depth understanding of web API design: 

- The Design of Web APIs by Manning Publications
- Designing Web APIs by O'Reilly Media, Inc.
