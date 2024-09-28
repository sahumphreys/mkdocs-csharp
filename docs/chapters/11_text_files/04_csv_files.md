---
title: Working with CSV Files in C\#
---

# {{ title }}

A Comma Separated Values (CSV) file is a common and simple format for storing tabular data, where each item is separated by a comma. Each line in a CSV file represents a record, and each comma-separated item is a __field__ within that record. CSV files are widely used for storing structured data such as contact lists, to-do lists, and simple databases because they are easy to read and write.

## Understanding CSV Structure

A CSV file has a straightforward structure where:

- Each line in the file corresponds to a single record.
- Each field within a record is separated by a comma.

For example, consider the following to-do list stored in a CSV file:

```text
13/04/2021,Apply for job,In progress
13/04/2021,Clean out hamster cage,Not Started
14/04/2021,Take car in for service,Not Started
15/04/2021,Buy birthday card for brother,Not Started
```

Each line represents a task with three fields: the due date, the task description, and its status.

## Writing to a CSV File

Let’s create a simple program to add new tasks to our to-do list and save them in a CSV file. Here's how you can do it:

```cs
using System;
using System.IO;

namespace csvfiles
{
    class Program
    {
        static void Main(string[] args)
        {
            DateTime taskDueDate;
            string task;
            string status;

            Console.Clear();
            Console.WriteLine("TODO Manager");

            // Getting input from the user
            Console.WriteLine("Enter the task: ");
            Console.Write("Due Date (e.g., 13/04/2021): > ");
            taskDueDate = Convert.ToDateTime(Console.ReadLine());
            Console.Write("Description: > ");
            task = Console.ReadLine();
            Console.Write("Status: > ");
            status = Console.ReadLine();

            // Writing to CSV file
            string filename = "todo.csv";
            using (StreamWriter sw = new StreamWriter(filename, true))
            {
                sw.WriteLine($"{taskDueDate.ToShortDateString()},{task},{status}");
            }

            Console.WriteLine("Task added successfully!");
        }
    }
}
```

- **Getting User Input**: We prompt the user to enter the due date, description, and status of the task.
- **Writing to the File**: The program writes the new task to the file `todo.csv` using `StreamWriter`. The `true` parameter in the `StreamWriter` constructor enables __append mode__, which prevents overwriting existing data.
- **String Interpolation**: We use string interpolation (`$"{taskDueDate.ToShortDateString()},{task},{status}"`) to format the data into a single line, with each field separated by a comma.

!!! note
    The `DateTime` field is converted using `ToShortDateString()` to only store the date, not the time.

## Reading from a CSV File

To read and process the data stored in a CSV file, we need to read each line and split it into its individual fields using the `Split()` method.

Here’s how we can read the data from the `todo.csv` file and display it:

```cs
using System;
using System.IO;

namespace csvfiles
{
    class Program
    {
        struct Todo
        {
            public DateTime taskDueDate;
            public string task;
            public string status;

            public override string ToString()
            {
                return $"{taskDueDate.ToShortDateString()} : {task} ({status})";
            }
        }

        static void Main(string[] args)
        {
            string filename = "todo.csv";
            try
            {
                using (StreamReader sr = new StreamReader(filename))
                {
                    Todo taskItem;
                    string line;

                    Console.WriteLine("TODO List:");

                    while ((line = sr.ReadLine()) != null)
                    {
                        string[] items = line.Split(',');
                        taskItem.taskDueDate = Convert.ToDateTime(items[0]);
                        taskItem.task = items[1];
                        taskItem.status = items[2];
                        Console.WriteLine(taskItem.ToString());
                    }
                }
            }
            catch (FileNotFoundException)
            {
                Console.WriteLine($"File {filename} not found.");
            }
            catch (IOException ex)
            {
                Console.WriteLine($"An I/O error occurred: {ex.Message}");
            }
        }
    }
}
```


- **Reading the CSV File**: The program reads each line from the `todo.csv` file using `StreamReader`.
- **Splitting the Line**: Each line is split into an array of fields using `Split(',')`.
- **Mapping to `struct`**: The values from the array are assigned to the `taskItem` struct fields: `taskDueDate`, `task`, and `status`.
- **Displaying the Data**: The `ToString()` method is overridden to display the data in a readable format.

### Using `struct` for Data Management

Using a `struct` helps organize the data, making it easier to manage and process. The `Todo` struct represents each task, holding the due date, description, and status of the task.

## Best Practices for Working with CSV Files

1. **Error Handling**: Always use `try...catch` blocks to handle potential exceptions, such as missing files or I/O errors.
2. **Append Mode**: Use the append mode (`true` parameter in `StreamWriter`) to add new data without overwriting existing content.
3. **Data Validation**: Validate user input to ensure it is in the correct format (e.g., date format) before writing to the file.
4. **Use `struct` or `class`**: For complex data structures, use a `struct` or `class` to represent each record, making the code more readable and maintainable.

## Exercise

1. **Extend the Program**: Modify the program to allow users to update or delete tasks in the CSV file.
2. **Search Functionality**: Implement a search function to find tasks by their status or due date.
3. **Data Validation**: Add data validation to ensure the date and status are entered correctly by the user.

By understanding and implementing these concepts, you’ll be able to effectively manage CSV files in C# and use them for a variety of applications.
