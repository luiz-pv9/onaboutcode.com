+++
date = "2018-05-04T10:00:00-03:00"
title = "About learning Elm"
Description = "I first tried to learn Elm in 2016. It was very different from everything else I’ve worked with before - and this is what motivated me the most. I like learning new things and I enjoy the feeling from the “AHA” moments. But as you noticed I said \"tried..."
Categories = []
Tags = []
+++

![Elm code example](/img/elm-code-print.png)

I first tried to learn Elm in 2016. Elm was very different from everything else
I’ve worked with before - and this is what motivated me the most. I like learning new
things and I enjoy the feeling from the *AHA* moments. I was really excited and ready to get
into functional programming, but as you noticed I said “tried to learn”. I gave up about two weeks later after watching talks on youtube, reading articles
and following the official guide. I just couldn’t make the jump from reading tutorials to building 
something on my own.

Elm’s programming paradigm is radically different from what I was used too. It has a static type system, immutable data structures and pure functions with isolated side-effects. It felt like *too much* stuff for me to learn at once, a person with a background mainly in Ruby, PHP and Javascript.

During those two weeks I followed [Evan Czaplicki](https://twitter.com/czaplic) (the creator of Elm) and [Richard Feldman](https://twitter.com/rtfeldman) (great talks about Elm and programming in general) on twitter, which meant Elm was always in my sight. From time to time I came across something about Elm, sometimes a presentation in a conference, sometimes a blog post.

Two years passed and I decided to try Elm again in a small project - and it was *so much* easier.

> The project was a chat bot. If you're interested, the source code and demo is [available here](https://github.com/luiz-pv9/elm-chat-bot-example).

So… what changed in those two years? Well, Elm stayed pretty much the same so the only reasonable conclusion is that **I changed**. In those two years, I realized I was learning and getting used to functional programming slowly, concept by concept, without any pressure or specific goal. I believe this is due the fact that a lot of mainstream libraries and frameworks (specially the React ecosystem overall) has bought a lot attention to those concepts: immutability with transformation instead of mutation and side-effect-free functions (or at least making the effects go through the same reducer). Even things like [Laravel’s Collection](https://laravel.com/docs/5.6/eloquent-collections) class provides functions like `map`, `filter` and `reduce`. I was getting used to some functional programming concepts without even noticing.

In Elm, the only thing that was new, but not so foreign anymore, was the type system. In comparison, the only language with static types that I had experience with was C. In C, types are mostly about memory layout and optimization, while in Elm it felt like it's about design and how different parts of the code fit together, almost like a spec test of the code you’re about to write.

> I’ll write another post about my experience working with languages with static types and dynamic types, but for now I can say the project I wrote was big enough for me to appreciate Elm's type system. The ease of refactoring and the strong confidence it gave me the app was still working after the changes was just awesome. As Richard Feldman said in one of his talks, once it compiles again it usually works.

If you haven’t tried Elm yet, give it a go. Read some example code, watch some talks, try to make something on your own. It might be a rough experience, but that’s not a problem. Maybe you need to take some time as I did, wait a couple months, maybe a whole year. It’s always nice to revisit subjects and see how much **we** have changed. Joshua Foer said in his book Moonwalking with Einstein that the more we know the easier it gets to learn new things. It may sound weird, but a lot of the learning process is relating new stuff to the stuff are already know. We always need to place new concepts in the context of the things we already know, so if we keep trying to learn Elm (or any new concept, really) it’ll get easier **to learn** if we keep revisiting it from time to time.

I hope you have a great day!



