when someone types www.example.com in their browser

| Step | Phase                               | Description                                                                                                               |
| ---- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| 1    | **Browser DNS Cache Check**         | Browser checks its internal DNS cache for the IP of the domain (e.g., `gaethe.io`).                                       |
| 2    | **OS DNS Cache Check**              | If not found in browser cache, the browser asks the OS, which checks its own DNS cache.                                   |
| 3    | **DNS Server Lookup**               | If still unresolved, the OS sends a DNS query to the configured DNS server (e.g., 8.8.8.8 or ISP's DNS) over UDP port 53. |
| 4    | **Root Name Server Query**          | The DNS resolver queries a root name server to find the name servers responsible for the `.io` TLD.                       |
| 5    | **TLD Name Server Query**           | The resolver queries the `.io` TLD server for the name servers responsible for `gaethe.io`.                               |
| 6    | **Authoritative Name Server Query** | The resolver queries the authoritative name server for `gaethe.io` to get its IP address (A/AAAA record).                 |
| 7    | **IP Address Returned and Cached**  | The resolver returns the IP to the OS, which passes it to the browser. Both OS and resolver cache it according to TTL.    |
| 8    | **TCP Handshake**                   | Browser initiates a TCP connection to the resolved IP (port 443 or 80) using a SYN → SYN-ACK → ACK sequence.              |
| 9    | **TLS Handshake** _(if HTTPS)_      | If HTTPS is used, browser and server exchange certificates and encryption keys to establish a secure TLS session.         |
| 10   | **HTTP Request**                    | Browser sends an HTTP GET request for the page, including headers like `Host`, `User-Agent`, etc.                         |
| 11   | **HTTP Response**                   | Server responds with an HTTP status code (e.g., `200 OK`) and sends the HTML content of the page.                         |
| 12   | **Subresource Requests**            | Browser parses the HTML and sends additional requests for stylesheets, scripts, images, fonts, etc.                       |
| 13   | **Rendering**                       | Browser constructs the DOM, CSSOM, executes JavaScript, and renders the visual page for the user.                         |
| 14   | **Connection Reuse or Closure**     | Based on HTTP version and headers, the browser may reuse or close the TCP connection for further requests.                |
# **1 - browser checks temporary internal dns cache**

**Chrome**:
Access via `chrome://net-internals/#dns`
# **2 - if not cached, browser queries OS**

# **3 - OS checks if domain name is cached**

**Windows**
```bash
ipconfig /displaydns
```
# **4 - if not cached, OS queries dns server configured**
the os sends a **DNS query** over **UDP (port 53)** or **TCP** (for larger responses or DNS-over-TLS/HTTPS) to the **configured DNS server**. This is usually:
- Your ISP's DNS
- Google DNS (8.8.8.8)      
- Cloudflare DNS (1.1.1.1)        
- Quad9 (9.9.9.9)
# **5 - the dns server performs recursive resolution**
1. Contacts a **root DNS server** (to locate TLD nameservers)
2. Contacts the **.io TLD nameserver**
3. Contacts the **authoritative nameserver for `gaethe.io`**
4. Gets the final IP address (A or AAAA record)
 see [[dns]]
# **6 - dns server sends ip address back to OS**
# **7 - OS sends the ip address back to browser**
# **8 - browser and server do TCP handshake**
browser initiates TCP connection with ip address
(usually on port **80** for HTTP or **443** for HTTPS)
#### TCP 3-Way Handshake:
1. Client → Server: **SYN**
2. Server → Client: **SYN-ACK**
3. Client → Server: **ACK**
Now a reliable connection is established.

# **9 - *browser and server do TLS handshake*
If the site uses HTTPS (which most do), a **TLS handshake** happens next:
- Browser and server agree on encryption parameters
- Server presents an SSL certificate (validated by the browser)
- A secure encrypted session is established
🔐 Result: All data exchanged is now encrypted.
# **10 - browser sends HTTP request to server**
```http
GET / HTTP/1.1
Host: gaethe.io
User-Agent: Mozilla/5.0
Accept: text/html
```
# **11 - server sends HTTP response to browser**
```http
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 1276

<html>
  <head>...</head>
  <body>...</body>
</html>
```

