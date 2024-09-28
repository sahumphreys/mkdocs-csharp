## Questions

- Open Visual Studio and create a new project for the __Hello World__ application  
- Enter the source code from the "Hello World" example:

    ```cs
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello, World!);
                Console.ReadKey();
            }
        }
    }
    ```

- Compile and run
- Enhance the program to store your name in two variables, one for your first name and the other your last name
- Print your name to the screen using these variables using each of the approaches suggested above.  Compile and run your program
- Study the following program, and answer the questions below:

    ```cs
    using System;

    namespace volume
    {
        class Program
        {
            static void Main(string[] args)
            {
                int length;
                int height;
                int width;
                int volume;

                Console.Clear();
                Console.Write("Enter length >");
                length = Convert.ToInt32(Console.ReadLine());
                Console.Write("Enter height > ");
                height = Convert.ToInt32(Console.ReadLine());
                Console.Write("Enter width > ");
                width = Convert.ToInt32(Console.ReadLine());

                volume = length * height * width;

                Console.WriteLine($"The volume of the box ({length}x{width}x{height}) is {volume}");
                Console.WriteLine("Press any key to quit ...");
                Console.ReadKey();
            }
        }
    }
    ```

     - What does the program do?
     - What does `Console.ReadLine()` do?
     - The variables, `length`, `width` etc are preceded by the keyword `int`.  What is the purpose of `int` in this context?
     - `Convert.ToInt32` is easy to read as "Convert to a 32 bit integer", but why is this necessary here?
     - What is the meaning of `=` in this context?
     - The "Hello World" program used `Console.WriteLine()`, this program uses `Console.Write()`.  What is the difference between them?

**Create a new project for the program in question 5, enter the code, compile and run.  Add a title to print to the screen and add comments to identify the following features of the source code:**

   - program header
   - statement to include a C\# namespace (library)
   - variable declarations
   - output statement
   - input statement
   - assignment statement

## Additional Exercises

1. Install Visual Studio Community Edition on a home computer  
2. Create a directory on your computer for your programming projects  
3. Set up a [GitHub account](https://github.com/join)  
4. Write a program to calculate the area of a triangle.  (The formula is $\frac{height \times base}{2}$)
5. Follow the [Microsoft "numbers in C#" tutorial](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/intro-to-csharp/numbers-in-csharp)
