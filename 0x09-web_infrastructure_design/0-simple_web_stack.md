# Simple Web Infrastructure Design

## Components:
1. **1 Server**
2. **1 Web Server (Nginx)**
3. **1 Application Server**
4. **1 Application Files (your code base)**
5. **1 Database (MySQL)**
6. **1 Domain Name (foobar.com)**

## Overview:
This design hosts a website reachable via `www.foobar.com` on a single server.

![Simple Web Infrastructure](./simple_web_stack.png)

## Request Flow:
1. **DNS Resolution**:
   - User types `www.foobar.com` in their browser.
   - The DNS resolver translates `www.foobar.com` to the IP address `8.8.8.8`.

2. **HTTP Request**:
   - The user's browser sends an HTTP request to the server at IP address `8.8.8.8`.

3. **Nginx Web Server**:
   - Receives the HTTP request.
   - Serves static content directly if requested.
   - Forwards dynamic content requests to the application server.

4. **Application Server**:
   - Processes the request.
   - Interacts with the MySQL database if necessary.
   - Executes application logic defined in the application files.

5. **MySQL Database**:
   - Manages application data.
   - Responds to queries from the application server.

6. **HTTP Response**:
   - The application server sends the response back to the Nginx web server.
   - The Nginx web server forwards the response back to the user's browser.

## Issues:
- **Single Point of Failure (SPOF)**: The entire infrastructure depends on a single server.
- **Maintenance Downtime**: Updates or maintenance can cause downtime.
- **Scalability**: Limited capacity to handle high traffic volumes.

## Recommendations:
Consider implementing a more robust infrastructure with multiple servers, load balancers, and distributed databases for better reliability, reduced downtime, and enhanced scalability.

