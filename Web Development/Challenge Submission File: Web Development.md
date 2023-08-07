
# Module 12 Challenge Submission File




## Web Development

Make a copy of this document to work in, and then respond to each question below the prompt. Save and submit this completed file as your Challenge deliverable.


### HTTP Requests and Responses



1. What type of architecture does the HTTP request and response process occur in?

```
Client-Server Architecture
```


2. What are the parts of an HTTP request?

```
Parts of HTTP Request: 1. Request Line 2. Headers 3. Whitespace 4. Request Body.
```


3. Which part of an HTTP request is optional?

```
Request Body
```


4. What are the three parts of an HTTP response?

```
Status Line
Headers
Whitespace
Response Body
```


5. Which status-code number class represents errors?

```
400 codes indicate Client Errors
500 codes indicate Server Errors
```


6. What are the two most common request methods for a security professional to encounter?

```
GET and POST
```


7. Which type of HTTP request method is used to send data?

```
POST
```


8. Which part of an HTTP request contains the data being sent to the server?

```
Th Request Body
```


9. In which part of an HTTP response does the browser receive the web code to generate and style a webpage?

```
The Response Body
```




### Using cURL



10.  What are the advantages of using `curl` over the browser?

```
With curl security professionals can quickly test HTTP requests in a way that can be automated but also allows them to make adjustments, for example, when working through the container which does not have a user interface. Also curl command ensures that web browsers don't leak sensitive data, looks for vulnerabilities on web servers and verifies that servers only respond to certain request types.
```


11. Which `curl` option changes the request method?

```
-X or --request
```


12.  Which `curl` option sets request headers?

```
-H, --header
```


13.  Which `curl` option is used to view the response header?

```
-I, --include
```


14. Which request method might an attacker use to figure out what HTTP requests an HTTP server will accept?

```
Get or options
```




### Sessions and Cookies



15.  Which response header sends a cookie to the client?

```
HTTP/1.1 200 OK
Content-type: text/html
Set-Cookie: cart=Bob  <<<<<< ANSWER!!!!
```


16.  Which request header will continue the client's session?
    
```
GET /cart HTTP/1.1
Host: www.example.org
Cookie: cart=Bob   <<<<<<< ANSWER!!!
```




### Example HTTP Requests and Responses

Use the following sample HTTP request and response to answer the questions in this section:

**HTTP Request**


```
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```




17.  What is the request method?

```
POST
```


18.  Which header expresses the client's preference for an encrypted response?

```
Upgrade-Insecure-Requests: 1
```


19.  Does the request have a user session associated with it?

```
NO
```


20.  What kind of data is being sent from this request body?

```
 Username: Barbara
 Password: password
```



**HTTP Response**


```
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```




21.  What is the response status code?

```
200
```


22.  What web server is handling this HTTP response?

```
Apache
```


23.  Does this response have a user session associated with it?

```
YES
Set-Cookie: SessionID=5
```


24.  What kind of content is likely to be in the [page content] response body?

```
Text/HTML using Unicode encoding
```


25.  If your class covered security headers, what security request headers have been included?

```
HTTP Strict Transport Security (HSTS) - Strict-Transport-Security: max-age=31536000; includeSubDomains

X-Content-Type-Options HTTP - X-Content-Type: NoSniff

X-Frame-Options HTTP - X-Frame-Options: DENY

Cross Site Scripting Protection (X-XSS) - X-XSS-Protection: 1; mode=block

```




### Monoliths and Microservices



26. What are the individual components of microservices called?


There are 8 core components of microservices, that are called SERVICES:
1 Clients 2. Identity Providers 3. API Gateway 4. Messaging Formats 5. Databases 6. Static Content 7. Management 8. Service Discovery

![Screenshot 2023-08-07 112131](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/71f90d20-3d88-48ac-8bc0-5eb5e78ae584)

(https://www.optisolbusiness.com/insight/8-core-components-of-microservice-architecture)</code>





27. What is a service that writes to a database and communicates to other services?

```
API: Application Programming Interface
```


28. What type of underlying technology allows for microservices to become scalable and have redundancy?

```
Containers and Load Balancer
```




### Deploying and Testing a Container Set



29. What tool can you use to deploy multiple containers at once?

```
Docker Compose
```


30. What kind of file format is required to deploy a container set?

```
.YAML file
```




### Databases



31. Which type of SQL query would you use to view all of the information within a table called `customers`?

```
SELECT * FROM customers
```


32. Which type of SQL query would you use to enter new data into a table? (You don't need a full query, just the first part of the statement.)

```
INSERT INTO customers (nameofthecolumn1, …, …) VALUES ("names", "emails", ….)
```


33.  Why would you never run `DELETE FROM &lt;table-name>;` by itself?

```
Without the WHERE clause, this command would delete the whole table.
```







© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
