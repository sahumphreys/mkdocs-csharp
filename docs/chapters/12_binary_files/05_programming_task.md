---
title: Programming Task - Running Club revised
---

# {{ title }}

## Running Club

Rewrite the running club program from the last chapter but this time read/write all data to a JSON (or XML) file using serialization.

Create a separate file to hold the Member struct (this must be wrapped in the same `namespace` as your main program file):

```cs
public struct Member
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }
        public string Distance { get; set; }
    }
```

Present the user with a menu of options:

```cs
Console.Clear();
Console.WriteLine("MAIN MENU\n");
Console.WriteLine("1 - Add Member");
Console.WriteLine("2 - Show Members");
Console.WriteLine("3 - Search for Member");
Console.WriteLine("4 - Save All");
Console.WriteLine("5 - QUIT");
Console.Write("> ");
menuOption = Convert.ToInt32(Console.ReadLine());
```

Use a `switch` to select one of the options.  Each option should call a relevant method to handle the option.

## Todo Manager

Chapter 11 included code to implement a simple task manager.  Adapt and extend this code to read and write data from the JSON file using serialization.  Create a `struct` for the task in the project directory (e.g. `taskItem.cs`).

Extend the program to include:

- `Boolean` field to indicate if the task has been completed
- A Category field e.g. "Home", "College".  Choose categories that suit your own circumstances
- Provide an option for the user to select only those tasks from a given category
