# How the Web Works: From URL to Web Page

Great developers don’t just write code — they understand how the web works behind the scenes.
This guide explains what really happens when you type a URL into your browser and press Enter.

---

## 1. What is a URL?

A URL (Uniform Resource Locator) is the address of a resource on the web.

Example:
[https://www.example.com/page]

It contains:
- **Protocol**: `https`
- **Domain name**: `example.com`
- **Path**: `/page`

---

## 2. DNS: Converting Name to IP Address

Computers don’t understand domain names — they understand IP addresses.

So the browser:
1. Checks browser cache
2. Checks OS cache
3. Queries a DNS server

Example:
example.com → 93.184.216.34


This process is called **DNS resolution**.

---

## 3. Establishing a Connection

Once the IP address is found:
- Browser creates a **TCP connection**
- For HTTPS, a **TLS handshake** happens
- Secure communication is established

This ensures data is encrypted and safe.


## 4. Sending the HTTP Request

The browser sends an HTTP request like:


GET /page HTTP/1.1
Host: example.com

This request asks the server for a resource.


## 5. Server Processing

The server:
- Receives the request
- Runs backend logic (Node.js, Django, etc.)
- Fetches data from databases if needed
- Generates a response

---

## 6. HTTP Response

The server sends back a response:


HTTP/1.1 200 OK
Content-Type: text/html


Along with HTML, CSS, JS, images, etc.


## 7. Browser Rendering Process

The browser:
1. Parses HTML → DOM
2. Parses CSS → CSSOM
3. Executes JavaScript
4. Builds Render Tree
5. Paints pixels on screen

This is why large CSS or JS files can slow websites.

---

## 8. Final Page Load

Once all resources load:
- Page becomes interactive
- Event listeners activate
- User can interact with the UI

---

## 9. Why Understanding This Matters

Understanding this flow helps developers:
- Build faster websites
- Debug performance issues
- Write better frontend & backend code
- Understand APIs and security concepts

---

## Conclusion

Every website load is a collaboration between:
- Browser
- DNS
- Network
- Server
- Backend logic

## Knowing this flow makes you a **better web developer**, not just a coder.
