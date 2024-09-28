---
title: Reading from a Text File in C\#
---

# {{ title }}

Reading data from a text file in C# is straightforward, using the `StreamReader` class. This class allows you to read the contents of a text file line-by-line or all at once. Let’s look at how to read data from a file effectively, and handle common issues like file existence and end-of-file detection.

## Example Code

Add the following code to your project after the code for writing to the file:

```cs
using (StreamReader sr = new StreamReader("text.txt"))
{
    string strIn = sr.ReadLine();
    while (strIn != null)
    {
        Console.WriteLine(strIn);
        strIn = sr.ReadLine();
    }
}
```

### Explanation

- **Opening the Stream**: The `StreamReader` object, `sr`, is initialized with the name of the file, `text.txt`. This file should exist in the current directory.
- **Reading Line-by-Line**: The first line is read using `ReadLine()` and stored in the `strIn` variable. The `while` loop continues reading until the end of the file is reached (when `strIn` becomes `null`).
- **Printing to Console**: Each line read from the file is printed to the console using `Console.WriteLine(strIn);`.

## Combining Operations

You can simplify the loop condition by combining the read operation directly in the `while` condition:

```cs
using (StreamReader sr = new StreamReader("text.txt"))
{
    string strIn;
    while ((strIn = sr.ReadLine()) != null)
    {
        Console.WriteLine(strIn);
    }
}
```

This version is more concise and is a common pattern for reading lines from a file until the end is reached.

## Checking for End of File with `Peek()`

An alternative to using `ReadLine()` and checking for `null` is to use the `Peek()` method:

```cs
using (StreamReader sr = new StreamReader("text.txt"))
{
    while (sr.Peek() != -1)  // -1 indicates the end of the file
    {
        string strIn = sr.ReadLine();
        Console.WriteLine(strIn);
    }
}
```

- **How `Peek()` Works**: `Peek()` returns the next character to be read without removing it from the stream. If the next character is `-1`, it means the end of the file has been reached.

## Handling Exceptions

When working with files, it’s essential to handle exceptions that may occur if the file is missing or inaccessible. The following example demonstrates how to use a `try...catch` block to manage these scenarios gracefully:

```cs
string filename = "text.txt";
try
{
    using (StreamReader sr = new StreamReader(filename))
    {
        Console.WriteLine($"File: {filename} has been opened.");
        string strIn;
        while ((strIn = sr.ReadLine()) != null)
        {
            Console.WriteLine(strIn);
        }
    }
}
catch (FileNotFoundException)
{
    Console.WriteLine($"Cannot find file: {filename}");
}
catch (DirectoryNotFoundException)
{
    Console.WriteLine("The specified directory was not found.");
}
catch (IOException ex)
{
    Console.WriteLine($"An I/O error occurred: {ex.Message}");
}
```

### Exception Types to Handle

1. **`FileNotFoundException`**: This exception is thrown if the file specified cannot be found.
2. **`DirectoryNotFoundException`**: This exception is thrown if the directory specified in the file path does not exist.
3. **`IOException`**: A general exception for I/O errors, such as file access being denied or the file being used by another process.

### Best Practices

- **Wrap File Operations in `try...catch`**: Always wrap your file operations in a `try...catch` block to handle exceptions gracefully and prevent your program from crashing unexpectedly.
- **Use `using` Statements**: Ensure that streams are properly closed by using the `using` statement, which automatically disposes of the stream when the block is exited.
- **Check File Existence**: Before attempting to read from a file, consider checking if the file exists using `File.Exists(filename)`.

## Exercise

1. **Modify the Program**: Change the file name in the example code to a file that does not exist on your system. Run the program and observe how the exceptions are handled.
2. **Experiment with `Peek()`**: Replace the `while` loop condition with the `Peek()` method and observe the differences in behavior.
3. **Read Entire File**: Modify the code to read the entire contents of the file into a single string using `ReadToEnd()` and then print it out.
