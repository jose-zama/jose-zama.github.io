---
layout: post
title:  "GoF - Structural	 Patterns"
categories: SoftwareEngineering
---

This post is the second of a series of three in which I will describe the design patterns defined in the book *Design patterns* [^GoF] of the Gang of Four (Gof)

[^GoF]: E. Gamma, R. Helm, R. Johnson, and J. Vlissides, “Design patterns: elements of reusable object-oriented software,” Jan. 1995.


## Structural Pattern

#### Adapter

> Convert the interface of a class into another interface clients expect. Adapter lets classes work together that could not otherwise because of incompatible interfaces.

![Adapter](/assets/adapter.svg)

The Gof provides of two versions of the adapter, the class adapter and the object pattern although the former goes against the cohesion principle and inheritance rules.

An adapter allows to communicate with external or internal systems that have different interfaces without chanding the core code by adding an adapter in the middle.

#### Proxy 

> Provide a surrogate or placeholder for another object to control access to it.

![Proxy](/assets/proxy.svg)

The client access the "subject" through an interface both real and proxy subjects implements. The client access the proxy subject and the proxy delegates operations to the real subject. So the client *sees* the real subject. The proxy manages the real subject in some way. It can be a remote proxy, that simulates a remote subject to be local. Or a performance proxy, that implements caching techniques to improve performance.

Proxies provide indirect access to, and managemenet of, objects by adding an intermediate object with the same interface.

#### Decorator

> Attach additional responsiblities to an object dynamically. 

A decorates is an abstact class that has the interface that the class to be decorated. Subclasses (decorators) that implements the abstract class extends the functionality in runtime wihtout updating the code of the decorated class. The advantage is that the original class remains cohesive. 

![Decorator](/assets/decorator.svg)

Adding a decorator allows to add extra functionality without reducing cohesion.

#### Flyweigth

> Use sharing to support large numbers of fine-grained objects efficiently.

The flyweight helps to reduce memory usage by creating flyweith objects through a factory. This would cache existing objects and return them instead of creating new ones. This probably would not be singletons. 

In we think in a text processor, where the characters are flyweight objects, and this charactes has a state (color, font, size) we would not want that if one instance state change, change all the references to it. 

Use it wisely, due to it is optimization but add complexity. Flyweight objects may have an instrinsic state and a extrinsic state. An instrincis state is that that is not related to the context while the extrinsic does. Those objects with extrinsic state cannot be shared. 

Accorgin to GoF use it only if all of the following are true:

- An application use a large number of objects.
- Storage costs are high because of the sheer quantity of objects.
- Most object state can be made extrinsic.
- Many groups of objects can be replaced by relatively few shared objects once the extrinsic state has been removed.
- The application does not depend on object identity.

![Flyweight](/assets/flyweight.svg)

In conclusion, flyweight pattern allows to reduce the number of objects by sharing them , even if they change state.

## Behavioural Pattern

#### Interpreter

> Given a language, define a representation for its grammar along with an interpreter that uses the representation to interpret the sentences in the language.

Code is harder to change than data. So avoid wirind data in the code. In general, take as much information from the code, data driven programming. If the data is complex, we will need to parse it. Interpreter parse it and interpret it as well. 

![Interpreter](/assets/interpreter.svg)

We have a class for every symbol. NonTerminals symbols compute the production rules within their classes. The result at runtime is a tree structure, with nonterminals at the internal nodes and terminals in the leaves.

#### Command

> Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and undoable operations.

A command pattern then, encapsulates user level commands into objects. These objects has the information to undo commands. A list of these objects forms a command history, allowing arbitrary levels of undo and redo. 

#### Observer

> Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

We have objects whose state changes *observables* and objects to need to react to those changes *observers*. For example in Java swing UI, JButtons, JMEnuItems etc. are observables. Aplication code objects are observers. And both implements inerfaces to be communicated. 

![Observer](/assets/observer.svg)

So the flow would be, the observer suscribes itself to a observable. The observable when changes its state, publish it to its observers. Finally observers act to this change.

We can easily add more obervers and observables (polymorphism/protected variations)

#### State 

> Allow an object to alter its behaviour when its internal state change. The object will appear to change its class.

An object that changes its behaviour over time could be implemented with an enumeration of states and switch statements. However it will make the class complex and hard to mantain.

![State](/assets/state.svg)

Behaviour that does not change in the class is implemented in the superclass. State-specific behaviour is implemented different in each subclass. States are described independently of the transitions between them. Adding a new state means just to add a new subclass. But adding a new operation means adding it in each class.
