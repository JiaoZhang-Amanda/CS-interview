# Networking concepts Interview Question
## [Protocols]
* **IP**(Internet Protocol): IP is designed explicitly as addressing protocol. It is mostly used with TCP. The IP addresses in packets help in routing them through different nodes in a network until it reaches the destination system. TCP/IP is the most popular protocol connecting the networks.
* **TCP**: Transmission Control Protocol. TCP is a popular communication protocol which is used for communicating over a network. It divides any message into series of packets that are sent from source to destination and there it gets reassembled at the destination.
* **UDP**: User Datagram Protocol. UDP is a substitute communication protocol to Transmission Control Protocol implemented primarily for creating loss-tolerating and low-latency linking between different applications.
* **FTP**: File Transfer Protocol. FTP allows users to transfer files from one machine to another. Types of files may include program files, multimedia files, text files, and documents, etc.
* **HTTP**: Hyper Text Transfer Protocol. HTTP is designed for transferring a hypertext among two or more systems. HTML tags are used for creating links. These links may be in any form like text or images. HTTP is designed on Client-server principles which allow a client system for establishing a connection with the server machine for making a request. The server acknowledges the request initiated by the client and responds accordingly.
* **HTTPs**: Hyper Text Transfer Protocol Secure. HTTPS is abbreviated as Hyper Text Transfer Protocol Secure is a standard protocol to secure the communication among two computers one using the browser and other fetching data from web server. HTTP is used for transferring data between the client browser (request) and the web server (response) in the hypertext format, same in case of HTTPS except that the transferring of data is done in an encrypted format. So it can be said that https thwart hackers from interpretation or modification of data throughout the transfer of packets.
* **SMTP**: Simple mail transport Protocol. SMTP is designed to send and distribute outgoing E-Mail.
* **POP**: Post office Protocol. POP3 is designed for receiving incoming E-mails.
* **SSH**: Secure Shell. SSH allows for remote command-line login and remote execution. It has many of the functions of FTP but is more secure.
* **Telnet**: Telnet is a set of rules designed for connecting one system with another. The connecting process here is termed as remote login. The system which requests for connection is the local computer, and the system which accepts the connection is the remote computer.
* **ARP**: Address Resolution Protocol.  It's used to find LAN address from the network address. It helps a node to send a frame over a local link. The node send a broadcast message to all nodes "What is the MAC address of this ip address". Node with the provided ip address replies with MAC address.
* **DHCP**: dynamic host configuration protocol. It is a network protocol used on IP networks. A DHCP server automatically assigns an IP address and other information to each host on the network so they can communicate efficiently with other endpoints. Device sends broadcast message "I am new here". DHCP server see message and responde and allocate an IP address, while other devices ignore the message.
* **Sliding Window Protocols**: Sliding window protocols are data link layer protocols for reliable and sequential delivery of data frames. The sliding window is also used in Transmission Control Protocol. In this protocol, multiple frames can be sent by a sender at a time before receiving an acknowledgment from the receiver. The term sliding window refers to the imaginary boxes to hold frames.
    - Types: Sliding Window ARQ(Automatic Repeat reQuest) 
        * **Go – Back – N ARQ**: sending multiple frames before receiving the acknowledgment for the first frame. The frames are sequentially numbered and a finite number of frames are sent. If the acknowledgment of a frame is not received within the time period, all frames starting from that frame are retransmitted.
        * **Selective Repeat ARQ**: sending multiple frames before receiving the acknowledgment for the first frame. However, here only the erroneous or lost frames are retransmitted, while the good frames are received and buffered.
    - TCP Window Size Scaling: TCP uses “windowing” which means that a sender will send one or more data segments and the receiver will acknowledge one or all segments. When the receiver sends an acknowledgment, it will tell the sender how much data it can transmit before the receiver will send an acknowledgment. We call this the window size. Basically, the window size indicates the size of the receive buffer. Typically the TCP connection will start with a small window size and every time when there is a successful acknowledgement, the window size will increase. 
* **Stop and wait protocol**: sender sends one frame, waits until it receives confirmation from the receiver (okay to go ahead), and then sends the next frame.
### 1. What is the difference between TCP and UDP? When would you use each of them?
TCP|UDP
--|--
TCP stands for Transmission control protocol|UDP stands for User datagram protocol
TCP is connection-oriented protocol means before sending data, there is connection establishment happens between two clients|UDP is connectionless protocol means there is no connection establishment before sending data between two clients
TCP provides reliable communication|UDP provides unreliable communiation
TCP gives guarantee of transmission of data|UDP does not give guarantee of transmission of data.
TCP header size is 20 bytes|UDP header size is 8 bytes
In TCP there is concept of acknowledgment|In UDP there is no concept of acknowledgment
TCP has concern of jitter. Means if any packet lost then TCP does not provide subsequent data to the application while it is requesting re-sending of the missing data|UDP does not have concern of jitter because there is retransmission of missing data.
TCP is slower as compared to UDP because retransmission of lost packets can take long delay.|UDP is faster as compared to TCP because there is no retransmission of lost packets

### 2. What are request methods in HTTP?
HTTP denotes Hyper Text Transfer Protocal, port#80, responsible for web context.
- **GET**- It is used to send data in url.
- **HEAD**- It only transfers status line and header section as a request.
- **POST**- It is used to send data to the server.
- **PUT**- It is used to send entire updated data to the server. 
- **DELETE**- Delete method sends a request to the server to perform delete operation.
- **CONNECT**- It is used to establish connection to the server.
- **OPTIONS**- Option method describes communication options for target resource.
- **TRACE**- It performs message loop-back test along the path to the target resource.

### 3. What is status code in HTTP?
4xx Client Error/5xx Server Error
- **500** internal server errors: Web server displays 500 internal server error, when processing fails due to some unanticipated incident on the server side. 
- **409** : When we use PUT request to create the same resource twice then server displays 409 code to the browser.
- **405**Method not allowed: Web Server displays the HTTP 405 error message, when requested method is not allowed. Ex. if a resource allows get method, we cannot request post to get this resource.
- **401**: This response code is generated when an unauthorized user request for secure resource on the web server.
- **404** Not found: It indicates that the requested resource is not available at the web server.
- **400** Bad Request: This request shows malfunction. It display specially with POST and PUT requests, when the data does not pass validation.
- **201** Created: This indicates that the request was successful. It is used to confirm success of a PUT or POST request.
- **200** OK: It indicates that the request is successful.

### 4. TCP Three-way handshake? TCP Synchronisation
* The client sends a TCP SYNchronize packet to Server
* Server receives client’s SYN
* Server sends a SYNchronize+ACKnowledgement
* Client receives Server’s SYN-ACK
* Client sends ACKnowledge
* Server receives ACK.
* TCP socket connection is ESTABLISHED.

## [Models]
### 1. Explain the seven layers of the OSI reference model. / What are layers in OSI model?
**OSI model** stands for Open System Interconnection. It’s a reference model which describes that how different applications will communicate to each other over the computer network.
* **Physical Layer**: Converts data bit into an electrical impulse.(e.g. ethernet)
* **Datalink Layer**: Data packet will be encoded and decoded into bits.
* **Network Layer**: Transfer of datagrams from one to another.
* **Transport Layer**: Responsible for Data transfer from one to another. Keep track all transmission and failure.
* **Session Layer**: Manage and control signals between computers.
* **Presentation Layer**: Transform data into application layer format.
* **Application Layer**: An end user and application interact with the Application layer. (e.g. email)

### 2. Explain TCP/IP Model
* The most widely used and available protocol is TCP/IP i.e. Transmission Control Protocol and Internet Protocol. TCP/IP specifies how data should be packaged, transmitted and routed in their end to end data communication.
* Given below is a brief explanation of each layer:
    * Application Layer: This is the top layer in the TCP/IP model. It includes processes that use Transport Layer Protocol to transmit the data to their destination. There are different Application Layer Protocols such as HTTP, FTP, SMTP, SNMP protocols, etc.
    * Transport Layer: It receives the data from the Application Layer which is above the Transport Layer. It acts as a backbone between the host's system connected with each other and it mainly concerns about the transmission of data. TCP and UDP are mainly used as Transport Layer protocols.
    * Network or Internet Layer: This layer sends the packets across the network. Packets mainly contain source & destination IP addresses and actual data to be transmitted.
    * Network Interface Layer: It is the lowest layer of the TCP/IP model. It transfers the packets between different hosts. It includes encapsulation of IP packets into frames, mapping IP addresses to physical hardware devices, etc.
    
### 3. Data transmission
e.g. a network server transmits data to a client</br>
![](https://community.emc.com/servlet/JiveServlet/showImage/2-831148-90201/image002.jpg)
* The data to be transferred is the HTML page of the web server.
* Add HTTP headers before data. The header  includes the HTTP version and a status code.
* HTTP application layer protocol sends data to the transport layer. The TCP is used to manage the sessions between the network server and the client.
* IP information is added before TCP information. IP specifies the appropriate source and destination IP addresses. This information constitutes an IP message.
* After the Ethernet protocol is added to both ends of the IP packet, the data link frame is formed. The above frame is sent to the nearest router on the path to the network client. The router removes the Ethernet information, looks at the IP message, determines the best path, inserts the message into a new frame, and sends it to the next adjacent router in the target path. Each router removes and adds new data link layer information before forwarding.
* Data is transmitted over the Internet, which contains media and intermediaries.
* The client receives the data link frame containing the data, and processes each headers, and then removes the protocol headers in the reverse order. First the Ethernet information is removed, then the IP protocol information, then the TCP information, and finally the HTTP information.
* After that, the web page information is passed to the client web browser software.

### 4. What's mtu?
A **maximum transmission unit (MTU)** is the largest size packet or frame, specified in octets (eight-bit bytes), that can be sent in a packet- or frame-based network such as the Internet. The Internet's Transmission Control Protocol (TCP) uses the MTU to determine the maximum size of each packet in any transmission.

## [Others]
### 1. Describe in as much details as possible what happens after we type "www.google.com" into the URL box of browser and hit enter. / What happens when you type a URL in the web browser?
- Step 1. URL is typed in the browser.
- Step 2. If requested object is in browser cache and is fresh, move on to Step  8.
- Step 3. DNS lookup to find the ip address of the server. Browser first looks up URL-ip mapping browser cache, then in OS cache. If all empty, then make a recursive query to local DNS server(provide ip address).
- Step 4. Browser initiates a TCP connection with the server using three way handshake.
- Step 5. Browser sends a HTTP request to the server.
- Step 6. Server handles the incoming HTTP request and sends an HTTP response.
- Step 7. Browser receives the HTTP response
- Step 8. Browsers renders and displays the html content 
- Step 9. Client interaction with server

### 2. What are cookies? Why do we need it?
**Cookies** are small pieces of information stored on the client computer. Use cookies to store small amounts of information on the client's machine. Web sites often use cookies to store user preferences or other information that is client specific.
- **Session Cookies**: stored **in-memory** during the client browser session. When the browser is closed the session, cookies are lost.
- **Persistent Cookies**:  same as Session Cookies except that, persistent cookies have an **expiration date**. The expiration date indicates to the browser that it should write the cookie to the client's hard drive.
**[Adv. ]**
1. Cookies do not require any server resources since they are stored on the client.
2. Cookies are easy to implement.
3. You can configure cookies to expire when the browser session ends (session cookies) or they can exist for a specified length of time on the client computer (persistent cookies).
**[DisAdv.]**
1. User can delete a cookie
2. User browser can refuse cookies
3. Cookies exit as plain text on client machine and they may pose a security rist as anyone can open the cookie.

### 3. Difference between Hub, Switch and Router?
* Computers can be connected to each other via a switch or a router. A switch is designed to connect computers within a network, while a router is designed to connect multiple networks together.
* The main objective of **router** is to connect various *networks* simultaneously and it works in *network layer*(Layer 3 of the OSI Model), whereas the main objective of **switch** is to connect various *devices* simultaneously and it works in *data link layer*(Layer 2 of the OSI Model).
* Hub, broadcast all data to every port, physical Layer.


### 4. What's DNS? what protocol it use? How DNS works(detail)? 
* DNS stands for Domain Name System. It translates domain names to IP addresses so browsers can load Internet resources. It works in a hierarchical way.
* It is an application layer protocol for message exchange between clients and servers. DNS primarily uses the User Datagram Protocol (UDP) on port number 53 to serve requests.
*  Process:
    * Step 1: Request information. <br>
      The process begins when you ask your computer to resolve a hostname, such as visiting https://dyn.com. The first place your computer looks for the corresponding IP address is its local **DNS cache**, which stores information that your computer has recently retrieved.
                  If your computer doesn’t already know the answer, it needs to perform a DNS query to find out.
    * Step 2: Ask the recursive DNS servers.<br>
    your computer queries (contacts) the **recursive DNS servers** (resolvers) from your internet service provider (ISP). 
    * Step 3: Ask the root name servers.
    If the recursive servers don’t have the answer, they query the **root name servers**.
    * Step 4: Ask the TLD name servers.
    The root name servers will look at the first part of our request, reading from right to left — www.dyn.com — and in our case, direct our query to the **top-level domain** (TLD) name servers for .com.
    * Step 5: Ask the authoritative DNS servers.
    The TLD name servers review the next part of our request — www.dyn.com — and direct our query to the name servers responsible for this specific domain.
    * Step 6: Retrieve the record.
    The recursive server retrieves the A record for dyn.com from the authoritative name servers and stores the record in its local cache.
    * Step 7: Receive the answer. 
    Armed with the answer, recursive server returns the A record back to your computer. Your computer stores the record in its cache, reads the IP address from the record, then passes this information to your browser. The browser then opens a connection to the webserver and receives the website.

* The 8 steps in a DNS lookup:
    * 1) A user types ‘example.com’ into a web browser and the query travels into the Internet and is received by a DNS recursive resolver.
    * 2) The resolver then queries a DNS root nameserver (.).
    * 3) The root server then responds to the resolver with the address of a Top Level Domain (TLD) DNS server (such as .com or .net), which stores the information for its domains. When searching for example.com, our request is pointed toward the .com TLD.
    * 4) The resolver then makes a request to the .com TLD.
    * 5) The TLD server then responds with the IP address of the domain’s nameserver, example.com.
    * 6) Lastly, the recursive resolver sends a query to the domain’s nameserver.
    * 7) The IP address for example.com is then returned to the resolver from the nameserver.
    * 8) The DNS resolver then responds to the web browser with the IP address of the domain requested initially.
    * Once the 8 steps of the DNS lookup have returned the IP address for example.com, the browser is able to make the request for the web page:
    * 9) The browser makes a HTTP request to the IP address.
    * 10) The server at that IP returns the webpage to be rendered in the browser (step 10).
    
### 5. What is a Proxy Server and how do they protect the computer network?
* For data transmission, IP addresses are required and even DNS uses IP addresses to route to the correct website. It means without the knowledge of correct and actual IP addresses it is not possible to identify the physical location of the network.
* Proxy Servers prevent external users who are unauthorized to access such IP addresses of the internal network. The Proxy Server makes the computer network virtually invisible to the external users.
* Proxy Server also maintains the list of blacklisted websites so that the internal user is automatically prevented from getting easily infected by viruses, worms, etc.

### 6. What are the different types of a network? Explain each briefly.
* Personal Area Network (PAN): It is the smallest and basic network type that is often used at home. It is a connection between the computer and another device such as phone, printer, modem tablets, etc
* Local Area Network (LAN): LAN is used in small offices and internet cafes to connect a small group of computers to each other. Usually, they are used to transfer a file or for playing the game in a network.
* Metropolitan Area Network (MAN): It is a powerful network type than LAN. The area covered by MAN is a small town, city, etc. A huge server is used to cover such a large span of area for connection.
* Wide Area Network (WAN): It is more complex than LAN and covers a large span of the area typically a large physical distance. The Internet is the largest WAN which is spread across the world. WAN is not owned by any single organization but it has distributed ownership.
* Storage Area Network (SAN)
* System Area Network (SAN)
* Enterprise Private Network (EPN)
* Passive Optical Local Area Network (POLAN)

### 7. Different Wi-Fi Protocols and Data Rates
IEEE 802.11 Wi-Fi protocol summary:

Protocol | Frequency  | Channel Width   |   MIMO   |   Maximum data rate (theoretical)
-- | -- | -- | -- | --
802.11ax   |   2.4 or 5GHz    |  20, 40, 80, 160MHz  |    Multi User (MU-MIMO)    |  2.4 Gbps1
802.11ac wave2   |   5 GHz   |   20, 40, 80, 160MHz   |   Multi User (MU-MIMO)   |   1.73 Gbps2
802.11ac wave1   |   5 GHz   |   20, 40, 80MHz   |   Single User (SU-MIMO)   |   866.7 Mbps2
802.11n  |    2.4 or 5 GHz   |   20, 40MHz   |   Single User (SU-MIMO)  |    450 Mbps3
802.11g  |    2.4 GHz    |  20 MHz   |   N/A   |   54 Mbps
802.11a  |    5 GHz   |   20 MHz  |    N/A    |  54 Mbps
802.11b  |    2.4 GHz    |  20 MHz    |  N/A   |   11 Mbps
Legacy 802.11  |    2.4 GHz   |   20 MHz   |   N/A   |   2 Mbps

## [network troubleshooting]
### 1. If your computer runs slow, how to troubleshout(linux server)?
* Because of some of the following reasons:
    * Many unnecessary services started or initialised at boot time by the init program
    * Many RAM consuming applications such as LibreOffice on your computer
    * Your (old) hard drive is malfunctioning, or its processing speed cannot keep up with the modern application
* To speed up:
    * Examine CPU information: cat /proc/cpuinfo
    * Check for services started at boot-time: service --status-all
    * Examine CPU Load: check whether your processor/CPU is overloaded with processes. (top)
    * Check for free memory space: RAM is where commonly used applications are usually stored. You can use the free command to check for memory information such as free space available for RAM and so on
    * Check if your hard drive is overworking
    
### 2. If you had no connection and thr address of 169.254 what does this means and how to solve the issue?
* Getting a 169.254.x.x address simply tells you the machine cannot reach the DHCP server over the network.
* 169.254.x.x: This is what's called an Automatic Private IP address. An IP in this range means that the computer cannot see the network. A computer using DHCP needs to have an external server tell it what IP address to use. Unfortunately, if there's no network connectivity, the computer is unable to talk to the server. In those cases, the computer will actually give itself an IP starting with 169.254, since it must assign itself some sort of number. When you see a 169.254.x.x address, you definitely have a problem. It could be as simple as an unplugged network cable, or it could be as complex as the network being down. A fair amount of troubleshooting is involved at this point, but the bottom line is that your computer doesn't even see the network.

### 3. Conmmands used to check Internet connection?
* PING servername/PING serverIP
* TRACERT servername/TRACERT serverIP

### 4. If a server failed to do a nightly backup, what could be a reason for that? 
* May be due to failure or mis-configuration of NTP Server.

### 5. When and why did you use wireshark?
Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education.

## [Socket Programming]
### 1. Difference between sendto and send functions.
These functions send data to a socket. Generally speaking, send() is used for TCP SOCK_STREAM connected sockets, and sendto() is used for UDP SOCK_DGRAM unconnected datagram sockets.

### 2. TCP Socket API
**socket()**: specifying the type of communication protocol (TCP based on IPv4, TCP based on IPv6, UDP).
```#include <sys/socket.h>
 int socket (int family, int type, int protocol);
```
**connect()**: is used by a TCP client to establish a connection with a TCP server
`int connect (int sockfd, const struct sockaddr *servaddr, socklen_t addrlen);`
**bind()**: assigns a local protocol address to a socket. With the Internet protocols, the address is the combination of an IPv4 or IPv6 address (32-bit or 128-bit) address along with a 16 bit TCP port number.
`int bind(int sockfd, const struct sockaddr *servaddr, socklen_t addrlen);`
**listen()**: converts an unconnected socket into a passive socket, indicating that the kernel should accept incoming connection requests directed to this socket.
`int listen(int sockfd, int backlog);`
**accept()**: retrieve a connect request and convert that into a request.
`int accept(int sockfd, struct sockaddr *cliaddr,socklen_t *addrlen);`
**send()**: is similar to write() but allows to specify some options.
`ssize_t send(int sockfd, const void *buf, size_t nbytes, int flags);`
**receive()**: is similar to read(), but allows to specify some options to control how the data are received.
`ssize_t recv(int sockfd, void *buf, size_t nbytes, int flags);`
**close()**: close a socket and terminate a TCP socket. 
`int close(int sockfd);`

Establishing a TCP socket on the **client side** are the following:
- Create a socket using the `socket()` function;
- Connect the socket to the address of the server using the `connect()` function;
- Send and receive data by means of the `read()` and `write()` functions.
- Close the connection by means of the `close()` function.
Establishing a TCP socket on the **server side** are as follows:
- Create a socket with the `socket()` function;
- Bind the socket to an address using the `bind()` function;
- Listen for connections with the `listen()` function;
- Accept a connection with the `accept()` function system call. This call typically blocks until a client connects with the server.
- Send and receive data by means of `send()` and `receive()`.
- Close the connection by means of the `close()` function.

### 3. UDP Socket API
**recvfrom()**: is similar to the read() function, but three additional arguments are required.
`ssize_t recvfrom(int sockfd, void* buff, size_t nbytes, int flags, struct sockaddr* from, socklen_t *addrlen);`
**sendto()**: is similar to the send() function, but three additional arguments are required.
`ssize_t sendto(int sockfd, const void *buff, size_t nbytes,int flags, const struct sockaddr *to,socklen_t addrlen);`
Establishing a UDP socket communication on the **client side** are the following:
- Create a socket using the socket() function;
- Send and receive data by means of the recvfrom() and sendto() functions.
Establishing a UDP socket communication on the **server side** are as follows:
- Create a socket with the socket() function;
- Bind the socket to an address using the bind() function;
- Send and receive data by means of recvfrom() and sendto().
