# Lab 01: File path traversal, simple case

**Difficulty:** Apprentice
**Category:** Server-side vulnerabilities

## Objective
This lab contains a path traversal vulnerability in the display of product images. To solve the lab, retrieve the contents of the `/etc/passwd` file.

## Reconnaissance
1. Browsed the lab website and clicked on a product.
2. Noticed the product images were loaded via a GET request with a filename parameter:
   `GET /image?filename=63.jpg`
3. This indicates the application is taking user input (the filename) and reading a file from the server's disk.

## Exploitation Steps
1. Attempted to manipulate the filename parameter directly in the browser URL to:
   `../../../etc/passwd`
   *(Result: The browser returned an `ERR_HTTP2_PROTOCOL_ERROR`, likely due to the browser normalizing the path or blocking the request).*
2. Opened **Burp Suite** and ensured the Proxy was intercepting traffic.
3. Refreshed the page, intercepted the `GET /image?filename=63.jpg` request, and sent it to **Repeater**.
4. Modified the request line in Repeater to:
   `GET /image?filename=../../../etc/passwd HTTP/1.1`
5. Clicked **Send**.

## Result
The server responded with `HTTP/2 200 OK`. 
The response body contained the contents of the `/etc/passwd` file, revealing system users such as `root`, `daemon`, `peter`, and `carlos`. The lab was marked as solved.

## Key Takeaway
When a web application reads files based on user input, always test for directory traversal (`../`). If the browser blocks the payload, use a proxy tool like Burp Suite to send the raw request directly to the server.
