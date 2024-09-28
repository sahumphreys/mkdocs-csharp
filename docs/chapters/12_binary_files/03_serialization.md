---
title: Serialization
---

# {{ title }}

## Introduction to Serialization

Serialization is a technique used to convert an object (or struct) into a stream of bytes for easy storage or transmission. This process can be reversed using **deserialization**, which recreates the object from the serialized data. Serialization is useful for saving the state of objects, transmitting data over networks, or sharing data between different applications.

## Types of Serialization

There are two main types of serialization:

1. **Binary Serialization**: Converts objects into a binary format. It's efficient but not human-readable. Note that Microsoft no longer recommends using the `BinaryFormatter` class due to security concerns. Instead, alternatives like `BinaryWriter` and `BinaryReader` should be used.
   
   > See [Microsoft's security guidance](https://docs.microsoft.com/en-us/dotnet/standard/serialization/binaryformatter-security-guide) for more details.

2. **Human-Readable Serialization**: Converts objects into text formats like XML or JSON, making them easier to read and edit manually. The `XmlSerializer` and `JsonSerializer` classes are commonly used for this purpose.

### When to Use Serialization

Serialization is the preferred method for saving objects and structs to files because it automatically handles the conversion of complex data types into a storable format. Understanding serialization is important for various tasks such as:

- Persisting application state.
- Transferring data between different applications or systems.
- Storing configuration settings or user data.

## XML Serialization in C\#

C# provides the `XmlSerializer` class in the `System.Xml.Serialization` namespace for serializing objects to and from XML format. This allows you to save objects in a structured, human-readable way.

### Example: Serializing and Deserializing an Object

Let's look at how to serialize and deserialize a `Book` object using `XmlSerializer`.

1. **Create a `Book` Object**:
   ```csharp
   Book book = new Book();
   book.Id = 1;
   book.Title = "Wind in the Willows";
   book.Author = "Kenneth Grahame";
   book.Price = 9.99;
   book.Year = 1908;
   ```

2. **Serialize the Object**:
   ```csharp
   using(XmlWriter writer = XmlWriter.Create("books.xml"))
   {
       XmlSerializer serializer = new XmlSerializer(typeof(Book));
       serializer.Serialize(writer, book);
   }
   ```

3. **Deserialize the Object**:
   ```csharp
   using(XmlReader reader = XmlReader.Create("books.xml"))
   {
       XmlSerializer serializer = new XmlSerializer(typeof(Book));
       book = (Book)serializer.Deserialize(reader);
   }

   // Output the book details
   Console.WriteLine(book.Title);
   Console.WriteLine(book.Author);
   Console.WriteLine(book.Price);
   Console.WriteLine(book.Year);
   ```

### Explanation

1. **Creating the Book Object**: Initialize a `Book` object with default values.
2. **Serialization**: 
   - Create an `XmlWriter` object to write to `books.xml`.
   - Instantiate an `XmlSerializer` with the type of object to serialize (`Book` in this case).
   - Call `Serialize()` method, passing in the writer and the `book` object.

   This converts the `Book` object into XML format and writes it to the file `books.xml`.

3. **Deserialization**:
   - Create an `XmlReader` object to read from `books.xml`.
   - Use the `XmlSerializer` to deserialize the XML back into a `Book` object.
   - Output the book details to verify that the object has been correctly reconstructed.

### Key Points to Remember

- **Namespace**: Include `using System.Xml.Serialization;` to access the `XmlSerializer` class.
- **Object Type**: You must specify the type of the object being serialized (`typeof(Book)` in this example).
- **File Handling**: Always close or dispose of the writer and reader objects after use to release file handles and resources.
- **Struct Visibility**: Ensure the `Book` struct or class is public and accessible by the serializer.

## Common Issues and Solutions

1. **Class or Struct Visibility**: 
   - The class or struct you are serializing must be `public`.
   - If defined within the same file as the main program, move it to a separate file with the same namespace.

   ```csharp
   public struct Book
   {
       public int Id;
       public string Title;
       public string Author;
       public double Price;
       public int Year;
   }
   ```

2. **Missing Default Constructor**: 
   - Ensure the class or struct has a parameterless constructor if it is not a simple struct.

3. **Unsupported Types**: 
   - Ensure that only serializable types are used as fields or properties of the class/struct.

## Next Steps

We will see the same process being used for JSON files in the next section. JSON is another popular format for serializing objects due to its lightweight and easy-to-read structure.

### Exercises

1. Create a `Student` class with fields like `Id`, `Name`, `Course`, and `Grade`. Write a program to serialize and deserialize a list of students to/from an XML file.
2. Modify the `Book` example to include a list of reviews for each book. Update the serialization code to handle this nested structure.
3. Explore the use of `DataContractSerializer` for more control over the serialization process.

### Further Reading

- [Serialization and Deserialization](https://docs.microsoft.com/en-us/dotnet/standard/serialization/)

Understanding serialization will help you effectively store and retrieve complex data in your applications.
