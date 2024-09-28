---
title: Extended Theory - Input/Output
---

# {{ title }}

One of the most important roles of an operating system (OS) is to manage the various devices connected to a computer, such as the mouse, keyboard, screen, touchpad, storage devices, printers, and network connections. These devices can either provide input to the system, receive output from the system, or perform both functions. The OS relies on I/O controllers to handle data entering and leaving the system, with the I/O subsystem of the OS packaging the data appropriately before passing it on to the controller.

C# includes several classes designed to handle I/O operations from a variety of devices. This chapter has primarily focused on the `System.Console` class for reading from and writing to the console using the default input and output devices (keyboard and screen). Other classes, such as `System.IO`, are used for file handling, while `System.Net` is employed for network communications. We will explore these namespaces in later chapters.

We can also utilize additional classes to gather information about our computer system, such as `System.Environment` and `System.Management`. For instance, to determine which operating system you are using, you can run:

```cs
Console.WriteLine(System.Environment.OSVersion);
```

## Additional System Information

Here’s a sample program that demonstrates how to access various system properties:

```cs
static void Main(string[] args)
{
    Console.WriteLine($"Operating system: {System.Environment.OSVersion}");
    Console.WriteLine($"64-bit OS: {System.Environment.Is64BitOperatingSystem}");
    Console.WriteLine($"Machine Name: {System.Environment.MachineName}");
    Console.WriteLine($"Current Directory: {System.Environment.CurrentDirectory}");
    
    string[] myDrives = Environment.GetLogicalDrives();
    Console.Write("Connected logical drives: ");
    foreach (string drive in myDrives)
    {
        Console.Write(drive + " ");
    }
    
    Console.WriteLine($"\nNumber of processors: {System.Environment.ProcessorCount}");
    Console.WriteLine($"User name: {System.Environment.UserName}");
    
    Console.ReadKey();
}
```

## Using System.Management for Detailed Information

The `System.Management` class can provide in-depth details about your CPU:

```cs
using System;
using System.Collections.Generic;
using System.Management;

namespace ViewAssembly
{
    class Program
    {
        static void Main(string[] args)
        {
            ManagementClass myCPU = new ManagementClass("Win32_Processor");
            ManagementObjectCollection myCPUCollection = myCPU.GetInstances();
            PropertyDataCollection pdc = myCPU.Properties;
            Dictionary<string, object> myCPUResults = new Dictionary<string, object>();

            foreach (var obj in myCPUCollection)
            {
                foreach (var prop in pdc)
                {
                    myCPUResults.Add(prop.Name, obj.Properties[prop.Name].Value);
                }
            }

            foreach (var result in myCPUResults)
            {
                Console.WriteLine($"{result.Key}: {result.Value}");
            }
            Console.ReadLine();
        }
    }
}
```

This example uses more advanced C# features than we have covered so far, but it illustrates the capabilities available for exploring the architecture of your computer system. By reading the code and comparing it with the output, you should gain insights into what the code is accomplishing.

!!! note
    To try out this last example in Visual Studio, a **reference** needs to be added. Right-click on "References" in the Solution Explorer window, select "Add Reference," and then choose "System.Management" from the list of "Assemblies."
