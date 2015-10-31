---
layout: post
title:  "GoF - Creational Patterns"
categories: SoftwareEngineering
---

This post is the first of a series of three in which I will describe the design patterns defined in the book *Design patterns* [^GoF] of the Gang of Four (Gof)

[^GoF]: E. Gamma, R. Helm, R. Johnson, and J. Vlissides, “Design patterns: elements of reusable object-oriented software,” Jan. 1995.


## Introduction

When creating an object, we have to decide where is the best place and when to create it and once in practice, is not so easy. GRASP Creator principle says

> Give the responsibility to a class A to create instances of B, if A contains B or if it has the initialization data of B.

Or whe creating intances from persistent storage. Creating objects of class A within the class A is often a good idea. However there are more complex creational issues where is more complicated to know where to create the object.

A pattern called Factory, which is pure fabrication, is often used to define a place to create objects of a determined class. It is another new class that does not belong to the domain, with the only purpose of creating objects.
The advantages are that

- Decouple creation logic from code using the objects created. The interface is very simple. Make the code more understandable.
- The factory itself is cohesive, it has only one job.
- Object creation strategy can change without affecting anything else.
- Information for creating objects can come from external sources. e.g. config files.
- Factories can implement caching strategies, etc. again without affecting other code.

It will be very probable that we might want to have only one factory instance. Thus a singleton pattern can be used.

## Singleton pattern

> Ensure a class only has one instance, and provide a global point of access to it.

This pattern should be used when we want only one instance. Another alternative is to make everything static and not have instances at all.

{% highlight java %}
	class BicycleFactory(){
		public static BicycleFactory instance;
	
		public static syncronized BicycleFactory getInstance(){
			if(instance==null){
				instance = new BicycleFactory();
			}
			return instance;
		}
	//code to create bicycles
	}
}
{% endhighlight %}

The last code used **lazy instantiation**. This means that the factory is created only when is needed. The alternative is called **eager instantiation**:

{% highlight java %}
	class BicycleFactory(){
		public static BicycleFactory instance = new BicycleFactory();
	
		public static syncronized BicycleFactory getInstance(){
			return instance;
		}
	//code to create bicycles
	}
}
{% endhighlight %}

In general, the tradeoff is between initialization time and time later.

## Abstract Factory pattern

> Provide an interface for creating families of related or dependent objects without specifying their concrete classes.

In general a simple factory will create a family of related products. We migth want to separate the different products with separate factories, for example for diffetent types of bicycles (Road or MTB), we can have an abstract factory with the subclasses being this subfactories; The common code can be in the abstract factory. An advantage is that if in the future we might want to add another type of bicycle (Fixie) we just add another factory. 

## Prototype

> Specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype.

This pattern consists in creating objects by copying from an existing object. This requires the class to be the prototype to provide a "copy constructor" in Java a clone() method. JavaBeans are an example. 