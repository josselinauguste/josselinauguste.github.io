---
layout: post
title: "Interesting Stuff #2"
date: 2018-01-18T00:17:10+01:00
---

## [Designing with Capabilities - Scott Wlaschin](https://www.youtube.com/watch?v=fi1FsDW1QeY)

A talk by Scott Wlaschin at DDD Europe, about designing systems by exposing capabilities restricting the consumer (a user or a piece of code) to only be able to consume the features available to him, instead of testing everywhere if the code has the permission to be executed. This looks like REST hypermedia applied to domain modelling, which seems appropriate to increase the affordance of the code we produce and consume.

## [GOTO 2015 • Applying the Saga Pattern • Caitie McCaffrey](https://www.youtube.com/watch?v=xDuwrtwYHu8)

Caitie McCaffrey shares her knowledge about the use of the saga pattern in distributed systems, inspired by her previous experience gained while working on the Halo game at Microsoft.

For further reading, here is the paper introducing the saga pattern: [Sagas by Hector Garcia-Molina, Kenneth Salem](https://www.cs.cornell.edu/andru/cs711/2002fa/reading/sagas.pdf).

## [Ideology, a talk by Gary Bernhardt from Strange Loop 2015](https://www.destroyallsoftware.com/talks/ideology)

Am I a real programmer? Does unit tests used in conjunction with a dynamic language really compensate for the help brought by a static type system? Or in a bigger picture, does our ideologies prevent us from being able to move forward? (And well, it once applied to functional programming and garbage collection too.)

Nice wrap-up about tests vs. type system: types are categories (and the granularity of the category is limited by the type system) while tests are examples.
