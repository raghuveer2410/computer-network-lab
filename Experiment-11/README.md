# Experiment 11 — HTTP and WWW Web Server Simulation

**Course:** Computer Networks Lab (ENCS304)  
**Institution:** KR Mangalam University  

---

## 🎯 Aim

Create a web server simulation to demonstrate the workings of HTTP and WWW. Implement basic HTTP request and response handling and simulate a simple web browsing session.

---

## 📌 Objective

- Understand the client-server architecture of the World Wide Web.
- Simulate HTTP GET and POST requests and responses.
- Configure a basic web server in Cisco Packet Tracer.
- Implement a simple HTTP server using Python sockets.

---

## 📖 Theory

### HTTP (HyperText Transfer Protocol)
HTTP is an application-layer protocol for transmitting hypermedia documents (HTML). It follows a stateless request-response model over TCP (port 80) or HTTPS over TLS (port 443).

### HTTP Methods
| Method | Purpose |
|--------|---------|
| GET | Retrieve a resource |
| POST | Submit data to server |
| PUT | Update a resource |
| DELETE | Delete a resource |
| HEAD | Get headers only |

### HTTP Status Codes
| Code | Meaning |
|------|---------|
| 200 OK | Request successful |
| 301 Moved Permanently | Redirect |
| 404 Not Found | Resource not found |
| 500 Internal Server Error | Server-side error |

### HTTP Request / Response Format
```
GET /index.html HTTP/1.1
Host: www.cnlab.com
User-Agent: Mozilla/5.0
Accept: text/html

HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 152

<html>...</html>
```

---

## 🖧 Network Topology

> 📷 Add screenshots below:

- `screenshots/web_server_topology.png`
- `screenshots/http_request.png`
- `screenshots/http_response.png`
- `screenshots/browser_simulation.png`

---

## 🔧 Step-by-Step Procedure

### Web Server in Cisco Packet Tracer
1. Add a Server and enable HTTP Service.
2. Edit `index.html` on the server.
3. Connect a PC via Switch to the server.
4. Open the Web Browser on the PC, type server IP (`192.168.1.100`).
5. Observe the HTTP GET request and HTML response in Simulation Mode.

### Python HTTP Server
1. Create a simple HTTP server that responds to GET requests.
2. Start the server on `localhost:8080`.
3. Open a browser and visit `http://localhost:8080`.

---

## ⚙️ Configuration Commands

```
! ---- Web Server in Packet Tracer ----
! Server > Services > HTTP: Enable
! Edit index.html with custom HTML content
! PC > Desktop > Web Browser > http://192.168.1.100
```

```python
# Simple HTTP Server (Python)
import socket

HOST = '0.0.0.0'
PORT = 8080

html_content = """<!DOCTYPE html>
<html>
<head><title>CN Lab Web Server</title></head>
<body>
    <h1>Welcome to CN Lab - Experiment 11</h1>
    <p>HTTP Server is running successfully!</p>
</body>
</html>"""

response = f"""HTTP/1.1 200 OK\r
Content-Type: text/html\r
Content-Length: {len(html_content)}\r
\r
{html_content}"""

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
server_socket.bind((HOST, PORT))
server_socket.listen(5)
print(f"HTTP Server running at http://localhost:{PORT}")

while True:
    client_socket, client_address = server_socket.accept()
    request = client_socket.recv(1024).decode()
    print(f"\nRequest from {client_address}:\n{request.splitlines()[0]}")
    client_socket.sendall(response.encode())
    client_socket.close()
```

---

## 📊 Observations / Results

> 📷 Add output screenshots in the `screenshots/` folder.

| Request | Method | URL | Response Code | Content |
|---------|--------|-----|---------------|---------|
| 1 | GET | /index.html | 200 OK | HTML Page |
| 2 | GET | /about.html | 404 Not Found | Error Page |

---

## ✅ Conclusion

This experiment successfully demonstrated the HTTP client-server model and the WWW architecture. A basic web server was configured in Cisco Packet Tracer and implemented using Python, illustrating how browsers fetch and display web content using HTTP request-response cycles.
