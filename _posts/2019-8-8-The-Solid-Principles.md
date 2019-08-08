---
layout: post
date: 2019-8-8
title: The Solid Principles
excerpt_separator: <!--more-->
---
                                                                                                              
Greetings!
<!--more-->

There are a lot of best practices and design patterns that keep popping up to software developers during their search for greatness. One of this best practices for object oriented programming is the SOLID principles.

What is the SOLID principles :
---

SOLID is an acronym, Each of its five letters represent a single principle. Listed in order, they are as follows:

* **S**ingle Responsibility Principle
* **O**pen-Closed Principle
* **L**iskov Substitution Principle
* **I**nterface Segregation Principle
* **D**ependency Inversion Principle

We will see each principle in a second, stay tuned


Single Responsibility Principle
---

Put shortly, the Single Responsibility Principle (SRP) tells us that an object should do one thing, and it should do it well. In the words of George C. Martin, “A class should have only one reason to change”. 

You might be asking: "What if a class is suited to keep track of two or more things together?" I sure did ask this at first, but then I realized that he wasn’t talking about variable states, but about reasons to exist. If a class is designed to parse a document and then display it to the user, it actually has two reasons to exist, and therefore it has two reasons to change. Either the documents content could change (and with it, the process of parsing it), or the format of the document could change (and therefore, change the way it should be displayed). These two responsibilities should, according to SRP, be split into two different classes, each one with a single reason to exist.

Open-Closed Principle
---

the open-closed principle states that software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification; that is, such an entity can allow its behaviour to be extended without modifying its source code.

It’s generally a good and very sought-after feat that a software object is extendable. This makes it easier for others to keep building on your work by adding more functionality to a new class, using yours as a parent.

On the other hand, you generally don’t want your code to be so open that another developer may override some method that is only meant to be used internally, and therefore change the behavior of your entire class.

What this whole principle basically says is:
Access modifiers are good. Use them to control what parts of your API others should have access to, but without being so restrictive that it takes away the benefits of using your code altogether. You should think about what information other may find useful and expose it, while keeping the internal workings private.

Liskov Substitution Principle
---

This idea was formulated by Barbara Liskov in 1987, and it says that any method or function that use an object of a class must be able to use an object of derived classes without knowing it. In simple words, Whenever a type T has a subclass of type S, one should be able to replace T with S without altering the correctness of the program.

Let’s say you have a Rectangle class, with a method that calculates its area. If you added a Square class that inherited from Rectangle, the Square would actually be able to replace the Rectangle object without messing with our results. There is an is-a relationship between the two that makes this possible, since a Square is a sort of Rectangle.

However, creating a Circle class and making it a subclass of Rectangle might not be such a great idea. Mainly because they calculate their areas in completely different ways, but also because they don’t share the same is-a relationship. Circle and Rectangle may both conform to a Shape protocol, but they are not suitable for subclassing in that manner.

The Liskov Substitution Principle is a way of ensuring that inheritance is used correctly.

Interface Segregation Principle
---

ISP states that no client should be forced to depend on methods it does not use.

A very nice and illustrative example of this principle is the popular Swift protocol Codable. Since it only specifies two methods, one for initializing a new object from a Decoder, and one for encoding an object to an Encoder, the Swift engineers could easily have stopped there.

However, someone came up with the idea that encoding and decoding are two very different processes, even though they do have a lot in common. The solution was to separate the method into two different protocols, Encodable and Decodable, and make Codable a composition of those two. By choosing this approach, developers who are only interested in decoding information are not forced to implement the encoding part, and vice versa.

Dependency Inversion Principle
---

The Dependency Inversion Principle states that one should depend on abstractions, not concretion. At first, that whole sentence seems very abstract, so let's concretize it.

Imagine that we’re creating a class that is going to store a whole lot of numbers. We could create a variable of type ArrayList and use that to store our numbers, but then we’d be painting ourselves into a corner. What if we realize later on that an ArrayList wasn’t the best choice and now we are depending on the specific methods of that particular class, methods that other classes may not have?

The solution to the above problem is to create a variable of type List. Since List is an interface, and not a concrete class, it only acts as a contract that a certain set of methods are always going to be available, no matter what class is performing the work. Replacing the actual class later on will therefore be as easy as just changing one line of code. Sweet!

The general idea of this principle is as simple as it is important: High-level modules, which provide complex logic, should be easily reusable and unaffected by changes in low-level modules, which provide utility features.

That’s it for this time! I hope you learned something from this article.

Thank you, regards.
