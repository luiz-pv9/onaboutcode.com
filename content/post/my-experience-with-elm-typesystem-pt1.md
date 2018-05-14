---
title: "My Experience With Elm's Typesystem (Pt. 1)"
date: 2018-05-14T08:56:20-03:00
description: "I’ve been working with dynamically typed languages such as Ruby and PHP for the past 6 years. For me, the type system was the most difficult thing to get used to while learning Elm - so hopefully I can help others avoid the same problems I had."
---

I've been working with dynamically typed languages such as Ruby and PHP for the past 6 years. For me, the type system was the most difficult
thing to get used to while learning Elm - so hopefully I can help others avoid the same problems I had.

Let's say we need to store a list of functions and some default arguments. In Javascript, I would have no problem with the following code:

```javascript
let callbacks = [
  { callback: callback1, args: listOfArgs1 },
  { callback: callback2, args: listOfArgs2 },
];

callbacks.map({callback, args} => callback.apply(null, args));
```

In Elm, however, it isn't as straight forward as Javascript - though it has its benefits. We need to think a little bit more about code design and the purpose of a "list of callbacks". As most statically typed languages, all elements of a list must be of the same type. Let's see how we can achieve a similar design in Elm.

> A list of callbacks is a simplified version of the problem I encountered while developing a [chat bot](https://github.com/luiz-pv9/elm-chat-bot-example). In order to send HTTP requests, the bot needs a `decoder` (that translates a JSON response into an Elm's value) and a `formatter` (that transforms the Elm's value into a Bot message).

```elm
type alias Callback =
    { callback : String -> String
    , args : String
    }


callback1 =
    { callback = \str -> "Hello, " ++ str
    , args = "world"
    }


callback2 =
    { callback = \str -> "Hey there, " ++ str
    , args = "Jane"
    }


callbacks =
    [ callback1, callback2 ]
```

Well, that works. But we don't want a callback that can only handle strings. Or do we? Let's say we don't,
and with a small tweak we can define our callback with a generic value `a`:

```elm
type alias Callback a =
    { callback : a -> String
    , args : a
    }
```

Everything still works, but the code is more interesting now. Our callback can hold any value as long as it is the same type in the the `callback` and `args`.

> Google tip: this is called a *generic data structure*.

We can now define callbacks that handles arguments of different types:

```elm
callback1 : Callback Int
callback1 =
    { callback = \num -> toString (num + 10)
    , args = 5
    }


callback2 : Callback String
callback2 =
    { callback = \word -> "Hello, " ++ word
    , args = "world"
    }
```

That's great so far - but now we introduced a problem to our list of callbacks:

```elm
-- Doesn't work anymore
callbacks = [callback1, callback2]

The 1st and 2nd entries in this list are different types of values.

22|             [callback1, callback2]
                            ^^^^^^^^^
The 1st entry has this type:

    Callback Int

But the 2nd is:

    Callback String
```

Elm isn't very happy with our list and the compiler explained really well why. Even though `Callback` is defined in terms of a generic value, each callback is implemented with a concrete value: `String` and `Int`. `Callback Int` is not the same as `Callback String`. We must reach for a union type to be able to store those callbacks in a list.

Union types are **one of** their constructors. In the example below, an operation can be either a sum or a subtraction, and a user can be either anonymous or named:

```elm
-- Constructors Sum and Subtraction with no parameters
type Operations = Sum | Subtraction

-- The Named constructor has a String parameter
type User = Anonymous | Named String
```

We can take advantage of union types to describe a `Callback` type that can be either a string callback or an integer callback. Here is the complete code:

```elm
-- Our union type can handle either a Callback Int 
-- or a Callback String
type CallbackDef
    = CallbackInt (Callback Int)
    | CallbackString (Callback String)


type alias Callback a =
    { callback : a -> String
    , args : a
    }


callback1 : Callback Int
callback1 =
    { callback = \num -> toString (num + 10)
    , args = 5
    }


callback2 : Callback String
callback2 =
    { callback = \word -> "Hello, " ++ word
    , args = "world"
    }


callbacks : List CallbackDef
callbacks =
    [ CallbackInt callback1, CallbackString callback2 ]


results : List String
results =
    List.map
        (\callbackDef ->
            case callbackDef of
                CallbackInt callback ->
                    callback.callback callback.args

                CallbackString callback ->
                    callback.callback callback.args
        )
        callbacks
```

As you can see, we need a `case of` expression to get the callback record out of the `CallbackDef`. By the way, `CallbackDef` is not a good name, I just used it to illustrate the difference between the callback product type (record) and the union type.

Once we pattern match the value with `case of`, Elm knows that the value has to be a string callback or an integer callback or any value in the union type.

Thanks for your time, I hope you have a great day!
