### Application deployed on NGINX returns "Connection Refused". How will you fix it?

### Short Explanation
This question evaluates your ability to troubleshoot reverse proxy setups and network-level issues. “Connection Refused” often means the NGINX server or upstream service isn’t reachable at all.

### Answer
I would first check whether NGINX itself is running and listening on the correct port, then verify that the application backend is also up and accessible. It could be a misconfiguration in the NGINX config or the application not listening on the expected socket or port.


### Step 1: Reproduce the Error
Try to access the app from the browser or use:

```curl -I http://localhost```
If you get:

```curl: (7) Failed to connect to localhost port 80: Connection refused```
It confirms the server refused the TCP handshake — not a 4xx/5xx error.

### Step 2: Check if NGINX is Running
``` sudo systemctl status nginx```
If it’s inactive or failed:
```
sudo systemctl restart nginx
sudo journalctl -u nginx -xe
```

### Step 3: Is NGINX Listening on the Expected Port?
```sudo netstat -tulnp | grep nginx```
or:

```ss -tuln | grep :80```
No output? Then NGINX is not listening on the port you're accessing.

### step4: Check NGINX Configuration
``` sudo nginx -t```
This tests the NGINX config for syntax errors.

Also verify your /etc/nginx/sites-enabled/default or your custom config:
```
server {
    listen 80;
    location / {
        proxy_pass http://localhost:5000;  # Is your app running here?
    }
}
```

### Step 5: Verify the Application Backend
If NGINX is trying to proxy to http://localhost:5000, is your app actually running on that port?
```
sudo netstat -tulnp | grep 5000
curl http://localhost:5000
```
If this fails, restart or debug your app.

### Step 6: Check Firewall/Security Groups (Cloud Hosts)
On cloud VMs, make sure the port is open in:

AWS Security Group
GCP firewall rules
```ufw or iptables```on the VM
```
sudo ufw status
sudo iptables -L
```

## Common Real-Life Causes:
App crashed or not listening on correct port
Wrong proxy_pass value in NGINX
Port blocked by firewall
NGINX service not restarted after config change
App takes too long to start — NGINX proxies fail