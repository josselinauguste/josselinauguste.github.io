---
layout: post
title: "Interesting Stuff #3"
date: 2018-01-24T19:02:59+01:00
---

## [Haxl: A Big Hammer for Concurrency by Simon Marlow](https://www.youtube.com/watch?v=sT6VJkkhy0o)

[Haxl](https://github.com/facebook/Haxl) is an Haskell library which completely abstracts concurrency, allowing to use it almost transparently when possible, and as easily as by nesting our code in a `do` block. This gives us concurrency, caching, testability (or at least snapshot testing) and reproductibility for debugging for almost free.

This looks like an interesting paradigm, at least conceptually, because, in the same way memory management was automated 20 years ago to drastically facilitate our daily job, it is still sad that we have to manually manage such a complex topic.

On a side note, Facebook seems to really did the functional way of doing things recently: [ReasonML](http://reasonml.github.io), OCaml ([Flow](https://flow.org), [Pfff](https://github.com/facebook/pfff/)), [Haskell](https://www.youtube.com/watch?v=sl2zo7tzrO8). I hope it will help attracting more developers towards functional pratices.

## [Ruby Conf 12 - Y Not- Adventures in Functional Programming by Jim Weirich](https://www.youtube.com/watch?v=FITJMJjASUs)

This one is just insane, Jim Weirich exploring the manipulation of higher order functions and functional refactorings in Ruby, on a basic example. I'm not sure if it's really an informative talk or just a nice standup comedy, but for sure it is a lot of fun.

## [Jim Weirich on Decoupling from Rails](https://www.youtube.com/watch?v=tg5RFeSfBM4)

Jim Weirich shows paths to decouple domain code from a Ruby on Rails application. Nothing really new here, basically repositories + services, but it can be enlighting for regular Rails developers who may have forgotten how much Rails tends to leak into our domain code and how much it can be annoying.

Jim chooses to replace the service pattern with what he calls a `Runner`, which is basically a wrapper around a use case. This pattern is sometimes called _functional object_, with the `run` method renamed to `call` so we can call the object in a more functional way by using the `.()` ruby syntactic sugar. Concerning the decoupling from the DB, he chooses to use a proxy business object which delegates plumbing back to the `ActiveRecord` object, and a repository for object creation and retrieve.

[Full Stack Fest 2015: Blending Functional and OO Programming in Ruby, by Piotr Solnica](https://www.youtube.com/watch?v=rMxurF4oqsc) is a great companion talk to Jim's one, exploring ways to write Ruby code in a little more functional way.
