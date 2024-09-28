---
title: Accessing Elements of the Array
---

In C#, you access elements of an array using the **square bracket notation**. Remember that array indexing is **zero-based**. This means that:

- `myArray[0]` references the **first** element in the array.
- `myArray[2]` references the **third** element in the array.

You can both retrieve and set the value of an element using this notation:

```cs
myArray[2] = 9;          // Sets the third element to 9
string[] primates = { "Gorilla", "Ape", "Lemur", "Simian" };
primates[0] = "Baboon";  // Replaces "Gorilla" with "Baboon"
```

## Using Loops to Access Array Elements

Loops are ideal for accessing each element in turn. The following `for` loop prints each element of the array:

```cs
int[] myArray = { 23, 16, 9, 86, 54, 3 };
for (int i = 0; i < myArray.Length; i++)
{
    Console.WriteLine(myArray[i]);  // Print each element
}
```

- `myArray.Length` is a property that returns the number of elements in the array. Here, it would return `6`.
- The loop runs from `i = 0` to `i < myArray.Length - 1`, ensuring we do not exceed the bounds of the array.

## Array Bounds and Exceptions

- **Lower Bound**: The lowest index of an array is always `0`.
- **Upper Bound**: The highest index is always `myArray.Length - 1`.
- **Out-of-Bounds Access**: Trying to access an index outside this range (e.g., `myArray[6]` or `myArray[-1]`) will result in an `IndexOutOfRangeException`. This is an error indicating that you are trying to access a memory location not allocated to the array.

!!! note
    You can use expressions within the square brackets, such as `myArray[i + 1]` or `myArray[12 / 4 - 1]`, as long as the result is a valid index.

## Using the `foreach` Loop

The `foreach` loop is a convenient way to iterate through all elements in an array:

```cs
int[] myArray = { 23, 16, 9, 86, 54, 3 };
foreach (int element in myArray)
{
    Console.WriteLine(element);  // Print each element
}
```

- The `foreach` loop processes each element in the array, from the first to the last.
- The loop variable `element` is read-only within the loop and represents the current array element.
- This loop is ideal for read-only access but **cannot** be used to modify the array elements directly.

## Additional Tips

- **Empty Arrays**: An array can be declared with a size of zero, but accessing any element will throw an `IndexOutOfRangeException`.
- **Null Arrays**: If an array is not initialized, attempting to access it will result in a `NullReferenceException`. Always check if an array is initialized before use.

