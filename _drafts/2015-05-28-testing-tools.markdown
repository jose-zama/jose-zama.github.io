---
layout: post
title:  "Testing and tools"
categories: SoftwareEngineering
---

## Changing interface VS refactor

Refactor is to change the structure of the code without affecting behaviour. Behabiour is:

- The function that is performed by the code
- The interface, API, services provided to the world

## When to refactor

- Complexity
	- Assignments, branches, calls (ABC)
	- Cyclometric complexity
	- Consider refactoring high score methods
- Structural similarity
	- Consider refactoring similar code
	
Dont do it by hand , use tools.

## Grading code

When grading, it uses the metrics complexity and similarity and a grade is assigned to the classes (A-D or F) and the code gets a GPA.

## Comprehensive testing

Lets say I change a test, instead of asserting true, change to false. A test should fail, if not a test is missing. There are tools that do this.

## Code coverage

IS good to revise the test coverage, though having a high test coverage does not mean high quality. This because most of the code could be support code as importing or code syntax, instead of code with real functionality.

## Why to do all this

- To maintain high quality.
	- No suprises
	- To facilitate the evolution of the code.
- Shared ownership of code
	- Different people working on the same code

## Other test helpers

### Fixture

