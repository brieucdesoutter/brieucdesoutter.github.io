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

This one is only relevent to statically typed language where the type of every expression must be known at 
compile time. 

In language like Java, C++ 03 and before, it is the programmer responsability to specify type information when
declaring variable and functions. However the compiler is usually capable of figuring out the type of declarations
in most cases.

Type inference leverages that knowledge and let the compiler works for the developer.

For example, say you have a C++ utility function that counts words in strings defined as follow:

{% highlight cpp %}
extern map<string, int> count_words(vector<string> input);
{% endhighlight %}

When you use it, you have to remember that it returns a ```map<string, int>```
and not a ```vector<int>``` and type the right type!

With type inference, all you have to do instead is:

{% highlight cpp %}
auto result = count_words(lines);
{% endhighlight %} 

The simple use of ```auto``` is enough to tell the compiler "figure the type of the result from the context".

So type inference is kind of type saving utility (pun intended).

Sometime however, it is nice to know what you're dealing with: say you're working with a new library or piece 
of code, and you call a method from that library, you can assign the result to an auto-declared variable but
it doesn't tell you a lot about what you can do whith it...

However the compiler knowledge about types of the program objects allows to build powerful tool like auto-completion.

The previous example is using C++ 11 but other languages have that too.

Swift uses ```var``` for mutable variables and ```let``` for immutable variables and Kotlin uses ```var``` and ```val```.

In dynamically typed programming languages like python, ruby and javascript to name a few, 
even though every epxression has a type, it is not determined/checked until runtime by the interpreter/JIT 
so there is not need for the programmer to add that information in his source code. 
The drawback is that it becomes quickly impossible for autocompletion tools to provide meaningful suggestions and 
the Python developpers have designed a system of type annotations that can be leveraged by IDE to perform some type-checking 
usually performed by a compiler in statically typed language. 

