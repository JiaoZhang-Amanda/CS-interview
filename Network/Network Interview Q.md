## Network Interview Question

### 1. Describe in as much details as possible what happens after we type "www.google.com" into the URL box of browser and hit enter. / What happens when you type a URL in the web browser?
Step 1. URL is typed in the browser.
Step 2. If requested object is in browser cache and is fresh, move on to Step  8.
Step 3. DNS lookup to find the ip address of the server
Step 4. Browser initiates a TCP connection with the server.
Step 5. Browser sends a HTTP request to the server.
Step 6. Server handles the incoming request
Step 7. Browser receives the HTTP response
Step 8. Browsers displays the html content 
Step 9. Client interaction with server

### 2. What are cookies? Why do we need it?
Cookies are small pieces of information stored on the client computer. Use cookies to store small amounts of information on the client's machine. Web sites often use cookies to store user preferences or other information that is client specific.
Session Cookies
Persistent Cookies
Session cookies are stored in-memory during the client browser session. When the browser is closed the session, cookies are lost.
Persistent Cookies are same as Session Cookies except that, persistent cookies have an expiration date. The expiration date indicates to the browser that it should write the cookie to the client's hard drive.

**[Adv. ]**
1. Cookies do not require any server resources since they are stored on the client.
2. Cookies are easy to implement.
3. You can configure cookies to expire when the browser session ends (session cookies) or they can exist for a specified length of time on the client computer (persistent cookies).

### 3. What is the difference between TCP and UDP? When would you use each of them?
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

### 4. What are request methods in HTTP?
**GET**- It is used to send data in url.
**HEAD**- It only transfers status line and header section as a request.
**POST**- It is used to send data to the server.
**PUT**- It is used to send entire updated data to the server. 
**DELETE**- Delete method sends a request to the server to perform delete operation.
**CONNECT**- It is used to establish connection to the server.
**OPTIONS**- Option method describes communication options for target resource.
**TRACE**- It performs message loop-back test along the path to the target resource.

### 5. What is status code in HTTP?
4xx Client Error/5xx Server Error
**500** internal server errors: Web server displays 500 internal server error, when processing fails due to some unanticipated incident on the server side. 
**409** : When we use PUT request to create the same resource twice then server displays 409 code to the browser.
**405**Method not allowed: Web Server displays the HTTP 405 error message, when requested method is not allowed. Ex. if a resource allows get method, we cannot request post to get this resource.
**401**: This response code is generated when an unauthorized user request for secure resource on the web server.
**404** Not found: It indicates that the requested resource is not available at the web server.
**400** Bad Request: This request shows malfunction. It display specially with POST and PUT requests, when the data does not pass validation.
**201** Created: This indicates that the request was successful. It is used to confirm success of a PUT or POST request.
**200** OK: It indicates that the request is successful.

