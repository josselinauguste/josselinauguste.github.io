---
layout: post
title: "Interesting Stuff #4"
date: 2018-02-22T14:16:43+01:00
---

## [Haskell at Work - Haskell Programming Screencasts](https://haskell-at-work.com)

A new haskell screencast serie, composed of (currently) short weekly episodes -- quite interesting and well produced.

## [The Death of Microservice Madness in 2018 - dwmkerr](http://www.dwmkerr.com/the-death-of-microservice-madness-in-2018/)

Why isn't it a good idea to migrate an architecture to microservices to follow a trend, instead of doing so facing a real technical problem? What are the potential drawbacks?

Another perspective on this question by [Simon Brown](https://twitter.com/simonbrown):
<blockquote class="twitter-tweet" data-lang="fr"><p lang="en" dir="ltr">The monolith vs microservices debate is multi-faceted … this doesn’t capture everything, but here’s one way to look at it. <a href="https://t.co/7V5VFY0RbY">pic.twitter.com/7V5VFY0RbY</a></p>&mdash; Simon Brown (@simonbrown) <a href="https://twitter.com/simonbrown/status/847339104874381312?ref_src=twsrc%5Etfw">30 mars 2017</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## [Anatomy of a Haskell-based Application - Arnaud Bailly](http://abailly.github.io/posts/cm-arch-design.html)

This title can a little bit misleading. Ok, the article is mostly a feeback about the development from scratch of a business application in Haskell, but the subject covered is broader than that. There is a little bit of Haskell in here, and a paragraph or two about the choice of Haskell, but the main part of the content is more about designing an application using a functional paradigm and event sourcing, and this part is really interesting.

The fact that it is about a young application built to answer a business problem adds an interesting dimension to this story: the article describes the shortcuts and technical simplifications took from the canonical event sourced application, certainly to focus on the business side of things first. And it is quite refereshing to read someone telling us that our shiny event sourced application does not necessarily need an event bus from the first stage, or that we can just use a flat file for event storage, or we can avoid persisting the state in database, and just rebuild it from scratch at startup. Of course these choices have drawbacks, but they still can be fixed later **if necessary**, if the fundation of the application is well designed.

A follow-up to this article have been written 2 years later: [Anatomy of a Haskell-based Application, Revisited](https://tech-blog.capital-match.com/posts/3-anatomy-of-haskell-web-app.html).
