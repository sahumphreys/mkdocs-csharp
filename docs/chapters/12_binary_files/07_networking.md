---
title: Extended Theory - Networking
---

# {{ title }}

Modern computing relies heavily on communication between devices, whether on a local network or over the Internet. As you might expect, C# provides robust support for network programming through namespaces like `System.Net` and `System.Net.Sockets`, which include various classes for managing network communication. In this section, we'll explore some basic networking concepts and practical C# programming examples. These examples assume your computer is connected to a network.

Network programming is a vast topic, covering numerous protocols, security considerations, encryption, and different types of communication channels. Here, we'll only scratch the surface by focusing on the fundamental principles of transferring information between applications using a computer network. You can think of it as an I/O stream of data, but instead of being between files or memory, the stream is between nodes on the network.

## IP Addresses and Domain Names

Every device connected to the Internet is assigned a unique address known as an IP address (Internet Protocol address). IP addresses come in two formats: IPv4, which is a 32-bit number (e.g., `192.168.1.1`), and IPv6, which is a 128-bit number designed to address the limitations of IPv4. IP addresses are assigned by Internet Service Providers (ISPs) and managed globally by the [Internet Assigned Numbers Authority (IANA)](https://www.iana.org/).

You can find the IP address of your machine using the following C# code:

```cs
using System;
using System.Net;

namespace GetIpAddress
{
    class Program
    {
        static void Main(string[] args)
        {
            string hostname = Dns.GetHostName();
            string myIp = Dns.GetHostEntry(hostname).AddressList[0].ToString();
            Console.WriteLine($"{hostname} : {myIp}");
        }
    }
}
```

Remembering IP addresses can be difficult, so we use a Domain Name System (DNS) to translate human-readable domain names like `bbc.co.uk` into their respective IP addresses. You can think of DNS as the Internet's phone book. It is a hierarchical, distributed database that maps domain names to IP addresses.

You can modify the previous example to retrieve the IP addresses of any domain:

```cs
using System;
using System.Net;

namespace GetIpAddress
{
    class Program
    {
        static void Main(string[] args)
        {
            string hostname = "bbc.co.uk";
            IPHostEntry host = Dns.GetHostEntry(hostname);
            Console.WriteLine($"{hostname.ToUpper()}: ");
            foreach (IPAddress address in host.AddressList)
            {
                Console.WriteLine($"    {address}");
            }
        }
    }
}
```

In our examples, we’ll often use the special IP address `127.0.0.1`, known as `localhost`, which refers to your local computer. This allows us to simulate network programs without requiring an actual network connection. However, if you know the IP address of another machine, you can also use that.

## TCP/IP

**Transmission Control Protocol/Internet Protocol (TCP/IP)** is the fundamental suite of protocols that enables devices to communicate over the Internet. It dictates how data should be packaged, transmitted, and received. The term "protocol" refers to a set of rules and conventions for communication between devices.

The TCP/IP suite includes several protocols:

- **HTTP**: HyperText Transfer Protocol, used for the web.
- **FTP**: File Transfer Protocol, used for transferring files.
- **SMTP**: Simple Mail Transfer Protocol, used for sending emails.
- **POP3**: Post Office Protocol, used for receiving emails.

While we can’t cover the full layered architecture of TCP/IP here, it’s worth noting its core principles:

- **Network Connectivity**: Any network can connect to any other network via a gateway or router.
- **Decentralization**: There is no central administration.
- **Error Recovery**: Lost data packets are retransmitted.
- **Black Box Design**: Networks can connect without internal modifications.

## Clients and Servers

In networking, a common model is the **client-server** model. A `client` requests a service, while a `server` provides it. For example, when you visit a website, your browser (the client) requests data from a web server.

### Example: Downloading a Web Page

The following C# code uses the `WebClient` class to download a web page and save its contents to a file:

```cs
using (var webClient = new WebClient())
{
    webClient.DownloadFile("https://stackoverflow.com/questions/tagged/network-programming", "networking.html");
}
```

The `using` block ensures that resources are released when the operation is complete. The `DownloadFile()` method takes a URL and a file name, and saves the web page content locally.

## Sockets

To enable communication between a client and server, we need two key pieces of information:

- The server's IP address.
- The port number on which the server is "listening" for requests.

These two elements form a **socket**, which is an endpoint for communication between two machines. In C#, the `TcpClient` and `TcpListener` classes manage client and server communication respectively.

### The Server

The server listens for incoming connections using a socket. Here’s a simple server setup:

```cs
IPAddress localIp = IPAddress.Parse("127.0.0.1");
TcpListener listener = new TcpListener(localIp, 8080);
listener.Start();
Console.WriteLine("Server is listening...");

while (true)
{
    Socket socket = listener.AcceptSocket();
    if (socket.Connected)
    {
        Console.WriteLine("Client connected");
        // Handle the client connection
    }
}
```

This server listens for connections on port 8080. When a client connects, the server can interact with it using the `socket` object.

!!! tip
    Always use `try...catch` blocks to handle exceptions, such as when a port is already in use.

### The Client

The client connects to the server using the server’s IP address and port number:

```cs
TcpClient client = new TcpClient("127.0.0.1", 8080);
Console.WriteLine("Connected to the server.");
```

Next, set up a `NetworkStream` for reading and writing data:

```cs
NetworkStream ns = client.GetStream();
StreamWriter sw = new StreamWriter(ns);
StreamReader sr = new StreamReader(ns);

// Send a message to the server
Console.WriteLine("Enter text to send to the server: ");
string message = Console.ReadLine();
sw.WriteLine(message);
sw.Flush();

// Read response from server
string response = sr.ReadLine();
Console.WriteLine($"Server Response: {response}");
```

## A Simple Client-Server Application

Below is a basic example of a client-server application. The client sends a command to the server, and the server responds based on the command received.

### The Client

```cs
using System;
using System.Net.Sockets;
using System.IO;

public class Client
{
    static void Main(string[] args)
    {
        TcpClient client = new TcpClient("127.0.0.1", 8080);
        NetworkStream ns = client.GetStream();
        StreamWriter sw = new StreamWriter(ns);
        StreamReader sr = new StreamReader(ns);

        Console.Write("Enter command (/e or /u) followed by message: ");
        string input = Console.ReadLine();
        sw.WriteLine(input);
        sw.Flush();

        string response = sr.ReadToEnd().Trim();
        Console.WriteLine($"Server Response: {response}");

        ns.Close();
        client.Close();
    }
}
```

### The Server

```cs
using System;
using System.Net;
using System.Net.Sockets;
using System.IO;

public class Server
{
    static void Main(string[] args)
    {
        IPAddress localIp = IPAddress.Parse("127.0.0.1");
        TcpListener listener = new TcpListener(localIp, 8080);
        listener.Start();
        Console.WriteLine("Server is listening...");

        while (true)
        {
            Socket socket = listener.AcceptSocket();
            NetworkStream ns = new NetworkStream(socket);
            StreamReader sr = new StreamReader(ns);
            StreamWriter sw = new StreamWriter(ns);

            string request = sr.ReadLine().Trim();
            string[] parts = request.Split(' ', 2);

            switch (parts[0])
            {
                case "/e":
                    sw.WriteLine(parts[1]);
                    break;
                case "/u":
                    sw.WriteLine(parts[1].ToUpper());
                    break;
                default:
                    sw.WriteLine("Unknown command.");
                    break;
            }

            sw.Flush();
            ns.Close();
            socket.Close();
        }
    }
}
```

In this example, the client sends a command (`/e` for echo, `/u` for uppercase) and a message to the server. The server processes the command and responds accordingly.

## Conclusion

Networking in C# involves many concepts, but the basics revolve around understanding how to use IP addresses, sockets, and streams to transfer data. With these fundamentals, you can start building more complex client-server applications.