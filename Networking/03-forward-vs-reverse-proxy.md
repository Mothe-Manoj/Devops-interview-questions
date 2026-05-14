### Explain the difference between a Forward Proxy and a Reverse Proxy.

Both proxies act as intermediaries in network communication, but they sit at different ends of the request flow and serve different purposes.

### Forward Proxy
- Between client and the internet
- Acts on behalf of the client

1. A forward proxy is used by clients to access external servers.
2. The target server only sees the proxy, not the real client.
3. Often used in corporate environments or VPNs to filter or restrict internet access.


## Reverse proxy

- Between internet and the server
- Acts on behalf of the server
```
                  - Bypass firewalls  
                  - Control access (e.g., parental control)  
                  - Caching outgoing requests  
                  | - Load balancing  
                  - SSL termination  
                  - Caching incoming responses  
                  - Protect internal servers 
```

1. A reverse proxy sits in front of a group of servers and routes client requests to them.
2. The client thinks it's talking directly to the server, but it's talking to the proxy.
3. Used for load balancing, security, and SSL offloading.

**Client → Forward Proxy → Google | User → Reverse Proxy → Internal Web Server**


### Forward Proxy:
A school uses a proxy server to prevent students from accessing YouTube.

### Reverse Proxy:
A company uses NGINX as a reverse proxy to distribute requests to multiple backend services (e.g., /api, /auth, /app).

