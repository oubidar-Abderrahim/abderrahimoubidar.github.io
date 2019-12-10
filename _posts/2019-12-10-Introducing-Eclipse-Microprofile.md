---
layout: post
date: 2019-12-10
title: Introducing Eclipse Microprofile!
excerpt_separator: <!--more-->
---
                                                                                                              
Greetings!
<!--more-->

Java EE has been an extremely successful platform. The **Java Community Process (JCP)** has been the steward of over 20 compatible implementations during its nearly 20-year history, resulting in a $4 billion industry. However, the management of Java EE by Oracle (unintentional or not) of Java EE (unintentional or not) stalled innovations, and while other standards have developed, the Java community worldwide and CIOs at all major enterprises desired an open standard for Java within their enterprise.

In its early stages, J2EE grew somewhat quickly from J2EE 1.2 up to J2EE 1.4, as the platform needed to address the immediate requirements of the enterprise. Beginning with Java EE 5 in May 2006, the pace began to slow down as the platform began to mature, and it was 3 years and 6 months between releases. After Java EE 7, which was released on June 12, 2013, there has been a long delay in its development. Java EE 8 was formally launched in September 2014 at JavaOne, where Oracle announced that it would be completed by JavaOne 2016. But then in June 2015, Oracle updated its release date to the first half of 2017. And again, at JavaOne 2016 (September), Oracle revised the Java EE 8 release date to the end of 2017. Java EE 8 was finally released on September 21, 2017, at JavaOne.

Java EE had been following the slower release cadence that a standards organization typically reflects. A standards-based release cadence by design does not address rapid innovations. And while this was occurring, the digital economy happened, which brought about the popularity and rising use of the cloud, containers, Agile methodologies, DevOps, continuous integration and continuous delivery, microservices, API management, and open source projects (Red Hat has been successful in delivering many of these solutions to the marketplace).

The slowdown in Java EE releases (and maturity) opened the door to competing technologies, such as Spring and Node.js, for example, which were able to fulfill the needs and requirements of digital businesses. In addition to this, many vendors, such as Red Hat and IBM, started innovating with Enterprise Java microservices based on a subset of Java EE and decided to collaborate in the open, potentially providing a wider effort upstream. This culminated in the announcement of Eclipse MicroProfile in June 2016 by many vendors, Java Champions, Java User Groups, and corporations.

Since MicroProfile was announced on June 27, 2016, at DevNation, a lot has happened. MicroProfile v 1.0 was released on September 19, 2016. Its implementation interoperability was demonstrated in November 2016 at Devoxx Belgium, where Red Hat, IBM, Tomitribe, and Payara demonstrated a unified web application (known as the Conference Application) with underlying microservices that had been developed separately by each vendor using MicroProfile. Additionally, MicroProfile became part of the Eclipse Foundation as an incubation project on December 14, 2016. New members, including SOUJava, Hazelcast, Fujitsu, Hammock, kumuluzEE, Oracle, Lightbend, and Microsoft, have joined the MicroProfile project. The complete list of members can be found at [microprofile](https://microprofile.io/).

Eclipse MicroProfile is a community-driven innovation project whose goal is to work on microservice patterns for Enterprise Java and to integrate applications with the infrastructures they run on (that is, a cloud environment) with patterns such as health checks and metrics. The focus of Eclipse MicroProfile is rapid collaborative innovation and this is why the project has a time-boxed release schedule, with each release including incremental updates or new features, and there is no guarantee of backward compatibility across releases. The Eclipse MicroProfile community is composed of individuals, vendors, and organizations.

Eclipse MicroProfile is not Java EE or a subset of Java EE. This confusion occurred because the first release of MicroProfile (before it became part of the Eclipse Foundation) was a collection of three Java EE APIs, namely, CDI, JSON-P, and JAX-RS. The MicroProfile community purposely made the first release of MicroProfile small because they wanted the community to decide the best path of evolution for the project.

The MicroProfile community took a no need to reinvent the wheel approach for the first release and chose three enterprise-grade, market- and production-proven APIs from Java EE to get started. In fact, MicroProfile utilizes some existing Java EE APIs and combines them with new APIs to create a platform for Java microservice architectures.

At the time of writing this article, Eclipse MicroProfile consists of 12 APIs (or sub-projects) under the project umbrella. Four of them come from Java EE APIs: CDI, JSON-P, JAX-RS, and JSON-B, and the remaining eight are MicroProfile-specific project. They are as follows:

+ Config
+ Fault Tolerance
+ JWT Propagation
+ Health Check
+ Metrics
+ Open API
+ Open Tracing
+ REST Client
+ CDI (a specification from Java EE)
+ JSON-P (a specification from Java EE)
+ JAX-RS (a specification from Java EE)
+ JSON-B (a specification from Java EE)


Here is a high-level explanation of the requirement that each of the aforementioned APIs fulfills:

+ **MicroProfile Config** addresses the need for changing the environmental parameters as an application or microservice moves across development, unit testing, integration/system testing, preproduction, and production environments, for example. MicroProfile Config makes it possible to set or modify configuration data from outside the application without repackaging it.
+ **MicroProfile Fault Tolerance** provides different strategies for when an application or microservice encounters a fault. MicroProfile Fault Tolerance provides specifications for constructs such as retries, circuit breakers, bulkheads, and timeouts, among others.
+ **MicroProfile JWT Propagation** handles security propagation across microservices.
+ **MicroProfile Health Check** fulfills the need to probe the state of a computing node from another machine, that is, a Kubernetes service controller. This specification examines cloud-infrastructure environments where the node state is tracked by automated processes.
+ **MicroProfile Metrics** delivers on the need to monitor the essential parameters of a running service, such as the system, application, business- and vendor-specific metrics in order to ensure its reliable operation.
+ **MicroProfile Open API** provides Java interfaces and programming models to natively produce OpenAPI v3 documents for RESTful services that can facilitate the management of microservice APIs.
+ **MicroProfile Open Tracing** defines the specification for equipping microservices to be traceable in a highly-distributed environment where messages can traverse different architectural tiers and services.
+ **MicroProfile REST Client** provides a type-safe approach to invoke RESTful services over HTTP in a consistent and easy-to-reuse fashion.
+ **CDI** (a specification from Java EE) handles all aspects of dependency injection.
+ **JSON-P** (a specification from Java EE) covers all aspects related to the processing of JSON objects.
+ **JAX-RS** (a specification from Java EE) handles all aspects related to RESTful communication.
+ **JSON-B** (a specification from Java EE) covers all aspects related from the object to JSON mapping.

It is worth mentioning that all the APIs (or sub-projects) created by the MicroProfile projects are not created in a vacuum. Although anybody can participate and is welcome in any sub-project, members of each sub-project are subject-matter experts with long and extensive expertise and experience. They apply their knowledge gained from the field, considering best practices, past lessons-learned, and other existing open source specifications and projects, to come up with the best approach for the corresponding MicroProfile sub-project.

Eclipse MicroProfile has been evolving rapidly and their versions have been progressively adding more functionality as follows:

+ Eclipse MicroProfile 1.1 included Config, which is a MicroProfile sub-project
+ Eclipse MicroProfile 1.2 included updates to Config as well as the new MicroProfile sub-projects: JWT Propagation, Metrics, Fault Tolerance, and Health Check.
+ Likewise, Eclipse MicroProfile 1.3 included additional brand new MicroProfile sub-projects: Open API, Open Tracing, and Rest Client.
+ MicroProfile 1.4 included updates to Config, JWT Propagation, Fault Tolerance, Open Tracing, and Rest Client.
+ In addition, MicroProfile 2.0 included the latest updates to CDI, JSON-P, JAX-RS, and the addition of JSON-B, all from Java EE 8. With these releases, Eclipse MicroProfile will offer the same level of functionality to be usable with either Java EE 7 or Java EE 8.
+ Eclipse MicroProfile 2.1 included updates to Open Tracing.
+ Eclipse MicroProfile 2.2 included updates to Fault Tolerance, Type Safe Rest Client, Open API, and Open Tracing.
+ Lastly, MicroProfile 3.0 included updates to Rest Client, and non-backward-compatible changes to Metrics and Health Check.

There are currently many implementations of Eclipse MicroProfile on the market. Eclipse MicroProfile is one of the tools that developers can leverage to solve problems and implement solutions with the enterprise capabilities needed to run workloads in production. In addition, developers familiar with Enterprise Java frameworks, such as Java EE, will find in MicroProfile a natural progression of Enterprise Java into the world of cloud-native application development.

Thank you for following this introduction to Eclipse MicroProfile from [Hands-On Entreprise Java Microservices with Eclipse MicroProfile!](https://www.oreilly.com/library/view/hands-on-enterprise-java/9781838643102/)
