+++
title="2021-12-11"
date=2021-12-11
+++

A recent interview with Anders Hejlsberg!

![Anders Hejlsberg](2021-12-11/2021-12-11-01-09-01.png)

{{ youtube(id="K3qf8gRFESU")}}

I found this on [Hacker News](https://news.ycombinator.com/item?id=29514900)

- His brother is one of the interviewers
- They started programming 40 years ago in Copenhagen
- Started using high school computer in the 1970s
- Started by implementing a programming language, Turbo Pascal
- Cut his teeth by adding extensions to existing language to make it useful
- C# was first language designed from scratch
- "You can always add but you can never take away"
- The perfect programming language is one with no users(!)
- V1.0 is the only greenfield 
- Game of learning to say no vs. yes
- Language features asks come from people with an instance of a problem - he
  tries to find the class of problems that it belongs to
- HTML is an incomprehensible mess :)
- TypeScript was the first foray of a project that, from the onset was open
  source
- Wanted Roslyn to be open source, but C# and .NET was not open source
- Roslyn was not built as open source, was open sourced later
- Open development - 2014 moved to GitHub - everything is on GitHub is the
  next step, e.g., design notes - close to users
- Anders participates in C# design committee, but Mads has been running it for
  the last decade(!)
- Multiple inheritence - usefulness does not outweigh the downsides of
  additional complexity
- If he could change one thing in C# he would have nullability and
  value/reference types as orthogonal issues, e.g., you cannot have
  non-nullable reference types
- Tony Hoare called inventing null his billion dollar mistake
- Functional programming languages do not enable circular reference data types
  (e.g., double-linked list or trees with back-pointers)
- Opting into nullability in specific areas
- Don Syme did most of the implementation of generics in .NET 2.0
- He regrets dynamic in C# 4.0
- He likes the work done in C# 5.0 for async/await
- TypeScript - how solve the nullability problem. He is very happy with that
  result.
- Turbo Pascal 1.0 symbol table was a linked list(!)
- He read [Algorithms + Data Structures =
  Programs](http://www.cl72.org/110dataAlgo/Algorithms%20%20%20Data%20Structures%20=%20Programs%20[Wirth%201976-02].pdf)
  by Niklas Wirth - learned about hash tables and then reimplemented the
  symbol table in Turbo Pascal 2.0 using them [local copy in case this
  disappears from the web](2021-12-11/AlgoDataProgWirth.pdf)
- He learned by trial and error without formal background