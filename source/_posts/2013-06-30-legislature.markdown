---
layout: post
title: "legislature"
date: 2013-06-30 23:45
comments: true
categories: 
---

Coding and Legislature
====

I've never understood why we don't employ standard software engineering practices when creating laws.

* Comments, Documentation, Readable Code
* Version Control
* Boilerplate and DRY
* Refactoring
* Modularity
* Code Reviews
* Beta Testing
* Use Cases, Case Scenarios, Feature Testing
* User Experience and Interface Design


### Documentation

Clearly, written laws not meant to be understood by laymen.  That's okay though, we have compilers that translate our English code into binary form.

Now I'm not saying write laws as a form of code, or even pseudo code. Thats a bit extreme.  But readable code is considered to be goal, not a detriment.  When we can't write legible code, we add comments to explain the purpose of the line or stanza.  We'll even document the code and its entire processes externally elsewhere, to help others follow along with our intentions.

Often we'll take the extra step of designing the process first, before any code is written.  Using English and obtaining agreement from all concerns parties on the "design" of the process before starting the actual implementation.

With this implementation kept separate from the design and intention, we can obtain agreement on the "goals" of said process.  And if we can't reach an agreement on the implementation of the process then it turns out we really didn't have agreement on the design. Or the design wasn't clear enough to begin with.

### Design Patterns and Refactoring

When code gets hard to understand we employ various maneuvers to keep it readable, understandable, and maintainable.

We break off pieces of the code into other projects, other files.  Abstracting and refactoring the commonalities, breaking out the patterns, and rewriting the code into something more concise, that conveys just the notion it was meant to.


### Version Control and Code Reviews

Our "code review" process today in the law making process is well known to be terrible. Many laws and versions of laws are never inspected by all the necessary law makers before making it into the books.

We tend to employ simple version control techniques to follow the changes made to code over time. Pull request are an idea way to implement Code Reviews to ensure every change is heavily vetted before its made live.

### Testing, Testing, Testing

We test a lot in software engineering. We find ways to verify the behavior of a piece of code before it does live, or more importantly, verify that we haven't improperly altered the previous behavior of code after we've changed it.

Review laws and apply them, experimentally, against previously recorded and vetted case scenarios.  Existing people, real or fictitious, who embody the traits effected by these laws.  Do they effect people they shouldn't.  And can we somehow prove that they actually effect the change they desire to make?

Couldn't we have a single state or section of the country where new laws are tried out experimentally before they pass for the entire country?



### Human Experience

* Can a normal person understand the law, its purpose, its effects?
* Does it seem nonsensical, convoluted to everyone other than the author?
* Can an average person understand what to do to live by that law, and to avoid breaking it.
* Finally, does it improve or reduce the happiness in a persons life or break our fundamental freedoms and human rights?


### Wrap Up

There's a general analogy here between Code and Law. A think there's more similarity than difference between them.

Now this is, of course, a very immature proposal.  You know they say that when all you have is a hammer, every problem looks like a nail.  And, full disclosure, I am a Software Engineer, after all.

But I suppose there are probably some carpenters out there that think driving a nail into the head of every representative would be a great way to solve all of our legal problems.






