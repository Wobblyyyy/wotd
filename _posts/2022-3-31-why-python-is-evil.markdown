---
layout: post
title:  "Why Python is the root of all evil"
date:   2022-3-31 9:58:23 -0500
categories: python
---
Python is a high-level scripting language that first popped up in early 1991.
Designed by Guido van Rossum and maintained by the Python Software Foundation,
Python has exploded in popularity, due in part to its simple syntax,
ease-of-use, widespread availability, and high-level abstractions, making it
easy to write complex programs. Popular in fields like machine learning,
artificial intelligence, and computer vision, Python's high-level nature makes
it the de-facto language of anything involving a lot of data.

* TOC
{:toc}

# What Python is good at
A lot of things, actually. As much as I hate to admit it, Python is a popular
language for a reason. It's easy for inexperienced programmers to pick up, and
it's a great "first language." It has an intuitive syntax that abstracts away
many of the complexities of lower-level programming languages: memory
management and data structures, to name a few examples.

## It's popular. Extremely popular.
Google pushed Python very hard in during the first decade of the 2000s. Why?
Who the hell knows. But that contributed to its popularity. It's ease-of-use
and very gentle learning curve made it a popular choice for new programmers,
and it's now one of the most commonly-taught languages in the world. Its usages
have expanded to AI, ML, and even... back-end web development?

## It's easy to use. Really ease to use.
Python is probably among the most simple programming languages, and that's why
it's such a common choice for new developers without any programming experience
under their belt. They can pick it up quickly. The quicker they pick up the
principles of coding, the quicker they can actually start coding.

## Requires very little boilerplate
Python is a very high-level interpreted language. It's easy to do things that
would require much more code. As a particularly egregious example, let's
compare a bit of Java code to a bit of Python code. We'll create a map (or, as
it's called in the Python world, a dictionary) that will correlate the names of
some certain people to their number.

Here's what that looks like in Java.

{% highlight java %}
import java.util.Map;
import java.util.HashMap;

public class Example {
    private Map\<String, Integer\> map = new HashMap\<\>() {{
        put("John", 8);
        put("Linda", 2);
        put("Mike", 5);
    }};
}
{% endhighlight %}

And here's what that looks like in Python.

{% highlight python %}
map = {
    "John": 8,
    "Linda": 2,
    "Mike": 5
}
{% endhighlight %}

As much as I hate to admit it, Python requires you to write less code. _A lot_
less code, in fact.

# Why Python is evil
Allow me to preface this by saying that the title of this section (and this
blog post) is (are) a bit hyperbolic in nature. Python isn't genuinely evil,
but I do believe that it's being overused, and I do believe that learning
Python first produces a syndrome best named "Python brain."

## It's slow
This is one of the most common critiques of Python, and for good reason.
Python, as a high-level language, is pretty slow. Scripting languages are
inherently slower than compiled languages. There are a couple of issues with
how Python is designed that further complicate these speed issues.

### Global interpreter lock
Python's "global interpreter lock" prevents multi-threading entirely. The idea
is that all components of a Python application must be executed on a single
thread. Certain libraries can circumvent this by using languages such as C to
handle multi-threading. But Python does not natively support the usage of
multiple threads. This proves to be a huge drawback when attempting to develop
applications that would need to utilize multiple threads in order to optimize
performance.

[Real Python][global-interpreter-lock] explains why the global
interpreter lock ("GIL") exists: in short, Python uses reference counting for
memory management. Using multiple threads complicates reference counting, so
the GIL exists as a workaround to that issue. If you're curious, you can go
ahead and read a bit more on [Real Python][global-interpreter-lock].

### Dynamic typing
This is more of an issue with scripting languages in general rather than just
Python, but it's certainly a component of what makes Python so slow.

## It's... too easy?
Alright. Allow me to explain myself here. Python is an incredibly easy language
to learn - in fact, it's consistently ranked as one of the
[easiest languages to learn][easiest-langs-to-learn] - and for good reason.
However, I feel Python's gentle learning curve might hurt inexperienced
developers down the line. As a harsh example, learning Assembly requires you to
know how your computer is working on a very low level. Python doesn't do the
same - you don't worry about what a register is, what a stack is, what a heap
is, how memory is managed, etc. This concept is known as abstraction - Python
features many more abstractions designed to simplify the developer experience
when compared with lower-level languages, such as C, Java, or even x86 NASM.

I'm not saying you should learn C prior to Python or you'll never truly learn
how to code. However, what I am saying is this: if you become reliant on
Python's high level of abstraction, you'll have a difficult time mastering some
of the most important concepts of low-level programming. I'm fairly convinced
most Python developers would burst into flames if they were tasked with
creating a hash map, hash table, or hash set from scratch. Obviously, being
able to create hash map doesn't dictate whether or not you can code.

## It has a very forgiving syntax
Have you ever used Scratch? The block-based programming language? If not, I'll
give you a quick run-down: you use a graphical user interface to code, by
connecting bits of block code together. Scratch is incredibly easy to learn
because it's so intuitive, but it's limited. Firstly, it's very slow. Secondly,
block code doesn't allow you to be as specific as you may need to be. Although
you could whip up a simple 2d game in Scratch far faster than you could whip up
a 2d game in C++, you won't be able to customize the behavior of the Scratch
game anywhere near as much as the C++ game.

Writing a game in C++ is extremely challenging and requires you to write a lot
of code. That's because C++ is a relatively low-level language: you have near
complete control over the inner workings of your program. In other words, C++
could be said to be more "specific" than Scratch. This comparison is not unique
to Scratch and C++: introducing any abstractions inherently reduces the level
of control you have over your program.

So what's wrong with Python's syntax?
- No semicolons
- Dependent on whitespace
- Uses colons to indicate blocks
- No curly braces
- Limited parentheses
- Built-in global functions
- Dynamic typing
- No variable declaration keyword
- The "self" keyword

I'll cover a couple of the more important issues with Python's syntax in more
depth in just a moment.

### No semicolons/dependent on whitespace/no curly braces
This is terrible for three reasons.
1. You can't see whitespace! Why would you give semantic meaning to something
   that you can't even see!?
2. You have very little control over how your code is formatted. This normally
   isn't much of an issue, as most IDEs will strictly format your code for you
   (which is a good thing, by the way!). But the entire purpose of programming
   is to have as much control as possible over what your code does, how it
   works, how it looks, etc. - with Python, you can't do that.
3. No curly braces means you have a hard time telling when blocks end. If you
   genuinely feel that not having curly braces makes your code cleaner, I'm
   going to assume that you probably haven't written enough code to know
   better yet.
   - Curly braces make automatic indentation easier, meaning you can do less
     typing and rely more on your text editor.
   - Curly braces make it easier to see when a block starts and ends.

### Dynamic typing
This isn't an issue with Python, but rather scripting languages in general. I,
for the most part, try to be very accepting of the opinions of others when it
comes to programming. However, I firmly believe this: if you think dynamic
typing is superior to static typing, _you have not had enough experience with
code to understand why that's wrong_. I could write an entire blog post on why
dynamic typing is detrimental to programming, but I'll spare you for now.

### No variable declaration keyword
This is simply bizarre. Take a look at this Java code.

{% highlight java %}
public class Example {
    private int a = 0;
    private double b = 3.14159;
    private Object c = "Hey! Look! It's a string!";
}
{% endhighlight %}

You can easily tell what's going on there, just by breaking down each of the
statements. Let's take the first of those statements and break it down:
- `private`: the access modifier
- `int`: the type of the data
- `a`: the data's identifier
- `0`: the data's initial value

What about JavaScript, another dynamically-typed scripting language?

{% highlight javascript %}
let a = 0;
let b = 3.14159;
let c = 'Hey! Look! It\'s a string!';
{% endhighlight %}

Alright, not too bad. You can understand what's going on there - it's
declaring variables named `a`, `b`, and `c` and assigning those variables to a
default value. Although there aren't any data types (which would be even more
readable), you can see that the above code is declaring and defining a variable
by saying "hey, here's a variable named a" and "it has 0 as a value."

Now let's take a look at some code that does the same thing in Python. Spoiler
alert: it's not pretty.

{% highlight python %}
a = 0
b = 3.14159
c = 'Hey! Look! It\'s a string!'
{% endhighlight %}

What the hell is going on there? Who knows! There's no variable declaration
keyword, so... what's it doing? Is it creating a variable and assigning it
(yes, in this case, it is). Is it assigning an existing variable? Nope. Is it
declaring a variable and not defining it? Nope.

Not having a variable declaration keyword decreases readability and makes it
much harder to figure out what a program is doing. Normally, if there's a
declaration keyword, you can see when a variable comes into scope and goes out
of scope. With Python, you're left to guess. I can't even begin to fathom what
decision-making process led to a variable declaration keyword being omitted.

This is a quintessential demonstration of Python's ease-of-use being a
double-edged sword. Sure, the Python code is shorter and it's probably easier to
write, but it's MUCH harder to read.

[global-interpreter-lock]: https://realpython.com/python-gil/
[easiest-langs-to-learn]: https://mikkegoes.com/easiest-programming-language/
