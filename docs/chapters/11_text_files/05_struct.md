---
title: Understanding `struct` in C\#
---

# {{ title }}

A `struct` (short for structure) in C# is a value type used to represent a collection of related data fields where each field can be of a different type. Unlike an array, where all elements must be of the same type, a `struct` allows you to group different data types together in a single unit. This concept is similar to a __record__ in other programming languages.

## Characteristics of `struct`

- **Value Type**: Unlike classes, which are reference types, structs are value types. This means they are stored on the stack, not the heap, and when you assign a struct to another struct, a _copy_ of the data is made.
- **No Inheritance**: Structs cannot inherit from other structs or classes, but they can implement interfaces.
- **Lightweight**: Structs are generally used for small, simple data structures that do not require the overhead of a class.

Structs are ideal for representing small data structures that have a fixed format, such as the ones we’ll use in our examples. Getting familiar with structs will also help you understand the basics of classes, as they share many similar features.

## Defining a `struct`

For our simple TODO application, a `struct` could be defined as follows:

```cs
struct Todo
{
    public DateTime TaskDueDate;
    public string Task;
    public string Status;
}
```

This `struct` has three fields:

- `TaskDueDate`: A `DateTime` field to store the due date of the task.
- `Task`: A `string` field for the task description.
- `Status`: A `string` field for the status of the task (e.g., "In Progress", "Not Started").

### Declaring and Using a `struct`

We can declare a variable of the `Todo` struct type as follows:

```cs
Todo task;
```

To use the struct in our program, we access each field using the dot (`.`) operator:

```cs
static void Main(string[] args)
{
    Todo task;

    Console.Clear();
    Console.WriteLine("TODO Manager");

    Console.WriteLine("Enter the task details:");

    Console.Write("Due Date (e.g., 13/04/2021): ");
    task.TaskDueDate = Convert.ToDateTime(Console.ReadLine());

    Console.Write("Description: ");
    task.Task = Console.ReadLine();

    Console.Write("Status: ");
    task.Status = Console.ReadLine();

    // Writing the struct data to a file
    string filename = "todo.csv";
    using (StreamWriter sw = new StreamWriter(filename, true))
    {
        sw.WriteLine($"{task.TaskDueDate.ToShortDateString()},{task.Task},{task.Status}");
    }

    Console.WriteLine("Task added successfully!");
}
```

### Using the `new` Keyword

When you create a struct without using the `new` keyword, all fields must be assigned a value before you can use them:

```cs
Todo task; // All fields need to be assigned values manually.
task.TaskDueDate = DateTime.Now; // Assigning values to each field.
task.Task = "Complete homework";
task.Status = "Not Started";
```

Alternatively, you can use the `new` keyword to initialize the struct:

```cs
Todo task = new Todo(); // All fields are initialized to their default values.
task.TaskDueDate = DateTime.Now;
task.Task = "Complete homework";
task.Status = "Not Started";
```

## Adding Methods to a `struct`

A struct can contain methods to operate on its data. For example, we can add a method to convert the struct data to a CSV format:

```cs
struct Todo
{
    public DateTime TaskDueDate;
    public string Task;
    public string Status;

    public string ToCSV()
    {
        return $"{TaskDueDate.ToShortDateString()},{Task},{Status}";
    }
}
```

This method returns a comma-separated string of the struct’s fields, making it easy to write to a file:

```cs
sw.WriteLine(task.ToCSV());
```

### Using `ToString()` Method

The `ToCSV()` method is convenient for specific formats like CSV. However, in C#, all structs and classes inherit a `ToString()` method, which can be overridden to provide a string representation of the struct:

```cs
public override string ToString()
{
    return $"{TaskDueDate.ToShortDateString()} : {Task} ({Status})";
}
```

Using this method, we can easily display the struct data:

```cs
Console.WriteLine(task.ToString());
```

## Initializing and Using an Array of Structs

You can also create an array of structs to store multiple tasks:

```cs
Todo[] tasks = new Todo[20];
tasks[0].TaskDueDate = new DateTime(2021, 4, 13);
tasks[0].Task = "Apply for job";
tasks[0].Status = "In Progress";
```

Alternatively, you can use a list for more flexibility:

```cs
List<Todo> tasks = new List<Todo>();
tasks.Add(new Todo { TaskDueDate = DateTime.Now, Task = "Complete homework", Status = "Not Started" });
```

## Constructors and Properties

Structs can also have constructors and properties, similar to classes. A constructor is used to initialize the struct with specific values:

```cs
struct Todo
{
    public DateTime TaskDueDate { get; set; }
    public string Task { get; set; }
    public string Status { get; set; }

    // Constructor
    public Todo(DateTime taskDueDate, string task, string status)
    {
        TaskDueDate = taskDueDate;
        Task = task;
        Status = status;
    }
}
```

Now you can create and initialize a struct in a single statement:

```cs
Todo task = new Todo(DateTime.Now, "Study for exam", "In Progress");
```

## Summary

- **Value Type**: Structs are stored on the stack and are copied when assigned to another variable.
- **Lightweight**: Suitable for small, immutable data structures.
- **No Inheritance**: Structs cannot inherit from other structs or classes, but they can implement interfaces.
- **Methods and Properties**: Structs can have their own methods, properties, and constructors, making them versatile.

## Exercises

1. **Create a Struct for Students**: Define a `Student` struct with fields for name, age, and grade. Create an array of students and display their details.
2. **Implement a `ToString()` Method**: For the `Student` struct, override the `ToString()` method to provide a custom string representation.
3. **Manage a List of Todos**: Expand the TODO application to handle a list of `Todo` structs, allowing users to add, edit, and remove tasks.

