---
title: Declaring, Creating, and Initializing a String in C#
---

# {{ title }}

## Declaring a String Variable

To declare a string variable in C#, use the following syntax:

```csharp
string myString;
```

- This tells the compiler that `myString` is a string variable.
- At this point, `myString` is uninitialized and has a default value of `null`.

!!! note
    - A variable with a `null` value means it is not pointing to any object in memory. Trying to use `myString` without assigning a value will result in a runtime error.

## Understanding Reference Types

Strings, like arrays, are __reference types__. This means:

- **Stack vs. Heap Memory:**
    - The variable `myString` on the stack holds a reference (memory address) to the actual string object stored on the heap.
    - When you declare a string without assigning a value, the variable exists but does not reference any object in memory.

## Instantiating and Initializing a String

Before using a string, you must initialize it by assigning a value:

```cs
myString = "Hello, World!";
string name = "";
```

- The string literal `"Hello, World!"` is created in the heap, and `myString` holds a reference to this location.
- `name` is initialized as an empty string (`""`).

!!! warning
    - Declaring a string variable without assigning a value and then trying to use it will result in a `NullReferenceException`.

## Copying String References

If you assign one string variable to another, you're copying the reference, not the value:

```csharp
string myNewString = myString;
```

- This means `myNewString` now points to the same memory location as `myString`.
- Any changes to the string object will be reflected in both variables.

!!! note 
    - Even though strings are reference types, they are __immutable__. This means you cannot change the value of an existing string object in memory. Any modification results in a new string object being created.

## String Initialization in One Step

You can declare and initialize a string in a single step:

```cs
string greeting = "Welcome to A Level Computer Science!";
```

## Reading and Printing Strings

We have seen these methods quite a bit in previous sections, but copied here for completeness.

### Reading from the Console

The `ReadLine()` method reads a line of text entered by the user and returns it as a string:

```csharp
Console.Write("Enter your name: ");
string name = Console.ReadLine();
```

- The `ReadLine()` method waits for the user to press Enter and assigns the input to the `name` variable.

### Printing to the Console

The `WriteLine()` method prints a string to the console:

```csharp
Console.WriteLine("Hello, " + name + "!");
```

- This uses __string concatenation__ to combine the greeting and the `name` variable.

### String Interpolation

String interpolation provides a more readable way to include variables in strings:

```csharp
Console.WriteLine($"Hello, {name}!");
```

- The `$` symbol before the string allows you to embed variables directly within the curly braces `{}`.

**Advantages of String Interpolation:**
- More readable and easier to manage, especially with complex strings.
- Avoids the need to use the `+` operator for concatenation.

