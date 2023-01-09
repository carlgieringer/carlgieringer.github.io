---
title: Lessons in software engineering from working at Google
last_modified: 2022-05-07
---

This post highlights some professional insights I have gained about software engineering working at
Google.

## 'Doc-driven design'

Even modest code changes or projects at Google often start with a document. The document usually has
multiple approvers (people who must agree on the substance of the contents) or reviewers (people who
should be aware of or provide input to the contents.)

The docs sometimes begin as just rough notes or one-pagers. Sometimes the one-pagers remain initial
'executive summaries' and sometimes the one-pagers become the full design doc. For large projects,
there are hierarchies (or more often networks, because Google communication is somewhat
cross-organizational ([goomics-62])) of many related documents. Each document (should) have a single
purpose, and it defers some related details or decisions to other documents.

The benefits of design docs:

* Provides background on why certain design decisions were made
* Helps to reach and document consensus
* Makes it easier to coordinate remotely
* Provides confidence that alternatives were thoroughly considered
* Provide evidence of leadership and technical ability for promotion

Useful metadata to include in design docs:

* Author(s) (along with each contributor's role, if the authorship was unequal.)
* Date created and date modified
* Status: (Draft, In Review, Approved, Implemented/Final, Obsolete)
* A changelog
  * For large long-living design docs, a manually created change log helps readers to understand
    what has changed since they last read the document.

Part of implementing a solution often includes creating source-controlled documentation. This
documentation is often a summary of the "what" and "how" of the system with less of the "why" that
was in the design doc. The documentation can link to the design doc for more background.

## A solution is often as strong as its alternatives considered

Earlier in my career, I often thought that I had discovered the one right way to do something. This
attitude is more common with smaller changes, such as a single line of code, a single method, a
single class, etc. But with larger systems, it soon becomes clear that any particular design
embodies a balance of the non-functional qualities.

This realization is one part of the "engineering" of software engineering. (Others include coordinating 
groups of people and managing change over time.)  Programmers write code. Engineers
analyze problems and weigh the the relative tradeoffs of different designs.

Non-functional qualities:

* Execution speed (latency/throughput)
* Development speed
* Security
* Privacy
* ...

Wikipedia has an impressively long list of
[examples](https://en.wikipedia.org/wiki/Non-functional_requirement#Examples).

## Growth mindset

A company like Google hires talented people. I learned working there that talented people don't have
any special abilities to know everything, and that they ask a lot of questions. Googlers often have
a "I don't know how to do that, but I can learn" attitude because it's required in order to succeed
at a company of that size with so many systems.

## Seniority means more ambiguity/uncertainty

Prior to coming to Google, I had (mistakenly) assumed that seniority primarily corresponded with
scope. The more you were responsible for, the more senior you were. And that is true, but it's
not the whole picture.

The most important thing that comes with seniority is responsibility for ambiguous problem spaces.
In concrete terms, the more senior you are, the more the organization is depending on you to
understand and make decisions in problem spaces where there may be no one right answer.

So if you don't know what to do, that may be a really good thing! Does anyone know what to do? If not,
and you're the one responsible for figuring it out, then congratulations: you have seniority.

Here is a table outlining roughly the levels of engineering and their responsibility as it
relates to ambiguous or uncertain problem spaces:

| Level        | Role           | Description                                                                       |
| ---          | ---            | ---                                                                               |
| Entry level  | Execution      | We've designed the solution, and we need you to execute it.                       |
| "Engineer"   | Tactics        | We've clarified the problem, and we need you to design the solution.              |
| Senior       | Strategy       | We've prioritized a problem, and we need you to create a strategy for solving it. |
| Staff        | Prioritization | We know problems exist here, and we need you to identify and prioritize them.     |
| Principal    | Vision         | We don't know whether or where problems exist, please guide us.                   |

## Communicating status and change

In high productivity organizations, attention is a scarce resource. You often cannot rely on others
to passively discover things. Instead, leaders recognize when it is important for some audience to
pay attention to something, and they communicate those things in an appropriate medium.

* Tech talks
* Design doc reviews
* Emails (cc'ing a group list for discovery and historical preservation.)

If your organization has good internal search, as well as a culture of self-discovery, you can
probably rely on people to discover some 'status' pages.

Example status pages:

* Team pages: who's on the team, what we do, how to communicate with us
* System documentation: what the system does, how to use it, how to get help.

There are two important signals that active communication is required, though: confusion and change.

Confusion: sometimes people have misconceptions or misunderstandings about what a team does, how a
process should work, how a system works, whether a system is deprecated, etc. When leaders observe
this confusion, they plan to course correct the confusion, often with an email or presentation.
Usually they will record the presentation for posterity or for people who could not attend.

Change: it's the only constant. Leaders anticipate which changes require attention, and from which
audiences. They proactively schedule communication in order to prevent lack of awareness and
confusion.

## The Peter principle

Often phrased something like:

> Most organizations promote people based upon success in their current role, which leads to members
> being promoted until they reach their level of incompetence.

this idea is explained well elsewhere. ([E.g.](https://www.youtube.com/watch?v=IbFr5DAyZBM)).

Google fends off the Peter principle in a couple of ways. The first and most direct is that
promotion requires sustained performance at the new level. An engineer must already have been
performing at L+1 for at least six months, perhaps a year, before they are ready for promotion.

The second is that Google attracts and rewards technical experience. In many companies, you reach
the top of the engineering ladder within five to ten years, and your only option for upward mobility
at that point is enter management. Fulfilling Peter's principle, employees often try to trade in
their past success as engineers to become better compensated managers, with mixed success.

At Google, it can take twenty or more years to reach the pinnacle of the engineering ladder.

Not every company could achieve this model; it requires compensating employees well enough that they
are happy to work at L+1 prior to being officially promoted to that level. And having many senior
technical staff requires lot of complex impactful work.

[goomics-62]: https://goomics.net/62/