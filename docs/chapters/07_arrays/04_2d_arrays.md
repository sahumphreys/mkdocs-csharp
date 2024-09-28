---
title: Arrays with More Than One Dimension
---

# {{ title }}

A one-dimensional array, also known as a **vector** in mathematics, stores data in a linear sequence. However, when we need to represent more complex data structures like a chess board or a table with rows and columns, we use multi-dimensional arrays. A two-dimensional array is often called a **matrix** in mathematics.

Arrays can also have more than two dimensions, but these can become complicated to manage and visualize. For now, we'll focus on one-dimensional and two-dimensional arrays.

## Declaring Multi-Dimensional Arrays

Multi-dimensional arrays in C# are declared similarly to one-dimensional arrays, but with additional commas to represent each dimension:

```cs
int[,] matrix;   // Two-dimensional array (2D array)
int[,,] cube;    // Three-dimensional array (3D array)
```

As with one-dimensional arrays, memory needs to be allocated using the `new` keyword:

```cs
int[,] matrix = new int[8,8];  // 8x8 chessboard
int[,] myTable = new int[4,5]; // Table with 4 rows and 5 columns
```

In `myTable`, the first dimension represents the number of rows, and the second dimension represents the number of columns. This means `myTable` has 4 rows and 5 columns:

|   | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| 0 | 3 | 7 | 4 | 2 | 1 |
| 1 | 7 | 2 | 8 | 9 | 8 |
| 2 | 5 | 5 | 2 | 0 | 5 |
| 3 | 3 | 9 | 5 | 2 | 6 |

## Initializing a 2D Array

Just like one-dimensional arrays, a two-dimensional array can be initialized with values using curly braces:

```cs
int[,] matrix = 
{
    { 1, 2, 3, 4 },
    { 5, 6, 7, 8 }
};
```

This array has 2 rows and 4 columns.

## Accessing Elements in a 2D Array

To access an element in a two-dimensional array, you need to specify both indices: the row index and the column index.

```cs
int value = matrix[0, 2]; // Accesses the element in the first row, third column (value is 3)
matrix[row, col] = 10;    // Assigns the value 10 to the specified row and column
```

Each dimension of the array has its own length, which can be accessed using the `GetLength()` method:

- `matrix.GetLength(0);` returns 2 (number of rows).
- `matrix.GetLength(1);` returns 4 (number of columns).

## Iterating Through a 2D Array

To iterate through all elements in a two-dimensional array, we typically use two nested loops, one for each dimension:

```cs
for (int row = 0; row < matrix.GetLength(0); row++)
{
    for (int col = 0; col < matrix.GetLength(1); col++)
    {
        Console.WriteLine($"Element at ({row},{col}) is {matrix[row, col]}");
    }
}
```

This will print every element in the array, along with its position.

## Practical Example: Representing a Chessboard

A chessboard can be represented as an 8x8 two-dimensional array, where each element could store a piece's information or whether the square is empty:

```cs
char[,] chessboard = new char[8,8];
chessboard[0,0] = 'R'; // Rook
chessboard[0,1] = 'N'; // Knight
// Initialize other pieces...
```

## Handling More Dimensions

For three-dimensional arrays, the concept extends with an additional index. For example, a `cube` with dimensions `[3, 3, 3]` could represent a 3x3x3 Rubik's Cube. Each element in the cube would then require three indices to be accessed.

## Summary

Multi-dimensional arrays extend the concept of simple arrays to allow for more complex data representations, such as tables, grids, and even 3D structures. Understanding how to use them is crucial for handling structured data efficiently in programming.
