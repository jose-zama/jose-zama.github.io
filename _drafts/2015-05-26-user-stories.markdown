---
layout: post
title:  "User stories"
categories: SoftwareEngineering
---

A user story could be defined as:

> A short description of user or customer valued functionality.

Composed by:

- **Card** containing a description of the story for planning and as a reminder.
- **Conversation** about the story to flesh out the details.
- **Confirmation** tests that documents details and can be used to determine when the user story is complete.

### Examples of good user stories

- The user can export data to XML.
- As a registered user, i want to log in to access subscriber content.

### Examples of bad user stories

- The software will be written in Java.
- The system will be released by september 30th.

## Writing user stories

Use the INVEST acronym:

- Independent
- Negotiable
- Valuable to customers
- Estimable
- Small
- Testable

### Independent

Independent stories make easier the planning and prioritization. 

But stories are not always independent:

- One feature must be in place before another.
	- To develop iterative and incrementally.
- The presence of one feature affects another
	- Combine or split stories.
	
### Negotiable

User stories are short **descriptions of functionality**, not contracts or requirements.

Details are **negotiated** via conversation. Cards are a reminder to have that conversation. This details can be written on a part of the card.

### Valuable to customers or users

This means that the user story should describe a feature that is interesting to the customer , e.g. avoid any technical solution or characteristic.

### Estimable

Developers must be able to estimate the story size and the time it will take to code it. There are three problems that can difficult the estimation which are:

- Lack of domain knowledge. Talk with the customer.
- Lack of technical knowledge. Go on a 'spike'.
- Story is too big. Break it down and leave it as an epic.

### Small

Size matters. Big stories are hard to plan and estimate. Also stories should not be too small. The size of the stories depend on team capabilities and technologies they use.

Stories that are too large are usually compound or complex stories.

#### Compound stories

Compound stories comprise multiple small stories. e.g.:

- A job seeker can post a CV
	- A job seeker can post several CV's
	- A job seeker can mark a CV as inactive.
	- A CV can include job info, salary info...

#### Complex stories

Complex stories involve uncertainty and/or difficult:

- Unfamiliar technology. Go on spike.
- Novel algorithm development. Add a research story.

The story should be splitted into a research and implementation, an put them in different iterations.

### Testable

It is possible to test a story, so we can know when is done. We want tests to be automated although no all tests can be.

### Product backlog 

Flexible format

|as a/an| I want to... | ... so that... | Done criteria |
|-|-|-|-|-|
| potential customer | sign up for email alerts |    i can receive special offers |Email alert sent to registered users | 
