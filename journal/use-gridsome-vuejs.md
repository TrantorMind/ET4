---
date: 2019-06-04
title: Controllable Scaling in Serverless Big Bang
author: authors/marin-r.md
excerpt: With the appearance of microservice architectures, communication using messages
  become common practice in today’s system design. Tightly coupled monolithic applications
  are rarely the choice of today’s developers or architects. Such applications mostly
  exist as legacy applications, waiting to be discontinued at some point in the near
  future.

---
## Controllable Scaling in Serverless Big Bang

With the appearance of microservice architectures, communication using messages become common practice in today’s system design. Tightly coupled monolithic applications are rarely the choice of today’s developers or architects. Such applications mostly exist as legacy applications, waiting to be discontinued at some point in the near future.

However, with message-based communication between microservices, we gained some new challenges. …

However, with message-based communication between microservices, we gained some new challenges. For instance, overusing of messages and making the system far more complex than it should be, or making one microservice dependent on the message that might never arrive, or having generic message types that have no exact purpose and might lead to misuse if incorrectly understood by a developer…

But in this article, I will discuss latency that can build as a result of queueing messages. Also, I will supply some ideas on how to mitigate those problems and avoid overwhelming source systems with minimal effort.

## Where do we make mistakes?

I am sure that all of you had a situation where you need to process some messages or events faster than the others. Some of the messages require different priorities when processed, as well as in real-life cases.  
  
For instance, if we take a hospital reception desk as a message router. People with urgent medical needs, such as a heart attack, need urgent attention in comparison with people that have common flu symptoms. So by evaluating the person’s condition, the receptionist is routing those patients to the specific hospital section in a prioritized way.  
In case, you have all patients in the same queue, some of them might die waiting :(

Similarly to patients in a hospital, some messages and events need quicker attention. Let’s walk through a real-life scenario with a perfect architecture but also with one shortcoming :)

## **Sluggish e-mail campaign solution**

We had a perfect idea to create a tool for email campaigns out of a few already existing external applications. So, we have used CMS to create HTML content for the email.  
We have integrated CRM to personalize email content by collecting user Firstname, Lastname etc. Also, to create target users, we had to integrate Segmentation DB.