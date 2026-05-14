### When using curl, the request works with an IP address but fails when using the domain name.


This scenario points to a DNS resolution problem — your system can reach the server IP directly, but it cannot translate the domain name into an IP.

### 1. DNS Not Resolving
- Your system cannot resolve example.com to its IP.
- Run:
    ```
    nslookup example.com
    dig example.com
    ```
- If these fail, DNS is the root issue.

### 2. Wrong or Missing DNS Configuration
- Check /etc/resolv.conf (Linux) to ensure a valid DNS nameserver (e.g., 8.8.8.8) is present.

### 3. Firewall or Network Blocking DNS
- Port 53 (used for DNS) might be blocked.
- Test with:
    - dig example.com @8.8.8.8

## Fix
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
```