---
title : Jagged Arrays
---

# {{ title }}

In addition to multi-dimensional arrays, C# also supports **jagged arrays**, which are essentially arrays of arrays. Unlike regular multi-dimensional arrays, jagged arrays allow each row to have a different length, providing flexibility for situations where data is not uniformly structured.

## Declaring and Initializing Jagged Arrays

The key difference when declaring jagged arrays is that each dimension is marked with separate square brackets:

```cs
int[][] myJaggedArray;
myJaggedArray = new int[2][];
myJaggedArray[0] = new int[7]; // First row has 7 elements
myJaggedArray[1] = new int[4]; // Second row has 4 elements
```

This can also be done at the point of declaration:

```cs
int[][] myJaggedArray = {
    new int[] { 9, 3, 14 },       // First row has 3 elements
    new int[] { 7, 2, 5, 1, 0, 2} // Second row has 6 elements
};
```

Each "row" in the jagged array is an independent array, and the rows can vary in size, making this structure more flexible than a regular multi-dimensional array.

## When to Use Jagged Arrays?

Jagged arrays are particularly useful when dealing with scenarios where rows contain varying amounts of data. For example:

- **Student Scores**: Each student may have different numbers of test scores.
- **Polygon Vertices**: Different polygons may have varying numbers of vertices.
- **Uneven Data Storage**: When data does not fit neatly into a rectangular structure, such as survey results where respondents answered a different number of questions.

## Example: Traversing a Jagged Array

Here's a practical example to illustrate how to declare, initialize, and iterate over a jagged array:

```cs
using System;

namespace JaggedArrayExample
{
    class Program
    {
        static void Main(string[] args)
        {
            // Declare a jagged array with three rows
            int[][] myJaggedArray = new int[3][];
    
            // Initialize each row with different sizes
            myJaggedArray[0] = new int[] { 1, 2, 3, 4 };
            myJaggedArray[1] = new int[] { 11, 34, 67 };
            myJaggedArray[2] = new int[] { 89, 23 };
    
            // Traverse the jagged array and print its elements
            for (int row = 0; row < myJaggedArray.Length; row++) 
            {
                Console.Write("Row({0}): ", row);

                for (int col = 0; col < myJaggedArray[row].Length; col++) 
                {
                    Console.Write("{0} ", myJaggedArray[row][col]);
                }
                Console.WriteLine(); // New line for each row
            }
        }
    }
}
```

## Using `foreach` for Traversal

A `foreach` loop can make traversal simpler and more readable:

```cs
foreach (int[] row in myJaggedArray)
{
    foreach (int element in row)
    {
        Console.Write(element + " ");
    }
    Console.WriteLine();
}
```

## Important Considerations

- **Initialization**: Uninitialized rows in a jagged array will cause a `NullReferenceException` if accessed. Always ensure each row is initialized before use.
- **Memory Efficiency**: Jagged arrays can be more memory-efficient than multi-dimensional arrays if the row sizes vary significantly.

## Summary

Jagged arrays provide a flexible way to handle collections of data with different lengths, making them a versatile choice for many programming scenarios. Understanding how to use and manipulate them is key to effectively managing non-uniform data structures in C#.

