---
layout: post
title: "Understanding web API security"
date: 2020-08-30 03:00:00 -0000
author: "Nielet D'mello"
tags: ['backend engineering', 'technology', 'api']
---

![API Security!](/images/apisecurity.jpg  "Photo by Moritz Erken on Unsplash")

> By 2021, 90% of web-enabled applications will have more surface area
> for attack in the form of exposed APIs rather than the UI, up from 40%
> in 2019.
>  
> By 2022, API abuses will move from an infrequent to the most-frequent
> attack vector, resulting in data breaches for enterprise web
> applications.
> 
> -Gartner: API Security: What You Need to Do to Protect Your APIs

Security is fundamental for any web application and particularly for APIs :computer: .

As new security issues and vulnerabilities come to light, it is crucial to secure APIs from these attack surfaces. With the microservices architecture, each service communicates with the other using APIs exchanging a ton of data. The well-known application security solutions are not enough when it comes to secure web APIs. If APIs leak data, a security breach can result in loss of critical data as well as revenue and damage the reputation of a business.

At its very core, when we think about security, what jumps to our mind are measures like input validation, content type validation, audit logs, protecting from XSS and CSRF, etc.

Yes, these are important. However, securing APIs goes beyond these techniques.

My first encounter with API security was when I found out the numerous hidden ways in which the API I had developed could be exploited. Since then, I have come a long way, having adopted a security-first mindset. In this short writeup, I would like to cover security principles that are inherent to APIs and dive into some key concepts to keep in mind to adopt a security-first mindset when designing and developing APIs.

### Authentication and Authorization

Two core concepts to understand here when talking API security:

**Authentication**: AuthN (authentication) is the process of verifying who a user is.

**Authorization**: AuthZ (authorization) is the process of verifying what they have access to.

Authentication is usually a precursor to authorization.
When designing APIs, it is important to think about how app developers will perform both authentication and authorization.

  

Traditionally, ***Basic Authentication*** is the simplest technique to enforce access control on the web. The requesting client sends HTTP request with an Authorization header with the word "Basic" followed by space and string (username: password) and encoding it with base64.

    ex. Authorization: Basic dXNlcjpwYXNzd29yZA==

This method offers the least amount of security. It has a number of drawbacks, one of which is that the username and password are passed in the clear with every request. Although somewhat less vulnerable under HTTPS this is clearly unsafe under HTTP.

  
***OAuth*** is an open standard that allows users to grant access to apps without sharing passwords. With OAuth, API providers' users can grant selective permissions to resources. Apps use an access token to call APIs on behalf of a user. The generation of this token happens in a multistep flow.

  

### OWASP top 10 for API security


The attack surfaces for APIs are widening. Some classic recent examples of API breaches are:
<a href="https://threatpost.com/internal-accenture-data-customer-information-exposed-in-public-amazon-s3-bucket/128364/" target="_blank">Accenture breach</a>,
<a href="https://www.zdnet.com/article/over-100000-github-repos-have-leaked-api-or-cryptographic-keys/" target="_blank">Leaked Keys on GitHub</a>,
<a href="https://threatpost.com/t-mobile-alerts-2-3-million-customers-of-data-breach-tied-to-leaky-api/136896/" target="_blank">T-Mobile breach</a>,
<a href="https://apisecurity.io/issue-49-uber-account-takeover-leaky-get-api/" target="_blank">Uber account takeover</a>,
<a href="https://www.wired.com/story/i-scraped-millions-of-venmo-payments-your-data-is-at-risk/" target="_blank">Venmo Payment</a>

These examples show us the extent and effect of an API security breach.
I personally recommend understanding the OWASP API security top 10 as it provides a comprehensive list of threats/ vulnerabilities to look for when working on securing APIs. The following are the top 10 for 2019:

-   **API1:2019 Broken Object Level Authorization**
 Exposing endpoints that handle object identifiers can create a wide attack surface. This vulnerability is present when using IDs to retrieve information from APIs. Object-level authorization checks should be considered in every function that accesses a data source using input from the user.

-   **API2:2019 Broken User Authentication**
Often, authentication mechanisms are implemented incorrectly. This allows attackers to compromise authentication tokens or to exploit implementation flaws to assume other user’s identities temporarily or permanently.
Compromising the client/user authentication in turn compromises API security overall.
OAuth2.0 is the de facto standard for securing APIs. We looked at the limitations of using Basic Auth and the risks it possesses.

-   **API3:2019 Excessive Data Exposure**
Sometimes generic implementations feel very lucrative thus causing the developers to expose all object properties without considering their individual sensitivity. This approach tends to rely on clients to perform the data filtering before displaying it to the user.  For example, if looking for data if a user is above the age of 21, instead of returning the date of birth, the data should return a boolean flag to indicate the same.

-   **API4:2019 Lack of Resources & Rate Limiting**
Many times, APIs do not impose any restrictions on the size or number of resources that can be requested by the client/user. As bad this is with an impact on the API server performance, it paves the way to Denial of Service (DoS). This also leaves the door open to authentication flaws such as brute force. Web Application Firewall (WAF) solutions can help to prevent such attacks.

-   **API5:2019 Broken Function Level Authorization**
Authorization flaws happen when Complex access control policies with different hierarchies, groups, and roles are in place. An unclear separation between administrative and regular functions can cause potential harm. By exploiting these issues, attackers gain access to other users’ resources and/or administrative functions. Using scopes to bound the permissions is a good approach.

-   **API6:2019 Mass Assignment**
This vulnerability is exposed when APIs blindly bind to JSON objects received via clients without being selective about the attributes it binds to. Attackers can modify object properties by guessing them, exploring other API endpoints, reading the documentation, or providing additional object properties in request payloads.

-   **API7:2019 Security Misconfiguration**
Using default configurations that are not secure, incomplete or ad-hoc configurations, open cloud storage, misconfigured HTTP headers, unnecessary HTTP methods, permissive Cross-Origin resource sharing (CORS), and verbose error messages containing sensitive information are some of the classic ways to expose a security misconfiguration.

-   **API8:2019 Injection**
When APIs accept data and pass it on to interpreters to execute as a part of a query or a command, Injection flaws such as SQL, NoSQL, Command Injection, etc., occur.
The attacker’s malicious data can trick the interpreter into executing unintended commands or accessing data without proper authorization.

-   **API9:2019 Improper Assets Management**
With the evolution of container technologies making deployment a breeze, a lot of APIs can get deployed easily and forgotten over time if not documented properly. Proper and updated documentation is highly important in this case.

-   **API10:2019 Insufficient Logging & Monitoring**
Logging and monitoring are important to get visibility in the system. Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems to tamper with, extract, or destroy data.

### API Threat Modeling

Threat modeling is a structured approach to identifying, communicating and evaluating threats to an application and it's mitigations. It can be applied to APIs as well to gain insight into an attacker’s perspective. A few key steps to doing this:

- What are the key security goals?

A few questions to ask that help identify the security goals are- What data needs to be protected? Are there compliance requirements(HIPAA, GDPR, etc.)? What intangible assets, such as trade secrets or intellectual property need to be protected?

- What are the elements of my application?

During this exercise, understanding the scope of the application, considering key functionalities, data flows, dependencies, trust boundaries, etc. allows a better mapping of threats.
It’s key to identify different security zones where data will be in transit or at rest.

- What are the system assets and entry points?

Identify components(configuration files, sensitive information, data consistency) that need to be protected against misuse by an attacker. Access points ( open ports or protocols or file system read-and-write privileges) are attack surfaces and paths attackers may use to access the targeted endpoints. APIs need to be reviewed extensively considering attack scenarios that might leverage API methods.

- What threats need to be looked at?

There are many ways an API can be exploited. We briefly went over the Top 10 as listed by the Open Web Application Security Project (OWASP).

- How to prioritize the risk?

Associate a risk level for each relevant threat associated with the API. Correct threat prioritization is very important when looking at mitigation strategies.

- What is the mitigation strategy?

The principle of least privilege irrespective of what method is exposed is one of the best practices when it comes to securing APIs. Input sanitization and enforcing schema checks are vital. Developers should consider Security engineers their allies when figuring out ways to address all security aspects during the development process.

- What is the commitment to keep evolving this?

Threat modeling is not a one-time thing. Itʼs a continuous cycle. As APIs evolve and mature, the threat model needs to evolve to constantly assess against the questions listed above.

### Checklist for API Security:

There are many things to consider based on what we discussed above regarding API security. However, to summarize it all, the following is a checklist that I consider helpful:

[ ] Are API keys and tokens stored in a secure manner?

[ ] Can API keys be regenerated in the event of compromise?

[ ] If access tokens are stored in a database, is the access restricted?

[ ] Are the access tokens encrypted before storing?

[ ] Is the App Secret accidentally exposed in client-side or decompilable code?

[ ] Is HTTPS used instead of HTTP to leverage protection against eavesdropping, data tampering, etc.?

[ ] Do the URLs expose information like usernames, passwords, session tokens, API Keys?

[ ] Can restricted keys be used to allow the only minimum level of access?

[ ] If using OAuth, is the state parameter used to mitigate CSRF attacks?

[ ] If using OAuth, are short-lived authorization codes and one-time refresh tokens leveraged?


### References

To get more detailed information on API security, I recommend these resources:

<a href="https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html" target="_blank">OWASP REST Security</a>

<a href="https://owasp.org/www-project-api-security/" target="_blank">OWASP API Security Top 10</a>

<a href="https://increment.com/apis/ask-an-expert-threat-models-api-security/" target="_blank">Threat Modeling for APIs</a>

