---
title: Text Files
---

# {{ title }}

!!! note "In this chapter"

    - Explain the need for __persistent data__
    - __Read__ and __write__ data to a text file using the __File__ class
    - Define the full file __path__ of a text file that is to be used
    - Use the __StreamWriter__ class to write one or more lines to a text file
    - Use the __StreamReader__ class to read a text file line by line
    - Recognise that a __struct__ is the implementation of a record in C\#
    - Know how to use a __struct__ as a lightweight class
    - Structure text file using CSV


While a program is running all data is stored in Random Access Memory (RAM), when the program ends (or the computer shuts down), all data in RAM will be lost.  To make our data __persist__ it needs to be saved to an external storage device, or network cloud, as a file.

There are two categories of classes in C\# for dealing with Input/Output (I/O). There are classes that deal with (1) information about the file system itself e.g. copying  or moving files and/or directories, and (2) reading and writing data from different sources.  The different approaches to handling I/O can seem intimidating at first, particularly with the second category as the data can come from a variety of devices (e.g. peripherals, files, network connections).  We've already been interacting with peripheral devices, reading data from the keyboard (`Console.ReadLine()`) and writing data to the screen (`Console.WriteLine`).  In this chapter we'll expand into reading data from files, and writing data to files.

Before getting into the actual reading and writing of data there are some utility classes that deal with file-handling and directories.

!!! note "From the syllabus"
    AQA: Fields, records and files (3.2.1.3/4.1.1.16): Be able to read/write from/to a text file.}
    
    - A **text file** is a computer file that only contains text and has no special formatting such as bold text, italic text, images, etc..  A text file stores all of its data as characters represented by their **Unicode** code.  Text files are read **sequentially**, from the beginning to the end.

## Directories, Files and Paths

- __Directory__: methods for working with folders
- __File__: a class we can use for files
- __Path__: the route to the folder where a file is stored

Let's see, first, how these interact by checking to see if a file called `settings.json` exists in a user's home directory.  Here's the code:

```cs
using System;
using System.IO;

namespace directories
{
    class Program
    {
        static void Main(string[] args)
        {
            string path = "";

            // check for SAH directory in personal user account directory
            try
            {
                // on a Windows system: C:\Users\<my username>\AppData\Roaming
                path = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.ApplicationData), "SAH");
                if (!Directory.Exists(path))
                {
                    Directory.CreateDirectory(path);
                    Console.WriteLine($"Directory created: {path}");
                }
                else
                {
                    Console.WriteLine($"Directory exists: {path}");
                }
            }
            catch
            {
                Console.WriteLine($"Unable to create directory: {path}.  please check permissions");
            }

            if (File.Exists(Path.Combine(path, "settings.json")))
            {
                try
                {
                    // load the file here
                }
                catch (Exception ex)
                {
                    Console.WriteLine($"Unable to load the settings file: {ex.Message}");
                }
            }
            else
            {
                try
                {
                    // create the file here
                }
                catch (Exception ex)
                {
                    Console.WriteLine($"Unable to create the settings file: {ex.Message}");
                }
            }
        }
    }
}
```

There's a lot of code here but most is taken up with __exception handling__.  Handling exceptions when dealing with files and directories is a must so we can deal with I/O errors correctly.

Firstly, we set the __path__:

```cs
path = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.ApplicationData), "SAH");
```

Using the `Combine` method of the `Path` class we concatenate the name of our directory, "SAH", with the ApplicationData (`%APPDATA%`) directory on our Windows box.  In this case it is is set to `C:\Users\<my username>\AppData\Roaming`.  If we have the correct permissions, or know the file should default to a particular location, we could have hard-coded the path e.g. `D:\\MyUSBDrive\\MyProjects`.  NB. the double backslash is required, it's an escape sequence.  If our program is saving data to a location on the user's file system we need to have permission to write to that directory.  Alternatively, we could ask the user for the location.

We then use the `Directory` class to check if this directory exists, if it does not exist it gets created with the `CreateDirectory` method.

It's a similar procedure to check if the file, `settings.json`, exists.  If it does we can load the settings into our application (code not shown), or create the file (code not shown).

!!! warning 
    Before being able to save data to an external storage device the user will need the necessary permissions and access rights.   Both Windows and Linux permit saving data to a user's personal directories.  If you release applications "into the wild" make sure you know where data can be stored.  It is probably safest to ask the user to select the directory.

The `File` class can be used for simple and quick file access.  To write (or read) from a file, the file has to be __opened__, and then __closed__ when finished with.  Here's a very simple example:

```cs
TextWriter myFile = File.CreateText("test.txt");
myFile.WriteLine("Hello, World!");
myFile.Close();
```

This looks very similar to writing text to the `Console`, replacing the Console class with the identifier for our file.  If the file does not exist it will be created and when we've finished with it the file is closed and made available for other programs to use.

This next example using the `ReadAllText()` method to the contents of a file into a string variable:

```cs
static void Main(string[] args)
{
    if(File.Exists("test.txt"))
    {
        string content = File.ReadAllText("test.txt");
        Console.WriteLine("Current content of file:");
        Console.WriteLine(content);
    }
    Console.WriteLine("Please enter new content for the file:");
    string newContent = Console.ReadLine();
    File.WriteAllText("test.txt", newContent);
}
```

This program assumes the path is the current working directory (though not recommended) and if the text file exists reads its contents to a string and displays the contents.  Our program then asks the user for more content which is saved to the file (actually overwriting any existing content).

There is an equivalent method `ReadAllLines()` which can read each line into an array of strings for further processing.

Other methods provided by the `File` class include:

- `ReadAllText()`: the opposite to `WriteAllText()`
- `Create()`: Creates a file, returning a `FileStream`
- `Delete()`: Deletes a file
- `Open()`: Opens a file for access with specified `FileMode`` i.e. read, write or append
- `Close()`: Closes a file.  If a file has been opened, it must always be closed.
- `Exists()`: Determines whether the file exists, returns a Boolean
- `Copy()`:  Copies an existing file to a new file specified in the second parameter
- `Move()`: Moves a file to a new location, or file
