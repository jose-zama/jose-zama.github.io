---
layout: post
title:  "Software analisys patterns"
categories: SoftwareEngineering
---


## Analysis Models

An **analysis model** (aka domain model) is

> A abstract representation of a software development problem.

An analysis model is often representad as a **conceptual model** which is

> A concept graph made of a coherent set of domain concepts and relationships.	

**Domain objects** or **domain concepts** are often represented as classes, therefore ussually called **domain classes**. 

A **domain object** is an abstraction of a set of real world things such that

- All the things (instances) in the set share the same characteristics
- All the instances are subject to the same rules.

Most domain objects falls the the next categories:

1. Tangible things
2. Roles
3. Incidents
4. Interactions
5. Specifications

Tangible thigns are the objects you find in the environment. 

**Roles** are played by persons, organisations or systems. They are also called *actors* or *agents*. In user cases the *actor* is the user, which are external to the system. And an *agent* is a worker of a user case, which is internal to the system.

And **incident** is a event or ocurrence, something that happens at a specific time, as a accident, system crash, performance, phone call.

An **interaction** is a transaction or contract between two or more domain objects. i.e. purchase ( related to the buyer, seller and the thing purchased) or marriage (two persons). Other interactins are those services of a bank, deposit, withdrawal, payment, registration.

An **Specification** is a description or definition. i.e. bank statement, transaction, service level agreement, phone bill, order confirmation. **Intangible** or abstract also belong to this category. memory capacity, digital video, song.

To build an analysis model two apporaches can be followed, the conventional: self experience, learning from experts of books, by trial and error. And the other way is by the reuse-oriented apporaches, by adapting an existing model to a new situation or by reusing analysis patterns.


**Analysis Pattern**

An analysis pattern is defined as:

> A *reusable* abstract representation of a coherent set of *domain objects* and their *relationships* for developing an analysis model.

An analysis model may be composed of one or more analysis patterns.

In these notes two analysis patterns are explained

1. Peter Coad's business transaction patterns
2. Martin Fowler's accounting patterns.

## Transaction Patterns

Transaction patterns are reusable analysis patterns found in business transaction application systems like Point-of-sale, CRM, warehouse management and order management systems.

Transaction Patterns

- Line Item

Describes the relationship between a product and its product line

- Container-Content

Describes the relationship between a container and its content.

- Transaction - Line Item

Describes the relationship between a transaction and the product involved in the transaction.

- Transaction - transaction

Describes the relationship between two transactions in a time order.

#### Line item pattern

Represents a binary relationship between an item and line item. An item is a product. 

A line item is

> A record of a purchased or ordered item, which includes the name, number, price and quantity of the product.

Each item can be in one or more item lines.


The advantage of this pattern is that separates the stable part of the product from its variable, thus if the description of the line item change it does not affect the description of the item.

#### Container-content pattern

Is a binary relationship between a thing and its container. A container may have more than one line items (content). Examples, aircraft-cargo, shopping cart-godds, catalogue-catalogue-item, store-goods.

![Container-content](/assets/container_content.svg)


#### Transaction-line item pattern

Represents the binary relationship between a transaction and a product line item. Each transaciton may contain one or more line items. 

The advantage is that it separates the information related to the transaction (date, amount payable) from the information of the purchased product (price, quantity) so that both can be changed independently.

![transaction-lineitem](/assets/transaction_lineitem.svg)

#### Transaction-transaction pattern

Represents a binary relationship between two transactions. A transaction can be followed by 0 or more subsequent transactions. For example, session-sale, sale-payment, session-payment, reservation-cancellation.

![transaction-transaction](/assets/transaction_transaction.svg)

The advantages is the separation of the two transactions to give flexibility to modify the transactions. For example in online shopping, update the shopping cart by adding more items or change the delivery method separately.

## Accounting patterns

This patterns are used in accounting systems which is:

> A system that responds to a business event by creating an accounting entry. For example an utility billing, or a payroll system.

There are four domain objects in this pattern which are:

**Event**

> Describes something that happens that is interesting to the business.

**Accounting entry**

> Records the consequence of an event that need to be tracked.

**Posting rule**

> Determines the accounting entries to make in reponse of an event.

**Account**

> Aggregates related accounting entries and provides a summarising behaviour.

#### Event pattern

Captures a record of events of something interesting. Organises the events into types. Use this pattern to keep log of all the things that cause a change in the system.

![event pattern](/assets/event_pattern.svg)

#### Accounting entry pattern

Records the consequence of an event that needs to be tracked. The accounting entry object records a change made by an event and the descriptor gives details of the change (possibly an account object).

![accounting pattern](/assets/accounting_pattern.svg)

The event pattern and the accounting entry pattern are closely related and should be used together. This link enables the model to answer the question: Why is this entry added?

![link_event_entry](/assets/link_event_entry.svg)

#### Posting Rule

Determines what accounting entries create in response to an event. Example. A gas company (host) get a meter reading (event type) and calculates the consumption accoring to a rate (posting rule) and generates the entries for the bill (accounting entries)

#### Account Pattern

The account object is a container for related account entries. Account is a container-content pattern. Use the account pattern to refine the accounting entry pattern by replacing the descriptor for an account.

![account entry](/assets/account_entry.svg)

## Pattern Forms

Authors use pattern forms or standard templates to describe a pattern. The form used to describe the accounting patterns contains:

- A sentence of the pattern definition
- A diagram to represent the pattern
- An example to illustrate the pattern
- Making it work
- When to use it
- Sample code

## A pattern-based software development process

Is defined as

> A sistematic reuse where analysis and design modes are composed from instances of existing patterns.

The process stages are:

- Problem analysis
- Overall architecture design
- Pattern identification
- Pattern adaptation
- Pattern composition

![pattern based development](/assets/pattern_based.svg)

The model above drives the design process model with analysis patterns. The implementation stage converts the analysis model into a design model. This transformation can or not use design patterns.

