---
layout: post
title:  "Software process patterns"
categories: SoftwareEngineering
---


## Software processes

According to Grady Booch[^grady] there are two traits or characteristics that make a **object-oriented system** a succesful one:

[^grady]: Grady Booch, Object-Oriented Analysis and Design, 2nd Ed, Addison-Wesley, 1994. 

- An existence of a strong *architectural* vision.
- An application of a well-*managed* *iterative* *incremental* development cycle

With developing with good software development processes lead to have a high quality of code and to risk reduction. 

A software process is defined as a 

> **structured set of activities for definying, designing, implementing and testing a software system.**

The processes can be divided into:

-	**Macro processes** Those that cover the entire development lifecycle
-	**Micro processes** Those that cover each major software development activity.

#### Macro processes

- Activities are represented on a scale of **weeks to months**
	- Specification
	- Design
	- Validation
	- Evolution
- Serves as a controlling framework for micro process
	
#### Micro processes
- Represents the **daily** activities
- Driven by the stream of *scenarios* and *arquitectural products* that emerge from the macro process.

---

## Process patterns

Process patterns can be divided into two groups:

- Macro process models
- Micro process models

A **process pattern** is:

> A **well-defined**, **predictable** and **repeatable** generic software process model.

Where a software **process model** is 

> An abstract representation of a process.

---

## Macro Process

Among the macro process models are:

- Waterfall (traditional)
- Iterative development (process iteration)
- Incremental development
- Spiral
- Agile
- MDD (Model driven development)

### Waterfall process

The phases are defined by Ian_Summerville[^Ian_Summerville] as:

[^Ian_Summerville]: Ian Summerville, Software Engineering, 6 th Ed. Addison-Wesley, 2000

1. Requirements analysis and definition.
2. System and software design.
3. Implementation and unit testing.
4. Integration and system testing.
5. Operation and maintenance.

There are three things to have in mind if is desired to work with this model:

1. Inflexible partitioning of the project into distinct stages .
2. Not good to respond to requirements change once the project has started.
3. Works well in projects where requirements are well understood.

### Iterative development

- Process iteration : *Successive Refinement* of a process.
- Always present in the process of large systems as system requirements always change throughout the project.
- Process iteration is common in earlier stages of development.
- Applicable with any generic process model.

### Incremental development

- **Decompose** the *development and delivery* into increments, where each of these deliver a part of the functionality required.
- **Prioritize** user requirements, delivering the highest priorities in early increments.
- **Frozen** the requirements once the increment development is started.
- Continue to evolve the requirements for later increments.

![Incremental development model](/assets/incremental_model.svg)

Among the advantages are:

- Customer value are delivered with each increment so system functionality is available earlier
- Early increments act as a prototype to help elicit requirements for later increments
- Lower risk of overall project failure.
- The highest priority system services tend to receive the most testing

### Spiral Development

- The model is represented as a spiral
- Each loop in the spiral represents a phase in the process
- No fixed phase. And loops are chosen depending on what is required.
- Risks are explicitly assessed and resolved throughout the process.

Common activities are:

- Objective setting
- Risk assessment and reduction. Risks are assessed and activities are put in place to recudes key risks.
- Development and validation. A development model can be chosen and can be any generic process model.
- Planning. Project is reviewed and the next phase of the spiral is planned.

### Agile Processes

There are different types of agile processes which share some processes, activities and tools, i.e. iterations or delivering of products with part of the functionality.

Among the agile software processes exist:

1. Extreme Programming (XP). Bases on Test Driven Development (TDD).
2. Feature-Driven Development (FDD).
3. SCRUM
4. Crystal Family
5. Agile Modelling
6. Adaptive Software Development (ASD)
7. Agile Unified Process (AUP)
8. Dynamic System Development Method (DSDM)
9. Kanban (development)
10. Lean Software Development.


#### Extreme Programming XP

Based on developing and delivering **very small increments of the functionality**(similar to incremental development). Relies in three things, constant **code improvement**, **user involvement** in the development team and **pair programming**.

The model is shown in the following figure:

![XP model](/assets/xp_model.svg)

In the design phase the technique of CRC[^crc] which stands for *Class, responsibilities and collaboration* is used to design the system as a team. It helps to think in objects-oriented design instead of procedural.This involves the whole team and the more people collaborates, more ideas are obtained. 

[^crc]: http://www.extremeprogramming.org/rules/crccards.html


#### Model driven development (MDD)

This process sees software develpment as a model building and model transformation activities. 

Separate diferent concerns in different models:

- Computation Independent Model (CIM)
- Platform Independent Model (PIM)
- Platform Specific Model (PSM)

Models and meta-models are primary software artefacts. The main language is UML for model development. This is suppported by automated model transformation and code generation technologies.

![MDD model](/assets/mdd_model.svg)

Models are higher level abstractions than programs and are closer to the problem domain. Thus are easy to understand and share.
Models are programming language independent, hence easy to move to different implementation plattforms.

---

## Micro Process

As commented before, micro processes are those that it lifecycle duration is a day and depends of the macro processes direction. For example:

1. Requirement engineering process
2. Design proces
3. Debugging process
4. Testing process
5. Testing phases
6. Evaluation process

### Requirement engineering process (RE)

Is the process of establishing what **services are required** and *constraints* of the system operation and development. This process is also called software specification.

The phases are:

- Feasibility study
- Requirements elicitation and analysis
- Requirements specification
- Requirements validation

![RE process](/assets/re_process.svg)

### Software design and implementation

Is the process of converting a software specification into an executable system. The **software design** refers to the process to design a software structure that complies to the specification. Whereas the **implementation** is the process of converting the structure into a executable software.
These activities are closely related and may be inter-leaved.

Software design activities:

- Architectural design
- Abstract specification
- Interface design
- Components design
- Data structure design
- Algorithm design

![Software design process model](/assets/design.svg)

Design methods

These are sistematic approaches to developing software design. The design is ussually documented as a set of graphical models(UML models). These are some examples:

- Data flow model
- Entity-relation-attribute model
- Structural model
- Object model

### Programming and debbugging

This process model refers to the activities of translating a design into a program and removing errors from it. Programming is an personal activity, so there is no generic programming process. Programmers carry out some porgram testing to find errors and remove them in the debugging process.

![Debugging model](/assets/debbugging_model.svg)

### Software validation

Verification an validation is intended to show the conformance of a system against its specification and whether meets the system and customer requirements. Involves checking and reviewing of processes and system testing.
System testing is perfomed by executing the system with test cases from the specification of the real data to be processed by the system.

The software validation process follows the next stages:

1. Unit Testing. Individual components are tested.
2. Module testing. Sets of dependent components are tested together.
3. Sub-system testing. Groups of modules are joined together to create a sub-systems, and these are tested. The focus is to test interfaces.
4. System testing. The system is tested as a whole. Testing of emergent properties.
5. Acceptance testing. The systen is tested with customer data to check if it pass the acceptance criteria.

![Test phases](/assets/test_phases.svg)


### Software evolution

Software inherently flexible and can change. As requirements change due to business circumstances, the software that supports the business must also evolve and change. Although there has been a demarcation between development and software evolution (maintenance) this is increasingly irrelevant as fewer and fewer systems are completely new.

![System evolution](/assets/system_evolution_model.svg)




--- 
