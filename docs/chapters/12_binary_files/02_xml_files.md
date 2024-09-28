---
title: XML Files
---

# {{ title }}

## Introduction to XML

As noted earlier, binary files are falling out of favor and being replaced by text-based formats like **XML** and **JSON** for transferring and storing data. Both are human-readable, making them easy to understand and edit. In this lesson, we’ll explore XML, a widely used format for data exchange.

**XML** stands for **Extensible Markup Language** and is used to structure, store, and transport data. It is both machine-readable and human-readable, making it a popular choice in many applications, such as configuration files, web services, and document storage.

### Why Use XML?

- **Structured Data**: XML allows for a well-defined structure with nested elements.
- **Self-Descriptive**: Tags and attributes describe the data, making it easy to understand.
- **Platform Independent**: It can be used across different systems and technologies.

Let’s look at a simple example to understand the structure of an XML file.

## XML Structure Example

Using our book example, the XML representation for a book collection might look like this:

```xml
<books>
    <book id="1">
        <title>Wind in the Willows</title>
        <author>Kenneth Grahame</author>
        <price>14.99</price>
        <year>1908</year>
    </book>
    <book id="2">
        <title>Alice in Wonderland</title>
        <author>Lewis Carroll</author>
        <price>9.99</price>
        <year>1865</year>
    </book>
</books>
```

### Explanation

- **Tags**: Elements are defined with tags (`<title>`, `<author>`), similar to HTML.
- **Attributes**: Elements can have attributes, such as `id="1"`, which provide additional information.
- **Hierarchy**: XML is structured as a tree, with a root element (`<books>`) and nested child elements (`<book>`).

### Common XML Errors

1. **Unclosed Tags**: Every opening tag `<title>` must have a corresponding closing tag `</title>`.
2. **Case Sensitivity**: Tags are case-sensitive, so `<Book>` and `<book>` are different.
3. **Invalid Characters**: Avoid using characters like `<` and `&` inside elements; use escape sequences like `&lt;` and `&amp;`.

## Working with XML in C\#

C# provides several classes in the `System.Xml` namespace for handling XML files. The most commonly used classes include:

- **`XmlDocument`**: Reads and writes the entire XML document.
- **`XmlReader`**: Reads XML data one element at a time, useful for large files.
- **`XmlWriter`**: Writes XML data to a file, stream, or `StringBuilder`.

### Writing to XML Files

To write to an XML file, we use the `XmlWriter` class. Remember to include the `System.Xml` namespace at the top of your program.

```csharp
using System;
using System.Xml;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Writing to an XML file");

        // Create a new book object
        Book willows = new Book(1, "Wind in the Willows", "Kenneth Grahame", 14.99, 1908);

        // Create an XmlWriter object
        using(XmlWriter xmlWriter = XmlWriter.Create("books.xml"))
        {
            xmlWriter.WriteStartDocument();
            xmlWriter.WriteStartElement("books");

            // Write book element
            xmlWriter.WriteStartElement("book");
            xmlWriter.WriteAttributeString("id", willows.Id.ToString());

            xmlWriter.WriteStartElement("title");
            xmlWriter.WriteString(willows.Title);
            xmlWriter.WriteEndElement(); // Close <title>

            xmlWriter.WriteStartElement("author");
            xmlWriter.WriteString(willows.Author);
            xmlWriter.WriteEndElement(); // Close <author>

            xmlWriter.WriteStartElement("price");
            xmlWriter.WriteString(willows.Price.ToString());
            xmlWriter.WriteEndElement(); // Close <price>

            xmlWriter.WriteStartElement("year");
            xmlWriter.WriteString(willows.Year.ToString());
            xmlWriter.WriteEndElement(); // Close <year>

            xmlWriter.WriteEndElement(); // Close <book>
            xmlWriter.WriteEndElement(); // Close <books>
            xmlWriter.WriteEndDocument();
        }

        Console.WriteLine("XML file written successfully.");
    }
}
```

### Key Points

- Start with `WriteStartDocument()` and the root element.
- For each book, use `WriteStartElement()` for elements and `WriteAttributeString()` for attributes.
- Use `WriteEndElement()` to properly close each element.
- Convert all data to strings before writing.

### Reading from XML Files

To read from an XML file, we can use the `XmlReader` class. The `Read()` method allows us to traverse the XML file element by element.

```csharp
using System;
using System.Xml;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Reading from an XML file");

        using (XmlReader xmlReader = XmlReader.Create("books.xml"))
        {
            while (xmlReader.Read())
            {
                if (xmlReader.IsStartElement())
                {
                    switch (xmlReader.Name)
                    {
                        case "title":
                            Console.WriteLine("Title: " + xmlReader.ReadString());
                            break;
                        case "author":
                            Console.WriteLine("Author: " + xmlReader.ReadString());
                            break;
                        case "price":
                            Console.WriteLine("Price: " + xmlReader.ReadString());
                            break;
                        case "year":
                            Console.WriteLine("Year: " + xmlReader.ReadString());
                            break;
                    }
                }
            }
        }
    }
}
```

### Explanation
- **`XmlReader`**: Reads the XML file one element at a time.
- **`IsStartElement()`**: Checks if the current element is a starting tag.
- **`ReadString()`**: Reads the value inside an element, like "Wind in the Willows."

### Using a List of Books

For more complex data, you can use a list of books:

```csharp
using System.Collections.Generic;

List<Book> books = new List<Book>
{
    new Book(1, "Wind in the Willows", "Kenneth Grahame", 14.99, 1908),
    new Book(2, "Alice in Wonderland", "Lewis Carroll", 9.99, 1865)
};

// Writing multiple books
using(XmlWriter xmlWriter = XmlWriter.Create("books.xml"))
{
    xmlWriter.WriteStartDocument();
    xmlWriter.WriteStartElement("books");

    foreach (var book in books)
    {
        xmlWriter.WriteStartElement("book");
        xmlWriter.WriteAttributeString("id", book.Id.ToString());

        xmlWriter.WriteStartElement("title");
        xmlWriter.WriteString(book.Title);
        xmlWriter.WriteEndElement();

        xmlWriter.WriteStartElement("author");
        xmlWriter.WriteString(book.Author);
        xmlWriter.WriteEndElement();

        xmlWriter.WriteStartElement("price");
        xmlWriter.WriteString(book.Price.ToString());
        xmlWriter.WriteEndElement();

        xmlWriter.WriteStartElement("year");
        xmlWriter.WriteString(book.Year.ToString());
        xmlWriter.WriteEndElement();

        xmlWriter.WriteEndElement(); // Close <book>
    }

    xmlWriter.WriteEndElement(); // Close <books>
    xmlWriter.WriteEndDocument();
}
```

### Reading Multiple Books

To read multiple books into a list, use a similar approach:

```csharp
List<Book> books = new List<Book>();
Book currentBook = null;

using (XmlReader xmlReader = XmlReader.Create("books.xml"))
{
    while (xmlReader.Read())
    {
        if (xmlReader.IsStartElement())
        {
            switch (xmlReader.Name)
            {
                case "book":
                    currentBook = new Book();
                    books.Add(currentBook);
                    break;
                case "title":
                    currentBook.Title = xmlReader.ReadString();
                    break;
                case "author":
                    currentBook.Author = xmlReader.ReadString();
                    break;
                case "price":
                    currentBook.Price = double.Parse(xmlReader.ReadString());
                    break;
                case "year":
                    currentBook.Year = int.Parse(xmlReader.ReadString());
                    break;
            }
        }
    }
}
```

### Conclusion

XML is a versatile format for storing structured data. Understanding how to read and write XML files in C# is an essential skill for working with data. Try creating and manipulating your own XML files to get comfortable with these concepts!

### Exercises
1. Create an XML file representing a list of your favorite movies. Include elements like `title`, `director`, `year`, and `rating`.
2. Write a program to read this XML file and display the movies directed by a specific director.
3. Extend the `Book` example to include a `publisher` element. Modify the code to handle this new element.

### Further Reading
- [XML Basics](https://www.w3schools.com/xml/)
- [Working with XML in C#](https://docs.microsoft.com/en-us/dotnet/standard/data/xml/)

Explore more advanced topics like querying XML using LINQ to XML for more powerful data manipulation!
