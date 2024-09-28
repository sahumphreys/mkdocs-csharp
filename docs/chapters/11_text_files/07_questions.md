---
title: Questions
---

# {{ title }}

1. What is a file?
2. What is a text file?
3. How is the end of a line in a text file indicated?
4. Find three other control codes that can be embedded in a text file.  How are these used in C\#?
5. The `File` class in the namespace `System.IO` has a number of static methods.  Find the method that provides the following functionality:

    a. Copies one file to another
    b. Moves a file to another location
    c. Reads all lines in the file to a string
    d. Checks if a file exists in a given location
    e. Appends a string to a file
    f. Opens a FileStream with read/write access

6. Describe a `struct` to hold details of a __Book__, including the fields Title, Author, ISBN, PublicationYear and Price.
7. What exceptions might occur when opening a file programmatically?
8. Given the following recursive method, an input string of `"Peter,Jones,Marketing Manager,Ext. 788"` and the `,` as the delimiter, what will be the output on the screen:

    ```cs
    static void OutputCSVLines(string input, char delimiter)
    {
        int location = input.IndexOf(delimiter)+1;
        string word = input.Substring(0, location);
        string rest = input.Substring(location);
        if (location > 0)
        {
            Console.WriteLine(word.Trim());
            OutputCSVLines(rest,',');
        }
        else
        {
            Console.WriteLine(rest);
        }
    }
    ```

## Additional Exercises

1. Write a program that reads the contents of a text file and inserts the line numbers at the beginning of each line, then rewrites the file contents.
2. Modify the Caesar Cipher program to read the plaintext from a file, output the cipher text to a different file.
3. Modify the Maze program to read a maze pattern from a file
4. Write a program to read a list of names from a file, sorts them (using a bubble sort or alternative sorting algorithm) and writes the sorted list back to the file
5. Write a program to read a file of text and count the number of words in the file
