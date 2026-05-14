### Your website is returning a 502 Bad Gateway HTTP status code.

A 502 Bad Gateway error means that a gateway or proxy server (like NGINX, HAProxy, or AWS ELB) got an invalid response from the upstream server (like an app server or container).


- A 502 error is returned when the reverse proxy or load balancer is unable to reach the backend service or gets a malformed response.

- Think of it as:
    - "The gatekeeper tried to contact the backend service — but something was wrong or unreachable."

**1. Backend Service is Down**
- App server (e.g., Node.js, Python, Java) is not running.
- Restart it:
    - systemctl status your-app

2. Wrong Upstream Configuration in NGINX
- NGINX is trying to proxy to the wrong port or host.
- Check nginx.conf or site config:
    - proxy_pass http://localhost:5000;

3. Backend is Too Slow / Times Out
- Backend takes too long to respond.
- Adjust timeouts:
    - proxy_read_timeout 60s;

4. Firewall or Security Group Blocking
- Backend port (e.g., 3000, 5000) is blocked.
- Use telnet or nc to verify:
    ```nc -zv localhost 5000```
5. Incorrect SSL Termination
- NGINX expects HTTP but backend speaks HTTPS (or vice versa).
- Fix proxy_pass protocol (http:// vs https://).
6. App Crashed or Out of Memory
- App logs show OOMKilled, panic, or crash.
- Check logs:
```
    journalctl -u your-app
    docker logs your-container
```


## How to Troubleshoot
- Check NGINX error logs
```tail -f /var/log/nginx/error.log```
- Restart app & NGINX
```
systemctl restart your-app
systemctl restart nginx
```
- Check App Health Endpoint
    - Test directly with curl:
    ```curl http://localhost:5000/health```