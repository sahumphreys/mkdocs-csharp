---
title: Writing to a Text File in C\#
---

# {{ title }}

When working with text files in C#, writing data to a file is a common task that is often necessary for logging, saving user input, or storing program results. Let’s walk through a simple example to understand how this works.

## Example Program

```cs
using System;
using System.IO;

namespace TextFiles
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Reading/Writing with text files");

            // Writing to a text file using StreamWriter within a using block
            using (StreamWriter sw = new StreamWriter("text.txt"))
            {
                sw.WriteLine("The first line");
                sw.WriteLine("The second line");
                sw.WriteLine("The third line");
                sw.Flush();  // Optional but recommended for safety
            }
        }
    }
}
```

## Key Concepts Explained

### Including the I/O Namespace

To work with files, you need to include the `System.IO` namespace:

```cs
using System.IO;
```

This namespace provides all the classes necessary for file handling, including the `StreamWriter` class used in this example.

### Using the `using` Statement
The `using` statement is used to ensure that the resources, like file streams, are properly disposed of once they are no longer needed. This automatically closes the stream, which is crucial to prevent resource leaks:

```cs
using (StreamWriter sw = new StreamWriter("text.txt"))
{
    // Code to write to the file
}
```

- **Why use `using`?** The `using` block ensures that `Dispose()` is called on the `StreamWriter` object, which in turn closes the file stream. Forgetting to close a stream can lead to file locks and other resource management issues.
- **Alternative:** Without `using`, you would need to call `sw.Close()` manually. However, it's easy to forget this step, so using the `using` block is considered a best practice.

### Writing to the File
The `StreamWriter` object allows you to write data to a text file. The `WriteLine()` method writes a string followed by a newline character to the file:

```cs
sw.WriteLine("The first line");
```

This method behaves similarly to writing to the console with `Console.WriteLine()`.

### Flushing the Stream
The `Flush()` method forces any buffered data to be written to the underlying file immediately:

```cs
sw.Flush();
```

- **Why flush?** Data written to a file is first stored in a buffer. If the program crashes before the buffer is flushed, the data may not be written completely, leading to an inconsistent file state. While not strictly necessary in this short example, using `Flush()` is good practice in more complex programs to ensure data integrity.

### File Location
In this example, the file `text.txt` is created in the current directory of the project. If you want to specify a different location, use an absolute path:

```cs
using (StreamWriter sw = new StreamWriter(@"C:\path\to\your\file.txt"))
```

### Running the Program
After running the program, a new file named `text.txt` will appear in your project directory with the following contents:

```
The first line
The second line
The third line
```

### Overwriting vs. Appending
By default, `StreamWriter` overwrites any existing file with the same name. If you run the program again, the previous contents of `text.txt` will be replaced. To add new content without overwriting, use the **append mode**:

```cs
using (StreamWriter sw = new StreamWriter("text.txt", true))
{
    sw.WriteLine("The fourth line");
}
```

The second parameter, `true`, enables append mode, ensuring that new content is added to the end of the file.

### Output in Append Mode
After enabling append mode and running the program again, the contents of `text.txt` will be:

```
The first line
The second line
The third line
The fourth line
```

## Exercise
1. Modify the program to ask the user for lines of text and write each line to the file.
2. Experiment with writing different data types (e.g., integers, dates) using `sw.Write()` and see how the file contents change.
3. Implement error handling to manage cases where the file cannot be written (e.g., due to lack of permissions).
