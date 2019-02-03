---
layout: post
date: 2018-5-3
title: How to map java.time.year with JA and Hibernate 
excerpt_separator: <!--more-->
---
                                                                                                              
Greetings!
<!--more-->

JPA 2.2 and Hibernate support several classes of the Date and Time API. Unfortunately, the java.time.Year class isn’t one of them. If you want to use it as an attribute type, you need to provide a custom mapping for it.

But don’t worry, you can do that easily with an [AttributeConverter](https://thoughts-on-java.org/jpa-21-how-to-implement-type-converter/), and it only requires a few lines of code.

An AttributeConverter provides a portable way to create custom type mappings. The only thing you need to do is to implement the *AttributeConverter* interface and annotate your class with the *@Converter* annotation.

Implementing the YearConverter
---

Here you can see an example of an AttributeConverter that maps a *java.time.Year* object to a Short.



 
 
Thank you, regards. 
