title: 'Readings: Clean Code by Uncle Bob'
tags:
  - Reading
  - review
categories:
  - self improvement
date: 2015-12-29 18:46:20
---

One of my recent readings was _Clean Code_ by _Robert C. Martin_. Thorough book with lots of examples on it. Firstly, the author describes the principles, patterns and practices of writing clean code. Then introduces several case studies of code cleanups with varying complexity. And at the end, introduces a list of "code smells" and heuristics.

What I really liked about this book is how the author shows the whole process of refactoring in detail, step by step. I used to think that such _rock star_ programmers simply have this incredible brain capacity to tackle down big problems and refactor stuff in one go. Reading the book helped me understand that this is not the way to go. Simply by doing lots of small refactorings helps you isolate one problem at a time and work on it effectively, quickly moving on to another. In the end, you have more features and cleaner code. Not surprisingly, the tests plays a big part in such refactoring cycle. 

<!--more-->

The other thing I liked about the book is the list of smells and heuristics. I have picked just a few which I stumble upon the most, or want to avoid more, or address more in my day to day work:
 - **Build and tests requires more than one step**
This is pretty important. Especially because build will probably have some options as well, which should be _well documented_. Creating a build script pays off, even if your build consists of `npm install` and `gulp`. This will change eventually and you will be sorry once you have to change these lines in CD tool or elsewhere. Same thing applies for running the tests
 - **Functions with too many arguments**
This happens way less frequently for me than before. However, still does. Best count for arguments is 1-3. Less is better.
 - **Functions with flag/selector arguments**
`saveEntity(true)` requires you to look at the function and understand how it works. And it could be fixed by creating 2 functions out of one.
 - **Obvious behaviour is not implemented**
One of the least things I stumble upon, however, one of the most annoying things.
 - **Incorrect behaviour at the boundaries**
This isn't too rare in my case. The best way to deal with this is writing tests for the boundaries, no matter how trivial the behaviour seems to be.
 - **Overridden Safeties**
In other words, turning off or ignoring warnings. Rarely happens for me I suppose, though is usually followed by a task to clean it up after the fire is put out.
 - **Duplication**
Strangely enough, this happens more than I would like to. Often duplications creeps in due to possibility of different needs in funcionality at first glance. Then you end up refactoring a bunch of components.
 - **Inconsistency**
Happens sometimes with duplication. New components have less duplication, while old ones have not been refactored yet.
Applies to more areas, however, most frequently is the one of least impact -- formatting, mixed tabs and spaces in particular.
 - **Feature envy**
Having to complete calculations of one object on a different class. Sometimes it's a necessary evil, though should be avoided if possible. Worst part, is that people end up not noticing feature envy.
 - **Function names should say what they do and do one thing only**
Having short names for functions are great - less writing. Writing function names based on what they do is a great way to check whether your functions have side effects and forces you to at least think about splitting the function in such cases. Also you end up with shorter functions and cleaner code. One of the most important heuristics for me because of its simplicity and the impact it has.
 - **Prefer polymorphism to if/else or switch/case**
The author uses ONE SWITCH rule: _There may be no more than once switch statement for a given type of selection. The cases in that switch statement must create polymorhic objects that take the place of other such switch statements in the rest of the system_.
 - **Replace magic numbers with named constants**
One of the most valuable things you can do for your future self and others.
 - **Encapsulate conditionals**
Encapsulating multiple ifs to a method cleans up the code and explicitly tells you what is being checked.
 - **Encapsulate boundary conditions**
These are hard to keep track of. Explanatory variable would help to explain the boundary.
 - **Keep configurable data at High levels**
Or in a separate config file if possible.
 - **Choose descriptive names and use explanatory variables**
I try to do this as much as I can. And look suspiciously at the code which, for example, has a variable called `c`, just to be sure that it is obvious. Having explanatory variables helps a lot if you end up debugging the code.
 - **Do not skip trivial tests**
 - **Insufficient tests**
I would like to address more both of the above, especially since I am relatively new to TDD concept and principles.

### Summary ###
I believe that the book is a must read for all developers, just like _Code Complete_. It might and probably will teach you a thing or two.
