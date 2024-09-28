---
title: Lists
---

# {{ title }}

A limitation of arrays is that their size is fixed (**static**)—once declared, the number of elements in an array cannot be changed at runtime. In contrast, a `List` is an **ordered collection** of elements that can grow or shrink as needed, making it **dynamic**.

Like arrays, each element in a `List` must be of the same data type, and you can access elements by their index. However, the flexibility to adjust the number of elements makes `List` a more versatile option in many cases.

## Declaring a List

To use a `List`, you need to include the `System.Collections.Generic` namespace. When declaring a `List`, you must specify the data type of its elements using angle brackets. Here’s an example:

```cs
using System.Collections.Generic; // Remember to include this
...
...
List<int> Marks = new List<int>();  // Initialize a list of integers
Marks.Add(78);                      // Add elements using Add()
Marks.Add(65);
Marks.Add(82);

foreach(int mark in Marks)           // Use foreach to iterate over the list
{                                    // No changes to the list are allowed during foreach
    Console.WriteLine(mark);         // Output each element
}

// or

for (int i = 0; i < Marks.Count; i++)  // Use a for loop to access elements by index
{
    if (Marks[i] > 75)
    {
        Console.WriteLine($"{Marks[i]} = Distinction");
    }
}
```

## Modifying a List

Unlike arrays, a `List` allows elements to be added and removed dynamically. You can remove elements either by value or by their index:

```cs
Marks.Remove(65);   // Removes the first occurrence of 65
Marks.RemoveAt(0);  // Removes the element at index 0
```

## Checking if a List Contains an Element

You can check if a list contains a specific element using the `Contains()` method:

```cs
if (Marks.Contains(54))  // Checks if 54 is in the list
{
    // Do something
}
```

To avoid duplicates, you can use this method before adding new elements:

```cs
if (!Marks.Contains(54))
{
    Marks.Add(54);
}
```

## Other Useful Methods

Here are some other common methods for working with lists:

- `Insert(index, value)` - Insert an element at a specific position.
- `Clear()` - Remove all elements from the list.
- `IndexOf(value)` - Find the index of the first occurrence of an element.

```cs
Marks.Insert(1, 90); // Inserts 90 at index 1
int index = Marks.IndexOf(82); // Gets the index of 82
Marks.Clear(); // Removes all elements from the list
```

## Differences Between Arrays and Lists

- **Static vs Dynamic**: Arrays have a fixed size, while lists can grow or shrink.
- **Length vs Count**: Use `.Length` for arrays and `.Count` for lists to get the number of elements.
- **Indexing**: Both arrays and lists are **zero-indexed**, meaning the first element is at index 0.

## Efficiency Consideration

While lists are flexible, some operations (like removing elements from the middle) can be less efficient than arrays because elements need to be shifted to fill gaps.

## Summary

`List` in C# offers a flexible, dynamic alternative to arrays, allowing you to modify the size of the collection at runtime. With methods like `Add()`, `Remove()`, and `Contains()`, lists are easy to work with and are suitable for situations where the number of elements is not known in advance or can change during program execution.
