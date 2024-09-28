---
title: JSON Files
---

# {{ title }}

## Introduction to JSON

**JavaScript Object Notation (JSON)** is a popular standard for representing structured data. It is similar to XML in that it stores data in a structured format, but it uses a different, more concise syntax. JSON files are often easier to read and write compared to XML, making them a popular choice for data interchange between applications.

### Key Features of JSON

- **Lightweight**: JSON uses a minimal syntax, reducing the size of data representations.
- **Human-Readable**: While primarily designed for machine parsing, JSON is easier for humans to read than XML.
- **Language-Independent**: JSON is text-based and can be used with almost any programming language, including C#.

## Working with JSON in C#

To illustrate the use of JSON, we'll extend our book management system. Instead of storing a single book, we'll work with a list of books, which will be serialized and deserialized using JSON.

### Using the `List<T>` Collection

We will use a `List<Book>` to store multiple books. The `List<T>` class is a dynamic data structure that can grow and shrink as items are added or removed. This makes it more flexible than arrays. 

To use the `List<T>`, include the `System.Collections.Generic` namespace:

```csharp
using System.Collections.Generic;
```

### Initializing the List

First, we'll create a list and add several books to it:

```csharp
List<Book> books = new List<Book>();
books.Add(new Book(1, "Wind in the Willows", "Kenneth Grahame", 14.99, 1908));
books.Add(new Book(2, "Alice in Wonderland", "Lewis Carroll", 9.99, 1895));
books.Add(new Book(3, "Treasure Island", "R.L. Stevenson", 14.99, 1883));
books.Add(new Book(4, "Oliver Twist", "Charles Dickens", 9.99, 1838));
books.Add(new Book(5, "Moby Dick", "Herman Melville", 2.99, 1851));
books.Add(new Book(6, "Frankenstein", "Mary Shelley", 4.99, 1818));
```

### Serializing the List to JSON

We can save this list of books to a JSON file using the `JsonSerializer` class. Here's how to do it:

```csharp
using System.Text.Json;  // Required for JsonSerializer
using System.IO;         // Required for StreamWriter

static void SaveAll(List<Book> books, string filename)
{
    using (StreamWriter writer = new StreamWriter(filename))
    {
        var options = new JsonSerializerOptions { WriteIndented = true };
        string json = JsonSerializer.Serialize(books, options);
        writer.Write(json);
    }
}
```

### Explanation

1. **Creating the StreamWriter**: This creates a stream to write to the specified `filename`.
2. **Setting Options**: We use `JsonSerializerOptions` to format the JSON with indentation for better readability.
3. **Serializing the List**: `JsonSerializer.Serialize` converts the list of books to a JSON-formatted string.
4. **Writing to File**: The JSON string is written to the file using `StreamWriter.Write()`.

### Deserializing the JSON File

To read the data back from the JSON file, we use the following method:

```csharp
using System.Text.Json;  // Required for JsonSerializer
using System.IO;         // Required for StreamReader

static List<Book> Load(string filename)
{
    using (StreamReader reader = new StreamReader(filename))
    {
        string json = reader.ReadToEnd();
        return JsonSerializer.Deserialize<List<Book>>(json);
    }
}
```

### Explanation

1. **Reading the File**: `StreamReader` reads the entire contents of the JSON file into a string.
2. **Deserializing**: `JsonSerializer.Deserialize` converts the JSON string back into a `List<Book>`.

## Defining the `Book` Struct

To work with the `JsonSerializer`, our `Book` struct must use properties instead of fields:

```csharp
public struct Book
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Author { get; set; }
    public double Price { get; set; }
    public int Year { get; set; }

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

### Properties vs. Fields

- **Fields**: Simple variables inside a class or struct, e.g., `public string firstName;`.
- **Properties**: Encapsulate fields with getter and setter methods, e.g., `public int Age { get; set; }`.

For serialization to work correctly, the `Book` struct must expose its data through properties.

## Comparing JSON and XML Serialization

- **JSON**:

    - More compact and readable.
    - Easier to parse in many programming languages.
    - Widely used for web APIs.

- **XML**:

    - More verbose but supports more complex data structures.
    - Offers features like schemas and namespaces.
    - Still used in many enterprise systems.

## Exercises

1. Modify the `Book` struct to include a list of `Review` objects, and update the serialization code to handle this nested structure.
2. Write a method to update the price of a book in the JSON file and re-serialize it.
3. Research the difference between JSON and YAML. Which would you prefer for a configuration file and why?

### Further Reading

- [JSON in C#](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-overview)
- [Comparison between JSON and XML](https://www.geeksforgeeks.org/difference-between-json-and-xml/)

Understanding serialization with JSON will enable you to efficiently store and exchange data between applications.
