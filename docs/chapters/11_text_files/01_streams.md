---
title: Understanding Streams in C#
---

# {{ title }}

In .NET, **streams** are fundamental to how input and output (I/O) operations are handled, especially when working with files. Nowadays, almost all I/O is managed using streams, making it essential to grasp this concept early on.

To work with streams and other file-handling operations in C#, you need to include the I/O namespace in your application:

```cs
using System.IO;
```

## What is a Stream?

A **stream** can be thought of as a pipeline through which data flows between an application and a data source or destination. This data source could be a file on a hard drive, a server on the internet, a printer, or even a device like a scanner or sound card. Essentially, any external device that can send or receive data can use streams.

Streams in .NET provide a consistent way to handle different data sources and sinks, abstracting the complexity of direct device interaction. This abstraction allows us to focus on data processing without worrying about the underlying I/O mechanisms.

In simple terms, a stream represents a data source as an object that can read or write data. It abstracts the details of how data is being transferred, making it easier to handle various I/O operations.

## Characteristics of Streams

From a computer's perspective, a stream is an ordered sequence of bytes. There are different types of streams for various purposes, such as:

- **Text Streams**: For working with text files.
- **Binary Streams**: For working with binary data, which will be covered in the next chapter.
- **Network Streams**: For communication across networks.

This chapter focuses specifically on the `FileStream` class, which deals with file operations.

## Opening and Closing Streams

A stream **must be opened** before use and **must be closed** once operations are complete. This ensures that resources are properly allocated and released. Failure to close a stream can lead to resource leaks and other issues.

!!! note
    Managing I/O in C# offers many options, which can be overwhelming initially. The complexity is not in the I/O itself but in choosing the right class or method for the task at hand.

## Basic Stream Operations

Regardless of the type of stream, the fundamental operations remain consistent:

1. **Create/Open**: Establish a connection to a data source, specifying the mode of access (read, write, or both).
2. **Read**: Retrieve data from the stream.
3. **Write**: Send data to the stream.
4. **Seek**: Navigate to a specific position in the stream (not supported by all streams, such as network streams).
5. **Close**: Disconnect from the data source and release resources.

Once a stream is connected to the data source, the stream itself handles the connection details, allowing you to focus on manipulating the data.

## Text Streams

A **text file** is the simplest and most common type of file. It contains plain text characters without any additional formatting. For example, while a `.docx` file may appear to contain text, it also includes complex binary formatting data. In contrast, a text file is natively readable and can be displayed without errors by basic text editors like Notepad on Windows.

### Classes for Handling Text Files

To read and write text in C#, you mainly use two classes:

- **TextReader**: For reading text data. Key methods include:
  - `ReadLine()`: Reads a line of characters from the stream.
  - `ReadToEnd()`: Reads all characters from the current position to the end of the stream.

- **TextWriter**: For writing text data. Key methods include:
  - `Write()`: Writes data to the stream without a newline.
  - `WriteLine()`: Writes data followed by a newline.

Both `StreamReader` and `StreamWriter` inherit from `TextReader` and `TextWriter` respectively. These are the primary classes used for handling text file operations in C#.

### Example: Reading and Writing Text Files

Here's a basic example of using `StreamReader` and `StreamWriter` to handle text file operations:

```cs
// Writing to a text file
using (StreamWriter writer = new StreamWriter("example.txt"))
{
    writer.WriteLine("Hello, World!");
    writer.WriteLine("This is a simple text file.");
}

// Reading from a text file
using (StreamReader reader = new StreamReader("example.txt"))
{
    string line;
    while ((line = reader.ReadLine()) != null)
    {
        Console.WriteLine(line);
    }
}
```

In this example, we use `StreamWriter` to write text to a file and `StreamReader` to read from it. The `using` statement ensures that the stream is properly closed after the operation is complete.

## Summary

Streams provide a powerful abstraction for handling various I/O operations in C#. Understanding how to work with different types of streams is crucial for effective file handling. In this chapter, we covered the basics of text streams using `StreamReader` and `StreamWriter`. In the next chapter, we'll explore binary streams and how they differ from text streams.

**Exercise**: Try creating a program that reads from one text file and writes only lines containing a specific keyword to another file using `StreamReader` and `StreamWriter`.
