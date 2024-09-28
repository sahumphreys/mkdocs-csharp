# Appendix 6: Unit Testing

Testing software can be a real challenge as there are potentially lots of different ways to test the correct working of the code we write.  This appendix looks at the process of creating __unit tests__ in Visual Studio Code.  It is a mere glimpse into the world of creating unit tests, a topic for further exploration and self-study.

Testing is not a trivial process, there are lots of different test cases but thinking how your code might fail, the errors that could be generated, is good software development practice.  

## What is a Unit Test?

A __Unit Test__ is code written to test individual parts of code from our main project, usually methods.  The test cases are written as methods (functions) that evaluate whether a returned value is the expected value or something unexpected.  Unit testing will not guarantee the absence of bugs, the test will only be as good as the code written in the unit test but thinking about how a method might fail is good practice and the writing of unit tests encourages that thinking.

Think of the unit test as another tool for testing, it should not replace pen and paper and tracing but automating aspects of testing can be really useful. Further, plan the tests before you code.

You can read more about unit testing on [Wikipedia](https://en.wikipedia.org/wiki/Unit_testing).

## Unit Testing with Visual Studio Code

Install the extension .Net Core Test Explorer

Adds a new icon to the sidebar, Testing

We'll need a separate library of code for the unit tests and we'll use another library of code to which we'll apply the tests.

First we'll create the library of code to test, a trivial set of methods to carry out basic mathematical operations.  At the terminal enter the following command in a fresh directory:

```dotnet new classlib -n MyMaths```

Then in the ```Class1.cs``` code file add the following:

~~~~~cs
using System;

namespace MyMaths
{}
    public class Class1
    {
        public static int Add(int first, int second)
            return first + second;
        }
    }
}
~~~~~

Make sure the project builds with the command ```dotnet build```.

We'll now add a test library for this method.  Back at the terminal enter:

```dotnet new xunit -n MyMathsTests```

In the ```Unittest1.cs``` file insert the following test code:

~~~~~cs
using System;
using Xunit;
using MyMaths;

namespace MyMathsTests
{
    public class UnitTest1
    {
        [Fact]
        public void Test1()
        {
            var actual = Class1.Add(2,3);
            Assert.Equal(5, actual);
        }
    }
}
~~~~~

Check this builds too with the ```dotnet build``` command.  (It should as we've not altered the boilerplate code)

If you click on the Testing icon in the VSCode sidebar a message will appear saying no tests have been found.

At the Terminal go into the root directory of the project and create a reference between the two projects:

```dotnet add .\MyMathsTests\MyMathsTexts.csproj reference .\MyMaths\MyMaths.csproj```

Now, clicking the Testing icon in the sidebar the tests in the test library will be displayed, by name.  Clicking the "Play" button will now run the tests.  If is passes a green tick will be shown against the name of the test.

Try adding a second test, using the same format but use data you'd expect to fail.  Running the ```dotnet test``` command again will show one test has passed but another failed (as you'd expect).
