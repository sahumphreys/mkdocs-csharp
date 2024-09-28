---
title: Binary Files
---

# {{ title }}


Binary files are a crucial aspect of data storage in programming, allowing for efficient storage and retrieval of data. Unlike text files, which store data in a human-readable format, binary files encode data in a way that is optimized for machine processing. This document will guide you through the process of creating, writing, and reading binary files in C#.

## Creating a Binary File

To create a binary file, we use the BinaryWriter class. Below is an example of how to create a binary file named test.bin:

```cs
string filename = "test.bin";
using (BinaryWriter bw = new BinaryWriter(File.Open(filename, FileMode.Create)))
{
    // Writing operations will go here
}
```

### Understanding FileMode

The FileMode parameter specifies how the operating system should open the file. The common options include:

- Create: Creates a new file or overwrites an existing file.
- Open: Opens an existing file and raises an exception if the file does not exist.
- Append: Opens an existing file and seeks to the end of the file for writing; creates a new file if it does not exist.
- OpenOrCreate: Opens an existing file or creates a new one if it does not exist.

## Defining a Data Structure

To write data to a binary file, we first define a struct to represent the data. A struct is a value type that can encapsulate data and related functionalities. Here’s an example of a Book struct:

```cs
private struct Book
{
    public int Id;
    public string Title;
    public string Author;
    public double Price;
    public int Year;

    public Book(int id, string title, string author, double price, int year)
    {
        Id = id;
        Title = title;
        Author = author;
        Price = price;
        Year = year;
    }
}
```

The constructor method must match the name of the `struct`, and parameters must be provided when creating an instance of the Book type:

```cs
Book willows = new Book(1, "Wind in the Willows", "Kenneth Grahame", 14.99, 1908);
```


## Writing Data to a Binary File

To write to the file, we call the Write() method of the BinaryWriter object:

```cs
using (BinaryWriter writer = new BinaryWriter(File.Open(filename, FileMode.Create)))
{
    writer.Write(willows.Id);           // Accessing the fields of the struct using the dot operator
    writer.Write(willows.Title);
    writer.Write(willows.Author);
    writer.Write(willows.Price);
    writer.Write(willows.Year);
}
```

As an aside, we can gather information about the file using the FileInfo class:

```cs
FileInfo fInfo = new FileInfo(filename);
Console.WriteLine($"{fInfo.Length} bytes");
```

## Reading Data from a Binary File

Reading from a binary file requires knowledge of the file's structure, as the data must be read in the correct format. The `BinaryReader` class provides several Read methods for different data types. Some of the available methods include:

- `ReadString()`
- `ReadInt32()`
- `ReadDouble()`
- `ReadBoolean()`

Each `Read()` call advances the file pointer by the appropriate number of bytes. For example, calling `ReadBoolean()` when we mean to use `ReadInt32()` will advance the pointer by only one byte instead of the required four, leading to data mismatches.

Here’s an example of reading our Book data from the binary file:

```cs
using (BinaryReader br = new BinaryReader(File.OpenRead(filename)))
{
    int id = br.ReadInt32();
    string title = br.ReadString();
    string author = br.ReadString();
    double price = br.ReadDouble();
    int year = br.ReadInt32();

    Console.WriteLine($"ID: {id}, Title: {title}, Author: {author}, Price: {price}, Year: {year}");
}
```

## Common Errors to Avoid

- **Mismatched Read/Write Types**: Ensure the types used in Write() and Read() methods match exactly to prevent data corruption.
- **File Access Issues**: Make sure the file is not open elsewhere, which can lead to exceptions when trying to read or write.

!!! note
    As with text files, you are strongly recommended to handle exception errors if the file cannot be found, or opened etc..

The Microsoft documentation has a good summary of all types of file handling available via the `System.IO` namespace:  [https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/ms404278(v=vs.100)?redirectedfrom=MSDN](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/ms404278(v=vs.100)?redirectedfrom=MSDN).
