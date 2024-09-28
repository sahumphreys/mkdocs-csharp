---
title: Extended Theory - Computational Thinking
---

# {{ title }}

At its heart computer science is about __problem-solving__, particularly solving problems using a computer and for programming actually writing the code that enables the problem to be solved.  It's a two-step process:

- Think about the steps needed to solve the problem, the __algorithm__, and then
- Write program statements to implement those steps, the __code__

To do this effectively we need, in some part, to think like a computer.  Of course, a computer cannot think (!) but it means we need to understand the processes and approaches taken by the computer in order to write our algorithm appropriately, or __computational thinking__.  It's a term coined by Jeannette Wing:

> Computational thinking is the thought processes involved in formulating problems and their solutions so ... [they] ... can be represented in a form that can be carried out by an information processing agent.  (Wing, 2010)

There are several processes involved here:

- __logical reasoning__: to predict, analyse and explain
- __algorithms__: the steps required to solve the problem
- __decomposition__: breaking the problem down into smaller problems
- __abstraction__: manage the complexity of the problem
- __generalisation__: being able to spot patterns and similarities for re-use
- __evaluation__: making judgements on the outcome

Much of the text thus far has been using the first two of these to construct algorithmic solutions to smaller problems using C\#.  Chapter 9 introduced the third, decomposition and we'll explore more of what that means as well as abstraction and generalisation here.

### Decomposition

Decomposition is not unique to programming or computer science, we do this every day in the real world.   Delivering a course such as this on programming in C\# involves breaking the language down into smaller chunks, working on those before advancing to the next.  The computer you use will be built from many different components, each manufactured separately before being combined into a computer hardware system.  Cooking a meal involves decomposition of selecting the menu, purchasing the ingredients, preparing and cooking those ingredients, perhaps combining the results from previous preparations and so on.  Each of these tasks could be passed to another person to complete, perhaps independently of any other tasks.

In the previous chapter we started to pass responsibility for completing parts of our program to smaller sections of code.  It makes the process of managing a larger problem much easier and in the "real world" we could work as a team with different teams taking responsibility for coding these sub-problems before they get combined into the larger problem.  These smaller problems, of course, may not be quite so small and will required further breaking down into a series of sub-sub-problems and so on.

It's important, as you plan your solutions to look for those opportunities to break the problem down.  Once you have the sub-problems solved you can combine them to produce the solution to the larger problem i.e. __composition__.

### Abstraction

The concept of __abstraction__ lies at the heart of __computational thinking__ allowing us to manage complexity - focusing on what is important and ignoring unnecessary detail thus making the problem easier to think about.  We've seen this at work already e.g. we use binary numbers ($0$s and $1$s) to represent physical voltages in a computer, the detail of how the semiconductors etc are handling these voltages is abstracted away to a $0$ or a $1$, it's hiding the underlying reality.  The underground map of London is another example of abstraction as it shows the various underground trains lines in London and the relative position of the stations on those lines.  It does not show the distance between the stations, nor how far underground each station is.  It's a __representational abstraction__ of the reality.

When designing a system for the computer we need to consider what details are required, and what details can be ignored.  In a system keeping track of students in a school or college there are details we need such as their first name, last name, postcode etc but details such as, say, their show size or favourite music style are irrelevant.  We may think differently if we were designing a system for an on-line shoe retailer or a streaming music service.  We need the right amount of detail to solve the given problem in hand - no more.

### Abstraction by generalisation

A generalisation is a form of abstraction, this involves a grouping of characteristics common to a particular type.  Thinking again of a system to handle data in a school system we're going to need data about pupils and staff (including teaching and non-teaching staff).  In this context the pupils and staff members are all people sharing common characteristics such as name, address, date of birth etc..  We can generalise these shared details into a new data type:  Person.  A "Person" is a more generalised type, a "Student" or "StaffMember" is a special kind of Person in this context.  One could further categorise "teaching staff" and "non-teaching staff" and make these specialised kinds of "StaffMember".

Problems themselves can also be categorised e.g. decision problems, search problems, counting problems, optimisation problems and tractable or intractable problems.  Each type of problem will exhibit shared characteristics and apply similar principles in developing their solution or even sharing code between them.  It's an important skill to be able to abstract away some of the details of a particular problem until we can arrive at a generalisation.  We can refer to this technique as __problem abstraction__.

### Information hiding

This refers to keeping implementation details hidden from a user.  For example, in card playing program we'd expect a method to `Shuffle()` the cards.  There are different ways of implementing the algorithm to produce a randomised sequence of cards ready for use in a card game.  We might have a method signature for this such as `public DeckOfCards Shuffle(DeckOfCards deck)`.  As developers all we need to know is the existence of this `Shuffle()` method and know that we need pass in a deck of cards to the method and expect to receive back the shuffled deck of cards.  The author of this method can make changes to the shuffling algorithm used at a later stage but our program can call the method ignorant of the implementation details, as long as the __interface__, that is the method signature, to that method remains the same.

We call this __method signature__ an __interface__, it's an abstraction of the complexity that lies behind that interface.  We're familiar with the term is e.g. __user interface__, an essential feature of an operating system that itself provides many examples of abstraction.  Think of the menus, icons etc, the folders and files made visible through the interface hiding the complexity of how those directories and files are physically stored.

We can also describe this hiding of implementation details as __functional abstraction__, the method is a _black box_.  Pass data in and data will be returned and we do not care how that returned data has been computed.

### Procedural abstraction

__Procedural abstraction__ represents a method.  The goal is to make the procedure as generalised as possible so it can be used for different problems.  We can think of this in two ways.  Take the example of calculating the area of a rectangle with sides of 4cm and 3cm, which we could call this method `CalculateAreaOfSquare();`:

```cs
public void CalculateAreaOfSquare()
{
    int area;
    int side1 = 4;
    int side2 = 3;
    area = side1 * side2;
    ConsoleWriteLine(area);
}
```

It should be clear that this is not an ideal way to proceed!  It would be much more useful to be able to calculate the area of a rectangle of _any_ size by passing in the sides as parameters:

```cs
public void CalculateAreaOfSquare(int side1, int side2)
{
    int area;
    area = side1 * side2;
    Console.WriteLine(area);
}
```

There's still an issue that this method will only handle rectangles with whole number sides.  Not an enormous problem as we could require the sides are converted into millimetres before calling the function.  However, there is a further issue that is problematic, but may not be immediately obvious.

The method calculates the area of a square.  That is _all_ it should do is do the calculations and return that value, but we're also displaying the result to the screen.  These should be regarded as two separate methods, `CalculateArea()` and `PrintArea()`.  The displaying to the screen statement in the original method is known as a __side-effect__, these should be avoided when writing methods.  Once we've removed the side-effect the method can be used in a console application, a web application, an application using a graphical user interface and so on.  This is known as __separation of concerns__, the method should be responsible for one thing either calculating the area or printing the output but not both.

The change needed is to make this method return the value of the `area` to the calling program:

```cs
public int CalculateAreaOfSquare(int side1, int side2)
{
    return side1 * side2;
}
```

Procedural abstraction involves making the procedure as generalised as possible.

### Data abstraction

Thinking back to the `Shuffle()` example.  This needed a `DeckOfCards` to be passed in and a deck of cards returned.  That data type could be defined as a `struct` or an an `object`.  Internally, this deck of cards will be made up of $52$ playing cards, another user-defined data type, `card`, that could be a `struct` or an `object` with variables for its rank and suit, but how will this deck of cards be organised?  It could be an array, a list, a stack, a queue or other structure we can use to organise data.

When we call the `Shuffle()` method we pass the Deck data type.  It's hidden from us, as we call the method, how the Deck has been implemented.  Is it an `array` of cards?  Perhaps it's a `list`?  Either the array or the list could be organised as a `stack`, or a `queue`.  The point is the details of how the data is being organised has been hidden.

Further, how that data structure itself has been implemented is also hidden.  If it's a `stack` of cards we'd expect to find methods to manipulate the stack, such as `Push()` to add an item to the top of the stack, and `Pop()` to remove the item at the top of the stack.  Again, how these methods have been implemented are not revealed unless we inspect the code at the lowest level.