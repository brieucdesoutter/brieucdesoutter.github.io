---
layout: post
title: Favorite programming language features
exerpt: My favorites programming languages.
---

I've always been on the lookout for the next cool programming language and it's really difficult for me to
commit on a new one: is it gonna be supported widely ? Am I gonna be able to do this and that without having
to re-invent the wheel ? How hard is it going to be ? Some kind of analysis paralysis that led me to ruby, 
to python (love it), to rust (couldn't do a simple thing, must be too stupid...) to Scala, Swift...
It looks like the grass is always greener somewhere else...

But recently, Google broke the news that Kotlin would be officially supported for Android application development.
And so I recently looked back at it and completed the koans (TODO insert link here)... And I loved it! 

It got me to think about features I like in a programming language and most importantly why they're cool!
So in this post I'll talk about several features I like in programming language and why.

Disclaimer: I'm an average programming dude. You might find my point of view rather limited in some occasion
or I might even totally miss the actual reason why a language feature has been added, please don't hesitate 
to contact me to fix this, I'll update the post if you got a valid point. 

So without further ado, and in no particular order...

## Type inference

"Type inference refers to the automatic deduction of the data type of an expression in a programming language." (source Wikipedia)

Compilers for statically/strongly typed languages do that to various level during compilation depending on their type system.
Some languages/compilers have limited type inference capabilities and thus force you, the developer, to provide the type for every variable and function/method declarations and to initialize variables with an expression whose type is compatible with the declared type.

Newer languages like Swift and Kotlin or revised one like C++ 11 are said to provide "Type Inference" when the developer does not 
have to provide type for most declarations because the compiler will figure it out.

This has the following advantages:
- it saves you a lot of typing (on the keyboard I mean);
- it also saves you from remembering the return type of all the library functions you may use;
- and it allows easier refactoring.

TODO implementation in Swift, Kotlin, C++ 11

In dynamic programming languages like python or javascript, even though every epxression has a type (don't quote me on that...), 
it is not determined/checked by the interpreter until runtime so there is no need for the programmer to add that information
in the source code and type inference as defined above is not required. 

However, without support of tools like code completion, the lack of type information in the source code can sometime be a problem
for the developer. Indeed, while coding, it is necessary to know what you're dealing with and what you can do with variables and
function return values. 

For statically typed languages, tools can use the compiler knowledge about types to provide code completion, and highlight errors
as you type. 
For dynamic language, things are more complicated, and the trend seems to add back type information in the source code: Python
type annotations, Flow or JSDoc comments in Javascript. IDE like PyCharm and IntelliJ provides much better inspection hints and warnings when those annotations/comments are present in the source code.



