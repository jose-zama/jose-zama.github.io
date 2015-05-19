---
layout: post
title:  "GRASP to GOF"
categories: SoftwareEngineering
---


## Kinds of software patterns

- Design patterns
- Architectural patterns
- Coding patterns
- Testing patterns
- Concurrency patterns
- Requirement patterns
- e-business patterns
- etc

## Desing-Patterns Basics

The design patterns are reusable designs, capturing best practices. These represents tools for communicating between experienced designers, pattern names replacing descriptions. Inspired by Christopher Alexander on patterns in architecture. Popularised by the "Gang of four" in 1994 in their book "Design patterns". A design pattern capture existing design ideas that have been used succesfuly several times.

The GoF book, "Design Patterns" of 1994 describes 23 design patterns, divided in creational, structural and behavioural. 

## GRASP principles

Stands for General Responsibility Assignment Software Patterns. It is a set of principles for *assigning responsibilities* to classes. It is the key skill in OO software design. For example **Introduce pure fabrication to mantain high cohesion and low coupling**. 
GoF patterns promote GRASP principles in not obvious ways. GRASP are not pattens, are general principles.

A **pure fabrication** is something that does not correspond to anything in the domain. e.g. collections, intefaces to external systems, factories (classes with the sole purposes to create objects), UI components, indirections and abstractions of other classes. 

Another principle is Polymorphism to improve cohesion and coupling. This principle occurs in the majority of the Gof patterns.

Using inheritance wisely. There must be a clear is-a-kind-of relationship between superclass and subclasses. The subclasses must be disjoint. The resulting classes should be consisnte with other GRASP principles, principally high cohesion. Avoid putting information of the subclass in the superclass. And avoid multiple inheritance.

Another principle, **protected variations** "try to protect your code against variations that might happen in the future. High cohesion and low coupling promote PV. Polymorphism often helps PV. However in practice is very difficuly to predict what will vary.



