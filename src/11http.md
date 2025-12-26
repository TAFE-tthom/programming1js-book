# HTTP Protocol and Utilities

Hypertext Transfer Protocol is the primary protocol of the web, it is built on top of TPC/IP which is used for establishing connections between two computers (client and server).

The HTTP protocol has two messages per connection (conceptually, HTTP 2 and 3 attempt to keep the connection alive for multiple requests). Each connection will send a request which will contain the following.

* Start Line, provide the http version and method of connction
* Headers, provides http headers that the server can extract, this can be metadata or information about the content being sent
* Body, provides the content that is being sent, this however is not relevant for a GET request.


THe HTTP response send the same kind data, it will contain a start-line, headers and body. Typically the body and headers are always set for the response to ensure that the client is able to receive some data.

Using `netcat` (may be `nc` on your system or may need to be installed). You can try the following example to connect to google.

```
[user@hostname ~] netcat google.com -p 80
GET / HTTP/1.1


```

The above snippet connects to google.com on port 80 (HTTP port) and sends the basic requirements for a HTTP message. You should receive a response from the server.

While you can use this command for testing your connections and the different kinds of messages you can send, you are better off testing endpoints with a command like `curl`.


```
[user@hostname ~] curl google.com
```

The above snippet will do a simple get request, when adding more to the command, you will be able to specify this easily and with the extra of curl handling HTTP 2 and 3 (which are binary protocols).

## Domains and URL

A webserver will need to be reachable via a URL which is typically tied to a domain name. When hosting locally, you will notice that you will use `localhost` as the domain you are accessing.

Our common usage is to not use IP addresses within the browser or to connect to servers, we usually use a **domain** or **hostname**. However, IP addresses are a fundamental construct for the internet.

Commonly with IPv4, we can represent an address with 4 bytes, each byte is typically represented on its own and then followed by a `.`.

As an example:
```
192.168.0.1
```

The example above has 4 numbers, each number is a number that is within the range of 0-255.


A **hostname** is a name that a computer has, it is a way of identifying it rather than remembering its IP address. A hostname and protocol can be used to build up a map of a local network or even a network online.

**Domain**s are a little more infrastructure specific and use the idea of a DNS server.A domain name server is a database map that takes a domain name string and returns the IP address associated, it is also present to outline/describe particular services on the internet.

**Domain** names are provided by a domain name registrar. A domain name registrar is responsible for handling domain name registration. An entity can register a domain name through one of these providers.

Given that these providers will hold a database of names and their associated IP address, these providers are going to be responsible for at minimum, providing tools for a user to input DNS records and associate with servers or other hostnames.

By default, you have heard (or not) of the root name server of `8.8.8.8` which actually points to google's root name server. This server helps will providing a list of other name servers.

### Serialised Data (JSON)

In the `post` example prior, we observed the usage of JSON when sending and receiving data. On this point, what is standard for web applications is using JSON but this may not be format that all applications use as they may use a binary protocol like `protobuf` or `capnproto` or other text-based serialisation formats like XML.

As a research exercise, look up what applications these protocols are used for.

* Protocol Buffers (protobuf)
* XML
* JSON

You can attempt to interpret data from a resource using the `JSON` library to `.parse` or in the case where you want to convert it to a string, `.stringify`.
