---
title: Sorting Elements in an Array
---

# {{ title }}

!!! note "From the syllabus"
    **AQA: Bubble Sort (4.3.5.1):** Understand and be able to trace (and analyze the time complexity) of the bubble sort algorithm. Time complexity is $O(n^{2})$.

Sorting is a fundamental procedure in computer science, and there are several algorithms available to organize data. One of the simplest, yet least efficient, is the **bubble sort**.

The bubble sort algorithm works by repeatedly stepping through the array, comparing adjacent elements and swapping them if they are in the wrong order. Each pass through the array moves the largest unsorted element to its correct position, "bubbling" it up to the top. This process is repeated until no more swaps are needed.

## Example of Bubble Sort in Action

Consider the array `{ 23, 16, 9, 86, 54, 3 }`. After each pass of the bubble sort, the array will look like this:

1. `{ 16, 9, 23, 54, 3, 86 }`  // 86 has bubbled to the top
2. `{ 9, 16, 23, 3, 54, 86 }`
3. `{ 9, 16, 3, 23, 54, 86 }`
4. `{ 9, 3, 16, 23, 54, 86 }`
5. `{ 3, 9, 16, 23, 54, 86 }`  // Array is now sorted

## Bubble Sort Code in C#

```cs
using System;

namespace BubbleSortExample
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] myArray = { 23, 16, 9, 86, 54, 3 };
            int temp;

            Console.Clear();
            Console.WriteLine("Initial contents of the array:");
            foreach (int value in myArray)
            {
                Console.Write($"{value} ");
            }
            
            // Bubble Sort Implementation
            for (int i = 0; i < myArray.Length - 1; i++)
            {
                for (int j = 0; j < myArray.Length - 1 - i; j++)
                {
                    if (myArray[j] > myArray[j + 1])
                    {
                        // Swap the elements
                        temp = myArray[j];
                        myArray[j] = myArray[j + 1];
                        myArray[j + 1] = temp;
                    }
                }
            }

            Console.WriteLine("\nSorted array:");
            foreach (int value in myArray)
            {
                Console.Write($"{value} ");
            }
        }
    }
}
```

## Optimizing the Algorithm

The code above will sort the array, but it is not efficient. It continues making passes even if the array is already sorted. To fix this, we can add a `bool swapped` flag:

```cs
bool swapped;
for (int i = 0; i < myArray.Length - 1; i++)
{
    swapped = false;
    for (int j = 0; j < myArray.Length - 1 - i; j++)
    {
        if (myArray[j] > myArray[j + 1])
        {
            // Swap the elements
            temp = myArray[j];
            myArray[j] = myArray[j + 1];
            myArray[j + 1] = temp;
            swapped = true;
        }
    }
    // If no two elements were swapped in the inner loop, break
    if (!swapped) break;
}
```

This version stops if no swaps are made during a pass, indicating the array is already sorted.

## Understanding the Trace Table

Use the following trace table to understand how elements are swapped:

| `i` | `j` | `0` | `1` | `2` | `3` | `4` | `5` |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  0  |  0  | 16  | 23  |  9  |  86 |  54 |  3  |
|     |  1  | 16  |  9  | 23  |  86 |  54 |  3  |
|     |  2  | 16  |  9  | 23  |  54 |  86 |  3  |
|     |  3  | 16  |  9  | 23  |  54 |  3  | 86  |
|     |  4  | 16  |  9  | 23  |   3 |  54 | 86  |
|  1  |  0  |  9  | 16  | 23  |   3 |  54 | 86  |
|  1  |  1  |  9  | 16  |  3  |  23 |  54 | 86  |
|  1  |  2  |  9  |  3  | 16  |  23 |  54 | 86  |

Notice how each pass reduces the number of elements that need to be compared (`j < myArray.Length - 1 - i`).

## Built-in Methods for Sorting

Although it's important to understand sorting algorithms and their efficiency, C# provides built-in methods for sorting arrays:

- `Array.Sort(myArray);` sorts the array in ascending order.
- `Array.Reverse(myArray);` reverses the order of elements.

Using these methods is much more efficient than manually implementing a sorting algorithm in most practical scenarios.

Understanding and implementing algorithms like bubble sort is crucial for grasping the fundamentals of algorithm development and analyzing time complexity, which are key skills in computer science.
