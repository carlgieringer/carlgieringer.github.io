---
title: What I have learned (so far) working at Google
last_modified: 2022-05-07
---

This post is a work-in-progress highlighting the important things I have learned working
at Google. It highlights some important professional and cultural issues that arise from working at
a high-productivity organization like Google.

## The importance of design docs

Significant changes or projects at Google almost always start with a document. 
The document usually has multiple approvers (people who must agree on the substance of the contents)
or reviewers (people who should be aware of or provide input to the contents.)

The docs sometimes begin as just rough notes or one-pagers. Sometimes the one-pagers remain initial
'executive summaries' and sometimes the one-pagers become the full design doc.

The benefits of design docs:

* Provides background on why certain design decisions were made
* Helps to reach and document consensus
* Makes it easier to coordinate remotely
* Provides confidence that alternatives were thoroughly considered
* Provide evidence of leadership and technical ability for promotion

Useful metadata to include in design docs:

* Author(s) (along with each contributors role, if the authorship was unequal.)
* Date created and date modified
* Status: (Draft, In Review, Approved, Implemented/Final, Obsolete)
* A change log
  * For large long-living design docs, a manually created change log helps readers to
    understand what has changed since they last read the document.
    
Part of implementing a solution often includes creating source-controlled documentation.
This documentation is often a summary of the "what" and "how" of the system with less of
the "why" that was in the design doc. The documentation can link to the design doc for
more background.

## The importance of alternative solutions

Earlier in my career, I often thought that I had discovered the one right way to do something.
This attitude is more common with smaller changes, such as a single line of code, a single 
method, a single class, etc. But with larger systems, it soon becomes clear that any particular
design embodies a balance of the non-functional qualities.

This realization is the "engineering" of software engineering. Programmers write code. Engineers
analyze problems and weigh the the relative tradeoffs of different designs.

Non-functional qualities:

* Execution speed (latency/throughput)
* Development speed
* Security
* Privacy
* ...

Wikipedia has an impressively long list of [examples](https://en.wikipedia.org/wiki/Non-functional_requirement#Examples).

## The importance of a growth mindset

A company like Google hires talented people. I learned working there that talented people
don't have any special abilities to know everything, and that they ask a lot of questions.
Googlers often have a "I don't know how to do that, but I can learn" attitude because
it's required in order to succeed at a company of that size with so many systems.

## The importance of communicating status and change

In high productivity organizations, attention is a scarce resource. You often cannot rely
on others to passively discover things. Instead, leaders recognize when it is important
for some audience to pay attention to something, and they communicate those things in
an appropriate medium.

* Tech talks
* Design doc reviews
* Emails (cc'ing a group list for discovery and historical preservation.)

If your organization has good internal search, as well as a culture of self-discovery,
you can probably rely on people to discover some 'status' pages.

Example status pages:

* Team pages: who's on the team, what we do, how to communicate with us
* System documentation: what the system does, how to use it, how to get help.

There are two important signals that active communication is required, though: confusion and change.

Confusion: sometimes people have misconceptions or misunderstandings about what a team does,
how a process should work, how a system works, whether a system is deprecated, etc. When
leaders observe this confusion, they plan to course correct the confusion, often with an email
or presentation. Usually they will record the presentation for posterity or for people who
could not attend.

Change: it's the only constant. Leaders anticipate which changes require attention, and from
which audiences. They proactively schedule communication in order to prevent lack of awareness
and confusion.
