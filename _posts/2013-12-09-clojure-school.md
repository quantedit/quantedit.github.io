---
layout: post
title: "Clojure School"
date: 2013-12-09
categories: learning clojure
---

My company [Likely](http://likely.co) hosted a Clojure School for four weeks
from 12th November 2013. Targeted at professional software developers, it aimed to teach the fundamentals of the [Clojure](http://clojure.org/) programming language in a practical way.

### Syllabus

Each class focused on a particular aspect of the Clojure language or its libraries
and walked students from the absolute basics to implementing a
multiplayer browser based game over WebSockets.

The topics for each week were presented as on slides with regular Q&A
and breaks for exercises. The org documents from which the slides were
generated are [linked below](https://github.com/likely/clojure-school).

* [Part 1](https://github.com/likely/clojure-school/blob/master/part-1.org)
  * Setting up with Leiningen & the REPL
  * Data types
  * Collection types
  * Functions
  * Higher-order functions
  * [Example code](https://github.com/likely/weather/blob/master/src/weather/core.clj)
* [Part 2](https://github.com/likely/clojure-school/blob/master/part-2.org)
  * Web development with Clojure
  * Ring, Compojure, Hiccup
  * Mutable state and STM
  * Atoms, Agents, Refs
  * Multithreading with Future
* [Part 3](https://github.com/likely/clojure-school/blob/master/part-3.org)
  * Macros
  * Techniques for managing concurrency
  * Core.async and CSP
  * ClojureScript
  * [Homework template](https://github.com/likely/sketchy)
* [Part 4](https://github.com/likely/clojure-school/blob/master/part-4.org)
  * Polymorphism in Clojure
  * Protocols
  * Multimethods
  * Websockets and channels
  * Building a multiplayer game of snake!
  * [Example code](https://github.com/likely/snake)

### Thanks

Clojure School was part of a series of courses organised with help
from [Dactic](http://dactic.io/).
