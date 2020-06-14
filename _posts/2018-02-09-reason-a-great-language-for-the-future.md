---
layout: post
title: "Reason: a great language for the future"
date: 2018-02-09T22:15:50+01:00
---

[Reason](https://reasonml.github.io) (a.k.a ReasonML) is an almost new programming language developed by Facebook, compiling to Javascript. Thanks to the [ReasonReact](https://reasonml.github.io/reason-react/) library, its aim is obviously to become the next de facto choice for building React applications (and indeed, it makes great sense).

The language is based on OCaml, and so benefits from all the nice OCaml features: static typing, great module system, immutability by default, nice compact syntax. This ancestry reinforces Reason strengths for React development, which perfectly fits with functional paradigms.

After only a few weeks of use, here are a few noticeable points about Reason I noticed:

## The Good

- Reason integrates seamlessly with React! JSX support is built in the language, and the ReasonReact library is quite good -- I may even say that it has some advantages over ReactJS for the beginner, as it comes with some opiniated choices in the same way Elm does, which is great for productivity and learning curve;
- Reason documentation is quite nice, even if not always as detailed as we may expect. But at least it exists and it is easy to find -- right on the official Reason website --, making it an obvious way to learn the language (and for more advanced topics, [Axel Rauschmayer](http://2ality.com) is often a great source of information);
- `refmt` is great (allowing to concentrate on stuff that matter, not on silly formatting questions);
- Its (static) type system, and particularly the module system, are awesome! Not overly complex, but still powerful enough to make the compiler our best friend for bug hunting;
- Facebook seems to be highly supportive towards the language -- more than Microsoft has ever been towards F# for example.

## The Bad

- Error messages can sometimes be cryptic and hard to read, which does not help while trying to understand an error and find its location (particularly those `<UNKNOWN SYNTAX ERROR>` messages);
- The syntax is better than the OCaml one, but I am not sure that the decision to borrow some JS idiomatic constructions (`()`, `{}` and `;`) was the best one to make, because it adds a lot of unnecessary verbosity. The F# syntax is in my opinion way clearer;
- Some OCaml oldies are still hidden here and there, like the necessity to have different operators depending on the type (`++` for *string*, `+` for *int* and `+.` for *float*), or the non-by-default support of UTF-8 strings;
- The standard library is kinda anemic, but [its gonna change soon](https://github.com/BuckleScript/bucklescript/issues/2463). The OCaml library is still there, but its documentation is not always the easiest to read;
- Editor plugins are still a little bit raw, but they will certainly improve as the community will grow;
- For a reason I ignore, there is no implicit interop with Js types (it is necessary to use `Js.Boolean.to_js_boolean` and `Js.true_` to manipulate boolean for example);
- This kind of stuff: `ReactDOMRe.domElementToObj(ReactEventRe.Form.target(event))##value`, especially for DOM event manipulation, is kind of painful;
- Parsing methods ala `int_of_string` rely on exceptions, whose handling cannot be enforced by the compiler :/ Using an `Either` type would allows to write a more robust code thanks to the awesome help provided by the compiler.

As a conclusion, Reason does not yet feel as consistent as Elm or F#, but the community is growing more than ever, so I am confident that the ecosystem and the tooling will improve drastically in 2018. In fact, I am even pretty confident that 2018 will be a turning point for Reason popularity, seeing more and more people embracing the language -- thanks to its maturity --, and talking about it in public.