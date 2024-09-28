---
title: Programming Task - The Caesar Cipher
---

# {{ title }} 

!!! note "From the syllabus"
    AQA: Understand what is meant by encryption and be able to define it. (3.5.6.8/4.5.6.10): Be familiar with Caesar cipher and be able to apply it to encrypt a **plaintext** message and decrypt a **ciphertext.** Be able to explain why it is easily cracked.
    
    - Encryption is the method by which information is converted into secret code that hides the information's true meaning. In computing, unencrypted data is also known as plaintext, and encrypted data is called ciphertext. The formulas used to encode and decode messages are called encryption algorithms, or ciphers.

Encryption is is the term used to converting information into an alternative, scrambled form so that only those who know how to unscramble the data can read the message.  The process takes the original message, the __plaintext__ and applies an algorithm to each character in the text producing an alternative version of the message, the __ciphertext__.  

Encryption has been used since earliest times and one of these early methods is the __Caesar Cipher__.  It is a type of __substitution cipher__ where each letter of the plaintext is replaced by another letter some number of positions further on (or back) in the alphabet.  If the shift value was 3 the letter 'a' would be replaced by 'd'.  It's a rudimentary encryption method and very easy to decrypt (though in Caesar's day it might have been effective as most of his enemies could not read).


__The Problem__ Write a program to encrypt a string. A simple "Caesar shift": each character in the plaintext is replaced by the one shift places from it in the alphabet eg if shift=3 then 'a' is replaced by 'd', 'b' by 'e', ..., 'x' by 'a', 'y' by 'b', 'z' by 'c'.

Here is an _incomplete_ Caesar Shift program.

```cs
using System;
using System.Text;

namespace CaesarCipher
{
    class CaesarCipher
    {
        static void Main(string[] args)
        {
            int shift;
            char letter;
            string plaintext;
            string ciphertext = "";

            Console.Clear();
            // get the message
            Console.Write("Enter your message to be encrypted: ");
            plaintext = Console.ReadLine();               
            
            Console.Write("Enter the shift value (key): ");
            shift = Convert.ToInt32(Console.ReadLine());
            
            // encrypt it
            // outer loop: step through the plaintext, one character at a time
            for (int i = 0; i < plaintext.Length; i++) 
            {
                letter = plaintext[i];       
                for (int n = 0; n < shift; n++) // inner loop
                {
                    letter++;    // move the ith letter on to the next in the ASCII table, 
                }
                ciphertext += letter;  //This appends the shifted letter to the ciphertext
            }

            // output the encrypted version
            Console.WriteLine("The encrypted message is " + ciphertext);
            Console.ReadKey();
        }
    }
}
```

The program does not work correctly.  This raises the question of how we can test a program.

There are many different ways of testing an algorithm or program. Here are two of them for you to try on the Caesar Shift program:

### Dry-run testing (also called hand-tracing)

We met trace tables in the previous chapter.  Tracing an algorithm using this method can help reveal problems with algorithms as in this case with the Caesar Shift program:

Start with a table, with a column for each variable in the program, like this:

| i     |   N   |   plaintext   |
|-------|-------|---------------|
|       |       |               |
|       |       |               |

The order of columns should match the order in which the variables are changed in the for loops: this makes the table easier to complete and understand.

To carry out a test, choose an initial value for the plaintext: say "cat" and a value for shift, say $3$. Now work systematically through the code, recording the values of each variable as they change

| i     |   N   |   plaintext   |
|-------|-------|---------------|
|       |       |   cat |
|    1   |  1     |   dat            |
|    1   |  2     |   eat            |
|   1   |   3   |   fat |
|   2   |   1   |   fbt |
|   2   |   2   |   fct |
|   2   |   3   |   fdt |
|   3   |   1   |   fdu |
|   3   |   2   |   fdv |
|   3   |   3   |   fdw |

The function has passed this test, though that doesn't mean that it will work __for all values of plaintext__.

1. Dry run the code, using a start value for the plaintext of "axe".  Follow the code literally, do not make any assumptions
2. What change is required to correct the errors you found (NB.  You will find an error!)
3. Implement the change to the code

### Functional Testing

In contrast to dry-run testing, functional testing __does__ require a computer, but __not__ access to the code, only the final executable and the specification of what the program is supposed to do. It is often called __black-box testing__ because the tester sees the program as a black box and cannot see the internal workings.

The aim of functional testing is to determine whether the program does what it's supposed to, for as wide a range of inputs _as possible_. Notice the last two words in the previous sentence. For most programs it is __impossible__ to test that they work correctly for all possible inputs, because there is an infinite number of them. So, the tester has to design tests for all _reasonably likely_ inputs: this includes those resulting from user error and ignorance!

Some general principles can be applied when designing data for functional tests:

- All users make mistakes
- Programs are most likely to fail with extreme data
- Programmers most often make mistakes at data boundaries

Applying these principles to the Caesar Shift program:

- __User errors__: non-numeric data for the shift value: eg "5q", non-integer data: eg 3.5
- __Extreme data__: 0 or very large numbers for the shift value, an empty or very long string for plaintext
- __Boundary data__: For the shift value: 0 (the minimum acceptable value), -1 (only just unacceptable)

In order to choose test data correctly it is essential that the tester has a precise specification for the program. That is, what data should it accept and, how should it respond to invalid data, and what are the expected outputs for a range of valid data?

Functional, black-box testing can be recorded using a table like this:

| Test \# | Test Data | Explanation | Expected result | Actual result | Pass/Fail |
| --------|-----------|-------------|-----------------|---------------|-----------|
|1        | 3, "cat"  |Valid data | outputs "fdw"   | "fdw"           |   Pass      |
|2          |q, "cat" |Invalid data |Fatal error    |               |   |
|3          |3, "xyz"   |Boundary data|Outputs "abc"|   | |
|4 ||||||

4. Add additional, appropriate tests to the above table for the Caesar Cipher program.
5. Implement those changes in your code
