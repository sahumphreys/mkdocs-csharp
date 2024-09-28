---
title: Extended Theory - Data Compression
---

# {{ title }}

**Data compression** is the process of reducing the size of our data by minimizing the number of bits needed to represent the same information. Data compression is widely used across various file types, including images, sound, video, and text. It serves as an excellent example of enhancing our understanding of string handling with C#.

## Types of Data Compression

There are two main types of data compression:

- **Lossy Compression**: In this method, some data is irreversibly removed from the original file during compression. As a result, the original file cannot be restored precisely when decompressed. Lossy compression is typically used for multimedia files where some loss of quality is acceptable, such as:

    - Images: JPEG
    - Audio: MP3
    - Video: MP4

- **Lossless Compression**: This method allows the original file to be restored exactly as it was before compression. Lossless compression is essential for text and program data where data integrity is crucial. Common formats include:

    - File Archives: ZIP
    - Images: PNG
    - There are two types:


### Run length encoding

**Run Length Encoding** is a form of lossless compression where runs of repeated data are replaced by a single data value and a count of repetitions. It works best with simple graphics, icons, and line drawings. 

For example, if we have a string of 20 characters: `ABBBBCCCCCCCAABDDDDA`, this could be encoded as `1A4B7C2A1B4D1A`, which uses only 14 bytes instead of 20.

To decompress the data, we read the string and interpret the digits as counts for the number of characters that follow.

In C\# the algorithm for compressing data this way would be as below.  It uses, by way of example, the `StringBuilder` class to build a string, from the `System.Collections` namespace, takes the string to compress as a parameter returning the compressed string for further processing:

```cs
static string Compress(string str)
{
    StringBuilder sb = new StringBuilder();
    int count = 1;
    char current = str[0];
    for (int i = 1; i < str.Length; i++)
    {
        if (current == str[i])
        {
            count++;
        }
        else
        {
            sb.AppendFormat("{0}{1}",count,current);
            count = 1;
            current = str[i];
        }
    }
    sb.AppendFormat("{0}{1}",count,current);
    return sb.ToString();
}
```

To decompress the string, we reverse the process:

```cs
static string Decompress(string str)
{
    string decodedStr = string.Empty;
    StringBuilder sb = new StringBuilder();
    foreach(char ch in str)
    {
        if(char.IsDigit(ch))
        {
            decodedStr = decodedStr + ch;
        }
        else
        {
            if(decodedStr == String.Empty)
            {
                sb.Append(ch);
            }
            else
            {
                int count = int.Parse(decodedStr);
                decodedStr = String.Empty;
                for(int j = 0; j < count; j++)
                {
                    sb.Append(ch);
                }
            }
        }
    }
    return sb.ToString();
}
```

RLE is particularly effective when the data contains many repeated runs of text. However, it can be inefficient for non-repetitive data. An improvement can be made by introducing a flag to indicate a repeated run. For example, A*4B*7C*2AB*4DA could use the asterisk as a flag, adding an extra byte for each run but potentially reducing the overall file size.

### Image Compression using RLE

RLE can also be applied to image files. For monochrome bitmaps, one bit can represent black or white, a byte for the pixel value, and another for the run length. The most significant bit (MSB) indicates color: a 0 for white and a 1 for black.

For example, the string 00000111111111111100000000000000000000 would be encoded as 00000101 10001101 00010100, representing runs of white and black pixels.

```cs
static void Main(string[] args)
{
    // load a "binary image"
    string[] data = File.ReadAllLines("CSharpASCII.txt"); 
    string[] compressedText = new string[data.Length];
    // print to check
    PrintImage(imageText,'*');
    // print some info about the original file 
    FileInfo info = new FileInfo("CSharpASCII.txt");
    Console.WriteLine($"({info.Length} bytes)");
    
    // compress each line of the file
    for (int i =0; i < data.Length; i++)
    {
        string s = Compress(data[i]);
        compressedText[i] = s;
    }

    // save compressed string to a file
    string compressedFileName = "CSharpCompressed.txt";
    if (!File.Exists(compressedFileName))
    {
        File.WriteAllLines(compressedFileName,compressedText);
    }
    
    // Read the compressed file
    string[] compressedData = File.ReadAllLines("CSharpCompressed.txt");
    foreach(string s in compressedData)
    {
        PrintImageLine(Decompress(s),'+');
    }

    // get size of compressed file
    info = new FileInfo("CSharpCompressed.txt");
    Console.WriteLine($"({info.Length} bytes)");
}

static string Compress(string str)
{
    int count = 1;
    string compressed = "";
    for(int i = 1; i < str.Length; i++)
    {
        if (str[i] != str[i-1])
        {
            if (str[i-1] == '1')
            {
                count = (count | 128);      // MSB <- 1
            }
            compressed += count + ",";
            count = 1;           
        }
        else
        {
            count++;
        }
        if (i == str.Length - 1)
        {
            compressed += count;
        }
    }
    return compressed;
}

static string Decode(string str)
{
    StringBuilder sb = new StringBuilder();
    string[] parts = str.Split(',');
    char ch;
    for(int i = 0; i < parts.Length; i++)
    {
        int run = Convert.ToInt32(parts[i]);
        if (run >= 128)
        {
            run -= 128;
            ch = '1';
        }
        else
        {
            ch = '0';
        }
        for (int j = 0; j < run; j++)
        {
            sb.Append(ch);
        }
    }
    return sb.ToString();
}

static void PrintImageLine(string line, char ch)
{
    for(int i = 0; i < line.Length; i++)
    {
        if(line[i] == '0')
        {
            Console.Write(' ');
        }
        else
        {
            Console.Write(ch);
        }
    }
    Console.WriteLine();   
}
static void PrintImage(string[] lines, char ch)
{
    foreach(string s in lines)
    {
        PrintImageLine(s,ch);
    }
}
```

A run of this code yields:

```cs

     *************
    **************    **     **
    ****              **     **
    ****         ********************
    ****         ********************
    ****              **     **
    ****         ********************
    ****         ********************
    ****              **     **
    **************    **     **
     *************
(438 bytes)
     +++++++++++++
    ++++++++++++++    ++     ++
    ++++              ++     ++
    ++++         ++++++++++++++++++++
    ++++         ++++++++++++++++++++
    ++++              ++     ++
    ++++         ++++++++++++++++++++
    ++++         ++++++++++++++++++++
    ++++              ++     ++
    ++++++++++++++    ++     ++
     +++++++++++++
(188 bytes)
```

An alternative, would be to make the first digit in the compressed version to represent white pixels.  If the string was `11111000000000000011111111111111111111` this would become `0,5,13,20`.

A similar approach could be taken for images with blocks of colour.  Each colour being represented by a byte, providing $256$ different colours (that could be stored in a lookup file, or embedded in the image file itself).  The data being represented as a series of two byte pairs, the first holding the frequency of repetition, the second the colour.  For example, the following slice from an image file:

![Run length encoding](../../assets/images/rle.png)

Assuming the colour blue used a code of 16, yellow of 12 and green of 3 this data can be compressed as:

`00001000 00010000 00001000 00001100 00001100 00010000 00000100 00000011`

If we need more colour, add in additional bytes for the colour codes.  $24$-bit colour uses a combination of the colours red, green and blue so a compressed image file could use $4$ bytes to represent the colour of each pixel.  As with the previous examples the amount of saving achieved through compression is dependent on the frequency of repeated data.


## Alternative Compression Techniques

- **Dictionary Compression**: A more complex algorithm involves building a dictionary of patterns for compression. One of the most well-known examples is the LZW (Lempel-Ziv-Welch) algorithm. This algorithm is used in formats like GIF. For further exploration, consider reading about it on [Wikipedia](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch).

- **Comparison with Other Techniques**: It’s useful to compare RLE with other compression techniques like Huffman coding, which can be more efficient for certain types of data. Each method has its strengths and weaknesses, depending on the data being compressed.
