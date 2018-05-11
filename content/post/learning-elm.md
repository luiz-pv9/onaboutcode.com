+++
date = "2018-05-04T10:00:00-03:00"
title = "Learning elm"
Description = "It's really fun"
Categories = []
Tags = []
+++

## Learning Elm

I first tried to learn Elm in 2016. It was *very* different from everything else I’ve worked with before - and this is what motivated me the most. I like learning new things and I enjoy the feeling from the “AHA” moments. But as you noticed I said “tried to learn”. I gave up about two weeks later after watching talks on youtube, reading articles and following the official guide. I just couldn’t make the jump from tutorials to building something on my own.

Elm’s programming paradigm is radically different from what I was used too. It has static types, all data structures are immutable and functions are pure. It was just too much stuff for me to learn at once, a person coming mainly from Ruby, PHP and Javascript.

During this time, I followed Evan Czaplick (the creator of Elm) and Richard Feldman (great talks about Elm and programming in general) on twitter, which meant Elm was always in sight. From time to time, I came across something about Elm, sometimes a presentation in a conference, sometimes a blog post.

Two years passed and I decided to try Elm again in a small project - and it was *so much* easier.

If you want to see the project running, click here.

So… what changed in those two years? Well, the language and architecture stayed pretty much the same, so the only reasonable answer is that **I** changed. In those two years, I realized was learning and getting used to functional programming slowly, concept by concept, without any pressure or specific goal. I believe is due the fact that a lot of mainstream libraries and frameworks (hat-tip to the React ecosystem overall) has bought a lot attention to those concepts: immutability with transformation instead of mutation and side-effect-free functions (or at least making the effects go through the same reducer). Even things like Laravel’s Collection class provides functions like `map`, `filter` and `reduce`. I was getting used to some functional programming concepts without even noticing.

In Elm, the only thing that was new, but not so foreign anymore, was the type system. The only language with static types that I have experience with was C. In C, types are mostly about memory layout and optimization, while in Elm it feels like the type system is about design. The type definition feels almost like a spec test of the code you’re about to write.

I’ve never programmed in Haskell or OCaml or any other ML-family language, so I can’t say anything about their type systems. I’ve read their type system are more sophisticated than Elm’s, though I’m not sure what it means exactly.

I’ll write another post about my experience with Elm’s type system overall, but for now I’ll say the project I wrote was big enough for me to appreciate the ease of refactoring and the strong confidence it gave me the app was still working after the changes. As Richard said in one of his talks, once it compiles again it usually works.

If you haven’t tried Elm yet, give it a go. Read some example code, watch some talks, try to make some changes. It’ll may be a rough experience, but that’s not a problem, maybe you need to take some time as I did. Wait a couple months, maybe a whole year. It’s always nice to revisit subjects and see how much *we* have changed. Joshua Foer said in his book Moonwalking with Einstein that the more we know the easier it gets to learn new things. It may sound weird, but a lot of the learning process is relating new stuff to the stuff are already know. We always try place new concepts in the context of the things we already know, so if we keep trying to learn Elm (or any new concept, really) it’ll get easier *to learn* if you keep revisiting it from time to time.

I hope you have a great day!



