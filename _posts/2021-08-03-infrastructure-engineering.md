---
layout: post
title: "The fascinating world of Infrastructure"
date: 2021-08-03 03:00:00 -0000
author: "Nielet D'mello"
tags: ['software engineering', 'technology']
image: /images/infrastructureengg.png
---

![Infrastructure Thingz!](/images/infrastructureengg.png)

I've been dabbling with infrastructures in my current role where I realized how vast and fascinating the current infrastructure space is.

Various flavors of infrastructure engineering exist today ranging from core Software Engineer- infrastructure roles to site reliability engineering, DevOps (although it's more of a culture thing than technology or role), data infrastructure, developer productivity, tooling, and so on.

As systems become largely distributed, challenges for scalability, reliability, and maintainability of services arise. These systems and their services are inherently cloud-native with five architectural principles-

- Containerization
- Dynamic management
- Microservices
- Automation
- Orchestration

The infrastructure teams own the charter for building and scaling the platform from conception to deployment and beyond. This allows product teams to build and ship products faster. In a nutshell, infrastructure engineering's primary goal is accelerating productivity across the organization and the company. I like Will Larson's definition of technical infrastructures from his SRECon '19 talk: Tools used by 3+ teams for business-critical workloads.

When I get asked about **'what skills or areas are key to working successfully in the infrastructure space'**, these are my technology agnostic notes based on my experience:

### Deep understanding of scalable distributed systems

Working on infrastructures involves complex distributed systems with many moving paths and dynamic behaviors. Most of these systems are hosted on public clouds using managed services.  A hybrid approach is fairly common in large corporations that have their own on-premise infrastructures. Having a high-level understanding of how distributed systems work at scale is important when building infrastructures that meet the short-term demands yet scale well in the long term.

### Problem Solving

The ability to debug complex problems across the whole stack, constant learning, and being creative contributes a lot to be successful at infrastructure engineering. It involves thinking about the edge cases, failure modes, and life cycles of the systems.

### Communication and Collaboration

In my opinion, one of the most important skills in infrastructure engineering (actually in overall software engineering) is communication and collaboration. This involves focusing on the needs of the users, conveying your ideas, candidly discussing opens, and clarifying things that are unclear. This is particularly valuable to thrive in a collaborative and diverse environment or dealing with incidents, outages, and migrations when you have to work with folks across the organization or company.

### Observability and Resilience

Once any system is up and running, monitoring and observability are critical to achieving proactive alerting about regression trends in service health, latency, and benchmarking. This skill largely piggybacks on the first skill as it is vital to know the plumbing of the system and how things flow through it.

### Capacity planning

Capacity planning is all about matching the demand to available resources. This includes examining what systems are in place, measuring their performance, and determining patterns in usage that enable the planner to predict demand. Various technology stacks and workloads consume resources in varied ways. A favorite approach I learned from my colleague is asking- "What is expected to break first?"

### Operational cost analysis and optimizations

Often in this space, it's about making informed tradeoffs around latency and the cost of running services in the cloud. A frequent pattern I have noticed is how stale resources lie around, consuming precious organizational budgets if cost analysis and optimization are not a priority early on. Deep diving to understand resource utilization and implementing cost optimization best practices helps reduce resources waste, fine-tune and optimize the environments to meet the scaling challenges, and maintain the financial budget.

### Automation

My favorite quote on this one is by Tom Preston-Werner: “You're either the one that creates the automation or you're getting automated”. My current project uses automation heavily at scale at every level and it's gratifying to see how much trouble it saves and how it boosts productivity across the company. In my observation of my colleagues super skilled at automation, what strikes me is their mindset of- 'Reject the temptation of manual work when something can be automated. Additionally, I learned that a robust, version-controlled Infrastructure as Code is supercritical to be delivering changes to a system in a dynamic environment to meet key metrics like- delivery lead time, deployment frequency, change fail percentage, and mean time to restore.

### Systems and Networking

The sheer volume of systems and networking to know when working on infrastructures is amazing. Some things that typically fall on the radar are understanding compute resources (virtual machines, physical servers, server clusters, containers, application hosting clusters, function as a service aka FaaS, etc.), storage resources (block storage, object storage, networked filesystems, structured data storage, secrets management, etc.), networked resources (network address blocks, names such as DNS entries, routes, gateways, load balancing rules, proxies, API gateways, VPNs, Direct connection, network access rules (firewall rules), asynchronous messaging, cache, CDN, service mesh, etc.).

### Security

This is inherently the most critical aspect of any infrastructure. A lot of work in this space follows the 'Secure by default' mantra that spans data classification and protection, certificates, IAM(authentication and authorization), vulnerability assessments, security policies, and fundamental network security.

## Closing thoughts

Infrastructure and Operations is an interesting and challenging space that continues to evolve in a cloud native era. I've barely scratched the surface here as I continue my own learning and aim to write more about these topics in my upcoming posts.
