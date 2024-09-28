---
title: Appendix 2 - Sample solutions
---

# {{ title }}

This appendix contains sample code listings for the exercises referenced in the text.  They are to be regarded as examples of possible solutions and not definitive.  When programming a solution there is often more than one way to arrive at a workable answer.

Solutions do not, or rarely, include concepts covered in later chapters.

## Chapter 1

**Write a program to calculate the area of a triangle**

```cs
using System;

namespace triangle
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Calculate the area of a triangle");

            int height;
            int width;
            double area;

            Console.Write("Enter the height of the triangle > ");
            height = Convert.ToInt32(Console.ReadLine());
            Console.Write("Enter the width of the triangle  > ");
            width = Convert.ToInt32(Console.ReadLine());

            area = height * width;

            Console.WriteLine($"The triangle's area is {area} units");

            Console.WriteLine("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 2

**Write a program that converts a temperature in degrees Fahrenheit into Centigrade/Celsius**

```cs
using System;

namespace TempConv
{
    class Program
    {
        static void Main(string[] args)
        {
            double fahrTemp;
            double celTemp;

            Console.Clear();
            Console.WriteLine("Temperature Conversion");

            Console.Write("Enter a temperature in degrees Fahrenheit > ");
            fahrTemp = Convert.ToDouble(Console.ReadLine());

            celTemp = (fahrTemp - 32) * 5/9;

            Console.WriteLine($"{fahrTemp} degrees F is {celTemp} degrees C");

            Console.WriteLine("Press any key to continue ...");
            Console.ReadKey();
        }
    }
}
```

**Declare two variables of type ```int```.  Assign them the values $8$ and $5$.  Swap their values and print them to the screen**

```cs
using System;

namespace swap
{
    class Program
    {
        static void Main(string[] args)
        {
            int first = 8;
            int second = 5;

            Console.Clear();
            Console.WriteLine("Simple swap");

            Console.WriteLine($"Before the swap:  First = {first}, Second = {second}");

            int Temp = first;
            First = second;
            second = Temp;

            Console.WriteLine($"After the swap:   First = {first}, Second = {second}");

            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

**Write a program which inputs the length and width of a rectangular garden. Calculate the area of the garden and the cost of turfing a lawn if a 1m unturfed border is around the perimeter of the garden. Assume the cost of turf is 10 per square metre**

```cs
using System;

namespace Turf
{
    class Program
    {
        static void Main(string[] args)
        {
            const int costPerSqMetre = 10;
            double length;
            double width;
            double lawnArea;
            double cost;

            Console.WriteLine("How much to turf a lawn?");

            Console.Write("Enter length of the lawn > ");
            length = Convert.ToDouble(Console.ReadLine());
            Console.Write("Enter width of the lawn  > ");
            width = Convert.ToDouble(Console.ReadLine());

            lawnArea = (length - 2) * (width-2);
            cost = lawnArea * costPerSqMetre;

            Console.WriteLine($"Total cost = ${cost}");

            Console.Write("Press any key to quit ...");
            Console.ReadKey(); 
        }
    }
}
```

## Chapter 3

**Displaying a pack of cards**

To avoid repetition in the code, this solution uses two methods (see Chapter 9) to return a string representation of the playing card, ```GetRankAsString()``` and ```GetSuitAsString()```.

```cs
using System;

namespace cards
{
    class Program
    {
        static void Main(string[] args)
        {
            string rank = "";
            string suit = "";

            Console.Clear();
            Console.WriteLine("Cards Complete");

            // Pick a card
            Console.Write("Enter a number (1-52) to pick a card from the deck, or 0 to select a random card > ");

            int myCardNum = Convert.ToInt32(Console.ReadLine());

            if (myCardNum == 0)
            {
                Random rnd = new Random();
                myCardNum = rnd.Next(52);
            }

            rank = GetrankAsString(m - 1);          // -1 to ensure first card can be selected
            suit = GetsuitAsString(m);    
            Console.WriteLine($"Your card is the {rank} of {suit}");
            

            Console.WriteLine("The whole deck ...");
            for (int i = 0; i < 52; i++)
            {
                //rankNum = (i % 13) + 1;
                //suitNum = i / 13;
                rank = GetrankAsString(i);
                suit = GetsuitAsString(i);    
                Console.WriteLine($"{rank} of {suit}");
            }

            Console.WriteLine("Press any key to continue ...");
            Console.ReadKey();
        }

        static string GetrankAsString(int rank)
        {
            int rankNum = (rank % 13) + 1;
            string rankStr = "";
            switch (rankNum)
            {
                case 1:
                    rankStr = "Ace";
                    break;
                case 2:
                    rankStr = "Two";
                    break;
                case 3:
                    rankStr = "Three";
                    break;
                case 4:
                    rankStr = "Four";
                    break;
                case 5:
                    rankStr = "Five";
                    break;
                case 6:
                    rankStr = "Six";
                    break;
                case 7:
                    rankStr = "Seven";
                    break;
                case 8:
                    rankStr = "Eight";
                    break;
                case 9:
                    rankStr = "Nine";
                    break;
                case 10:
                    rankStr = "Ten";
                    break;
                case 11:
                    rankStr = "Jack";
                    break;
                case 12:
                    rankStr = "Queen";
                    break;
                case 13:
                    rankStr = "King";
                    break;
            }
            return rankStr;
        }

        static string GetsuitAsString(int suit)
        {
            string suitStr = "";
            int suitNum = suit / 13;
            if (suitNum == 0)
                suitStr = "\u2663";      // club
            else if (suitNum == 1)
                suitStr = "\u2666";   // diamond
            else if (suitNum == 2)
                suitStr = "\u2665";      // heart
            else if (suitNum == 3)
                suitStr = "\u2660";     // spades
            else
                suitStr = "ERROR";
            return suitStr;
        }
    }
}
```

**Using a bitwise operator write a program that checks if an integer is odd or even**

```cs
using System;

namespace oddOrEven
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Odd Or Even");

            Console.Write("Enter a number > ");
            int value = Convert.ToInt32(Console.ReadLine());

            if ((value & 1) == 1)
                Console.WriteLine($"{value} is odd");
            else
                Console.WriteLine($"{value} is even");
            Console.WriteLine("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Write a program that takes as input a four digit number and calculates the sum of the digits**

```cs
using System;

namespace sumOfDigits
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Sum Of Digits");

            Console.Write("Enter a number with 4 digits only > ");
            string numString = Console.ReadLine();

            int sum = 0;
            sum += Convert.ToInt32(numString[0]) - '0';     // input is in ASCII, need to subtract 48, or '0'
            sum += Convert.ToInt32(numString[1]) - 48;
            sum += Convert.ToInt32(numString[2]) - '0';
            sum += Convert.ToInt32(numString[3]) - '0';

            Console.WriteLine($"Sum is {sum}");

            sum = 0;

            // alternatively a loop would help
            for (int i = 0; i < numString.Length; i++)
                sum += numString[i] - 48;
            Console.WriteLine($"The looped sum is also {sum}");

            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 4

**Returning the minimum and maximum of two values (not conditionals)**

```cs
using System;

namespace max
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Max without an IF");

            int first = 8;
            int second = 5;

            Console.WriteLine($"Smaller of ({first},{second}) is {Math.Min(first,second)}");
            Console.WriteLine($"Larger of ({first},{second}) is {Math.Max(first,second)}");

            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Printing in columns**

```cs
using System;

namespace columns
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Printing in columns");
            
            int first = 0xFF;
            double second = 245.7689;
            double third = -123.456;
            Console.WriteLine($"|0x{first,-8:X}|{second,-10:f2}|{third,-10:f2}|");

            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 5: Making Decisions

**Rock, Paper, Scissors**

```cs
using System;

namespace rockPaperScissors
{
    class Program
    {
        static void Main(string[] args)
        {
            string computerObject = "";
            int computerChoice = 0;
            bool computerWins = false;

            Random random = new Random();

            Console.Clear();
            Console.Write("Enter your choice r(ock), p(aper), s(cissors): ");
            string userObject = Console.ReadLine();

            char userObjectFirst = userObject[0];               // get first character of user choice
            computerChoice = random.Next(3);                    // get random value, 0..2, for selecting computer choice

            switch (computerChoice)
            {
                case 0:
                    computerObject = "rock";
                    break;
                case 1:
                    computerObject = "paper";
                    break;
                case 2:
                    computerObject = "scissors";
                    break;
            }

            char computerObjectFirst = computerObject[0];
            Console.WriteLine("Computer chose: " + computerObject);

            if (String.Equals(computerObjectFirst, userObject))
            {
                Console.WriteLine("It's a draw!"); 
            }
            else
            {
                if (computerObjectFirst == 'r' && userObjectFirst == 'p') 
                {
                    computerWins = false;
                }
                else if (computerObjectFirst == 'r' && userObjectFirst == 's') 
                {
                    computerWins = true;
                }
                else if (computerObjectFirst == 's' && userObjectFirst == 'r') 
                {
                    computerWins = false;
                }
                else if (computerObjectFirst == 's' && userObjectFirst == 'p') 
                {
                    computerWins = true;
                }
                else if (computerObjectFirst == 'p' && userObjectFirst == 'r') 
                {
                    computerWins = true;
                }
                else if (computerObjectFirst == 'p' && userObjectFirst == 's') 
                {
                    computerWins = false;
                }
               
                if (computerWins == true)
                {
                    Console.WriteLine("Computer has won!");
                }
                else
                {
                    Console.WriteLine("You have won!");
                }
            }

            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Leap Year**

```cs
using System;

namespace leapyear
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Leap year");

            int year;
            bool leapyear = false;

            Console.Write("Enter a valid year: ");
            year = Convert.ToInt32(Console.ReadLine());

            if ((year % 4 == 0) && (year % 100 != 0))
            {
                leapyear = true;
            }
            else if (year % 100 == 0)
            {
                if (year % 400 == 0)
                {
                    leapyear = true;
                }
            }

            if (leapyear)
            {
                Console.WriteLine(year + " is a leap year");
            }
            else
            {
                Console.WriteLine(year + " is not a leap year");
            }
        }
    }
}
```

**Roots of a quadratic equation**

```cs
using System;

namespace quadratic
{
    class Program
    {
        static void Main(string[] args)
        {
            int a, b, c;
            double discriminant;
            double x1, x2;


            Console.Clear();
            Console.WriteLine("Quadratic Equation Solver");

            Console.Write("Enter first value (a) > ");
            a = Convert.ToInt32(Console.ReadLine());
            Console.Write("Enter second value (b) > ");
            b = Convert.ToInt32(Console.ReadLine());
            Console.Write("Enter third value (c) > ");
            c = Convert.ToInt32(Console.ReadLine());

            discriminant = Math.Pow(b,2) - (4 * a * c);

            if (a == 0)
            {
                Console.WriteLine("Not quadratic");
            }
            if (discriminant == 0)
            {
                x1 = -b/(2.0*a);
                x2 = x1;
                Console.WriteLine($"Both roots are equal: {x1}");
            }
            else if (discriminant > 0)
            {
                Console.WriteLine("There are two real roots");
                x1 = (-b + Math.Sqrt(discriminant))/(2 * a);
                x2 = (-b - Math.Sqrt(discriminant))/(2 * a);
                Console.WriteLine($"First root = {x1}");
                Console.WriteLine($"Second root = {x2}");
            }
            else
            {
                Console.WriteLine("There are no roots");
            }

            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 6: Iteration

**Display table of ASCII codes (32-126)**

```cs
using System;

namespace ascii
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("ASCII Table of printable characters\n");

            Console.WriteLine("+----------+------------+-----------+");
            Console.WriteLine("|  Decimal |     Hex    | Character |");
            Console.WriteLine("+----------+------------+-----------+");
            for (int i = 32; i < 126; i++)
            {
                Console.WriteLine($"|{i,9} | {i,10:X} | {(char)i,10}|");
            }
            Console.WriteLine("+----------+------------+-----------+");
            Console.WriteLine("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

**Fizz Buzz**

```cs
using System;

namespace fizzbuzz
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Fizz Buzz");

            for (int i = 1; i <= 100; i++)
            {
                if ((i % 5 == 0) && (i % 3 == 0))
                {
                    Console.WriteLine(i + " FIZZ BUZZ");
                    
                }
                else if (i % 3 == 0)
                {
                    Console.WriteLine(i + " FIZZ");
                }
                else if (i % 5 == 0)
                {
                    Console.WriteLine(i + " BUZZ");
                }
                else
                {
                    Console.WriteLine(i);
                }
            }
            Console.WriteLine("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Sum the first $N$ numbers of the Fibonacci series**

```cs
using System;

namespace fibonacci
{
    class Program
    {
        static void Main(string[] args)
        {
            int number;
            int sum = 0;
            int temp = 0;
            int first = 0;
            int next = 1;
            Console.Clear();
            Console.WriteLine("sum of Fibonacci numbers to N");

            Console.Write("Enter a number: ");
            number = Convert.ToInt32(Console.ReadLine());
            
            Console.Write($"[ {temp} ");
            for (int i = 1; i < number; i++)
            {
                first = next;
                next = temp;
                temp = first + next;
                Console.Write($"{temp} ");
                sum += temp;
            }
             
            Console.WriteLine("]");
            Console.WriteLine($"The sum of the first {number} numbers in Fibonacci sequence is {sum}");

            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 7:  Arrays

**Initialise an array with square numbers**

```cs
using System;

namespace squareArray
{
    class Program
    {
        static void Main(string[] args)
        {
            const int LENGTH = 20;
            int[] myArray = new int[LENGTH];

            Console.Clear();
            Console.WriteLine("Initialising an array with square numbers");

            for (int i = 0; i < LENGTH; i++)
            {
                myArray[i] = i * i;
            }

            foreach(int element in myArray)
            {
                Console.Write($"{element} ");

            }
            Console.WriteLine();
            
            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

**Searching for an element in an array**

```cs
using System;

namespace randomSearch
{
    class Program
    {
        static void Main(string[] args)
        {
            const int MIN = 0;
            const int MAX = 100;
            const int NUM_ELEMENTS = 20;

            int[] myArray = new int[NUM_ELEMENTS];
            int searchKey;
            bool found = false;
            Random rnd = new Random();
            
            Console.Clear();
            Console.WriteLine("Searching for a value in an array");

            // initialise array
            for (int i = 0; i < myArray.Length; i++)
            {
                myArray[i] = rnd.Next(MIN,MAX);
            }

            // ask use for a search value/key
            Console.Write("Enter a value to find: ");
            searchKey = Convert.ToInt32(Console.ReadLine());

            foreach (int e in myArray)
            {
                //Console.Write($"{e} ");           // testing
                if (e == searchKey)
                {
                    found = true;
                    break;                          // only need first instance
                }
            }

            // print result
            if (found)
            {
                Console.WriteLine($"\nYour value {searchKey} was found!");
            }
            else
            {
                Console.WriteLine($"\nYour value {searchKey} could not be found");
            }
            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

**Merge two arrays**

```cs
using System;

namespace merge
{
    class Program
    {
        static void Main(string[] args)
        {
            const int SIZE = 10;
            const int MIN = 0;
            const int MAX = 100;
            int[] firstArray = new int[SIZE];
            int[] secondArray = new int[SIZE];
            int[] mergedArray = new int[SIZE * 2];

            Console.Clear();
            Console.WriteLine("Merge two arrays");
            Random rnd = new Random();
            // initialise starting arrays with random values
            int i;
            for (i = 0; i < SIZE; i++)
            {
                firstArray[i] = rnd.Next(MIN,MAX);
                SecondArray[i] = rnd.Next(MIN,MAX);
            }

            // merge into a new array
            for (i =0; i < SIZE; i++)
            {
                mergedArray[i] = firstArray[i];
            }
            for(int j = 0; j < SIZE; j++)
            {
                mergedArray[i] = SecondArray[j];        // note value for i
                i++;
            }
            
            Array.Sort(mergedArray);

            // Print arrays
            Console.WriteLine("nFirst array");
            // first array
            foreach(int e in firstArray)
            {
                Console.Write($"{e} ");
            }
            Console.WriteLine("\nSecond array");
            foreach(int e in SecondArray)
            {
                Console.Write($"{e} ");
            }
            Console.WriteLine("\nMerged array");
            // print merged array
            foreach(int el in mergedArray)
            {
                Console.Write($"{el} ");
            }

            Console.WriteLine();
            Console.Write("Press any key to quit ...");
            Console.ReadKey();
        }
    }
}
```

**Multiplication table**

```cs
using System;

namespace multiplicationTable
{
    class Program
    {
        static void Main(string[] args)
        {
            const int START = 1;
            const int END = 12;
            Console.Clear();
            Console.WriteLine("Multiplication Table");
            
            // header row
            Console.Write($"      ");
            for(int i = 1; i <= END; i++)
            {
                Console.Write($" {i,5} ");
            }
            // multiplication table
            for (int row = START; row <= END; row++)
            {
                Console.Write($"{row,3} | ");
                for (int col = START; col <= END; col++)
                {
                    Console.Write($" {row * col,5} ");
                }
                Console.WriteLine();
            }
        }
    }
}
```

## Chapter 8: Strings, Encryption and Testing

**Searching for keywords**

```cs
using System;

namespace stringChecking
{
    class Program
    {
        static void Main(string[] args)
        {
            string str = "I am going to check every word of this sentence for the keywords";
            string[] words;

            Console.Clear();
            Console.WriteLine("String Checking");
            
            words = str.Split(' ');

            foreach(string w in words)
            {
                if ((w == "check") || (w == "word") || (w == "sentence"))
                {
                    Console.ForegroundColor = ConsoleColor.DarkRed;
                    Console.Write($"{w} ");
                    Console.ForegroundColor = ConsoleColor.Black;
                }
                else
                {
                    Console.Write($"{w} ");
                }
            }

            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Counting characters**

```cs
using System;

namespace countCharacters
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] charFrequency = new int[26];
            string inputString;

            Console.Clear();
            Console.WriteLine("Counting characters");

            Console.Write("Enter a string: ");
            inputString = Console.ReadLine();
            inputString = inputString.ToUpper();

            for(int i = 0; i < inputString.Length; i++)
            {
                // only counting letters, not punctuation
                if ((inputString[i] >= 'A') && (inputString[i] <= 'Z'))
                {
                    charFrequency[inputString[i]-'A']++;
                }
            }

            // print, getting the character represented by each index followed by the value
            for (int i = 0; i < charFrequency.Length; i++)
            {
                Console.Write((char)(i+65) + ": " + charFrequency[i] + " ");
            }
            
            Console.WriteLine();
            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

**Screen scraping**

```cs
using System;

namespace screenScrape
{
    class Program
    {
        static void Main(string[] args)
        {
            string html = "<html><head><title>News</title></head><body><p>Getting proficient with C# requires <b>practice</b>, <b>practice</b> and more <b>practice</b></p></body></html>";
            string output = String.Empty;
            bool openingTagMode = false;

            Console.Clear();
            Console.WriteLine("Screen scraping");

            for (int i = 0; i < html.Length; i++)
            {
                if (html[i] == '<')
                {
                    openingTagMode = true;
                }
                else if (html[i] == '>')
                {
                    openingTagMode = false;
                }
                if ((!openingTagMode) && (html[i] != '>'))
                {
                    output += html[i];
                }
            }
            Console.WriteLine(output);
            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 9 - Methods

**Calculator**

```cs
using System;

namespace calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            int menuOption;
            
            Console.Clear();
            Console.WriteLine("Welcome to the calculator program\n");

            do
            {
                // Ask the user for two number and store them as floats
                Console.Write("Enter the first number: ");
                float number1 = GetFloat();
                //float number1 = float.Parse(Console.ReadLine());

                Console.Write("Enter the second number: ");
                float number2 = GetFloat();
                //float number2 = float.Parse(Console.ReadLine());

                // Output the menu options
                Console.WriteLine("\nEnter the menu number of the calculation to perform: ");
                Console.WriteLine("1 - Addition");
                Console.WriteLine("2 - Subtraction");
                Console.WriteLine("3 - Multiplication");
                Console.WriteLine("4 - Division");
                Console.WriteLine("5 - Modulus");
                Console.WriteLine("6 - Floor Division");
                Console.WriteLine("7 - QUIT\n");

                // Ask for the menu option
                menuOption = GetInt();

                switch (menuOption)
                {
                    case 1:
                        Console.WriteLine($"The result = {Addition(number1, number2)}");
                        break;
                    case 2:
                        Console.WriteLine($"The result = {Subtraction(number1, number2)}");
                        break;
                    case 3:
                        Console.WriteLine($"The result = {Multiplication(number1, number2)}");
                        break;
                    case 4:
                        Console.WriteLine($"The result = {Division(number1, number2)}");
                        break;
                    case 5:
                        Console.WriteLine($"The result = {Modulus(number1,number2)}");
                        break;
                    case 6:
                        Console.WriteLine($"The result = {Floor(number1, number2)}");
                        break;
                }
            } while ((menuOption >= 1) && (menuOption <= 6));
        }

        // The addition procedure has two floats as parameters, adds them together and outputs the result
        static float Addition(float num1, float num2)
        {
            return num1 + num2;
        }

        static float Subtraction(float num1, float num2)
        {
            return num1 - num2;
        }

        static float Multiplication(float num1, float num2)
        {
            return num1 * num2;
        }

        static float Division(float num1, float num2)
        {
            if (num2 != 0)
                return num1 / num2;
            else
                return -1;
        }

        static float Modulus(float num1, float num2)
        {
            return num1 % num2;
        }

        static int Floor(float num1, float num2)
        {
            //Console.WriteLine(Math.Floor(Division(num1,num2)));
            if (((num1 < 0) ^ (num2 < 0)) && (num1 % num2 != 0))
            {
                return Convert.ToInt32(num1/num2);
            }
            else
            {
                return Convert.ToInt32(num1 / num2)-1;
            }
        }
        static float GetFloat()
        {
            string input = Console.ReadLine();
            float result = 0f;
            while (!float.TryParse(input, out result))
            {
                Console.WriteLine("That is not a valid number, please try again.");
                Console.Write("Enter number > ");
                input = Console.ReadLine();
            }
            return result;
        }

        static int GetInt()
        {
            string input = Console.ReadLine();
            int result = 0;
            while (!Int32.TryParse(input, out result))
            {
                Console.WriteLine("That is not a valid number, please try again.");
                Console.Write("Enter number > ");
                input = Console.ReadLine();
            }
            return result;
        }
    }
}
```

**Secret Word**

```cs
using System;

namespace secretWord
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialise the variables and secret word
            int menuOption;
            string secretWord = "Computer";

            do
            {
                Console.Clear();
                // Output the menu
                Console.WriteLine("\nWelcome to the guessing program menu - choose your option:");
                
                menuOption = GetMenuOption();
                // Choose a task depending on the menu option 
                switch (menuOption)
                {
                    case 1:
                        // Change the secret word
                        secretWord = ChangeSecretWord();
                        break;
                    case 2:
                        // Guess the secret word
                        GuessSecretWord(secretWord);
                        break;
                    case 3:
                        // Quit the program
                        Exit();
                        break;
                    default:
                        Console.WriteLine("Invalid menu choice");
                        break;
                }
            }
            while (menuOption >= 1 && menuOption <= 2);
        }

        static int GetMenuOption()
        {
            Console.WriteLine("MAIN MENU\n");
            Console.WriteLine("1 - Change the secret word");
            Console.WriteLine("2 - Make a guess");
            Console.WriteLine("3 - Quit");
            Console.Write("> ");

            // Ask the user for the menu number
            return (GetInt());
        }

        static string ChangeSecretWord()
        {
            Console.WriteLine("What is the new secret word?");
            Console.Write("> ");
            return Console.ReadLine();
        }

        static void GuessSecretWord(string secretWord)
        {
            Console.Write("Guess the secret word: ");
            string guess = Console.ReadLine();

            // Check whether the word entered was the secret word - ignoring case
            if (guess.ToUpper() == secretWord.ToUpper())
            {
                Console.WriteLine("Well done - you have guessed the secret word!");
            }
            else
            {
                Console.WriteLine("Sorry, that is not the secret word");
            }
            PressAnyKey();
        }

        static void Exit()
        {
            Console.WriteLine("Thank you for playing secret word");
            Environment.Exit(0);
        }

        static void PressAnyKey()
        {
            Console.Write("Press any key to continue...");
            Console.ReadKey();
        }
        static int GetInt()
        {
            string input = Console.ReadLine();
            int result = 0;
            while (!Int32.TryParse(input, out result))
            {
                Console.WriteLine("That is not a valid option, please try again.");
                Console.Write("> ");
                input = Console.ReadLine();
            }
            return result;
        }
    }
}
```

**Binary to decimal 'bitwise' converter**

```cs
using System;

namespace binaryToDecimal
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Binary to decimal bitwise converter");
            string binary = GetBinaryValue();
            int result = ConvertBinary(binary);
            OutputResult(result);
            Exit();
        }

        static string GetBinaryValue()
        {
            Console.WriteLine("Enter binary number to be converted");
            Console.Write("> ");
            return Console.ReadLine();
        }

        static int ConvertBinary(string binary)
        {
            int column = 128;
            int result = 0;
            for (int i = 0; i < binary.Length; i++)
            {                
                int bitValue = ConvertBit(binary[i],column);
                column /= 2;
                result += bitValue;
            }
            return result;
        }
        static int ConvertBit(char bit, int col)
        {
            int result = 0;
            if (bit == '1')
            {
                result += col;
            }
            return result;
        }

        static void OutputResult(int result)
        {
            Console.WriteLine(result);
        }
        static void Exit()
        {
            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }
    }
}
```

## Chapter 10: Recursion

**Length of a string**

```cs
using System;

namespace stringLength
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Length of a string - recursively");

            Console.Write("Enter a string: ");
            string input = Console.ReadLine();
            Console.WriteLine($"The length of \"{input}\" is {GetLength(input)}");
            
            Console.Write("Press any key to quit...");
            Console.ReadKey();
        }

        static int GetLength(string input)
        {
            if (input == string.Empty)
            {
                return 0;
            }
            else
            {
                return GetLength(input.Substring(1)) + 1;
            }
        }
    }
}
```

**Calculate power**

```cs
using System;

namespace power
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Clear();
            Console.WriteLine("Calculate Power of value recursively");

            Console.WriteLine(Convert.ToInt32(Power(2,8)));         // 256

            Console.Write("Press any key to continue...");
            Console.ReadKey();
        }

        static int Power(int num, int exponent)
        {
            if (exponent == 0)
                return 1;
            else
                return num * Power(num, exponent-1);
        }
    }

}
```
