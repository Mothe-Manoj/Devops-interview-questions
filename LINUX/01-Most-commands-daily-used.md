### What are 10 Linux commands you use daily? 

excluding the basics like cd, ls, and pwd


1. tail -f /var/log/nginx/error.log

- Monitor log files in real time — very useful for debugging issues as they happen.

2. grep -i "timeout" /var/log/app.log

- Search through files, logs, or command outputs for specific patterns. I use this to quickly isolate errors

3. systemctl restart nginx

- Control system services — starting, stopping, checking status of systemd services.

4. journalctl -u docker.service -f

- View logs for systemd-managed services. Especially handy for debugging issues with services like Docker or Kubelet.

5. ps aux | grep nginx

- List running processes. I use this to find rogue or resource-intensive processes.

6. ```
    df -h       # Check available disk space  
   du -sh *    # See folder sizes in current directory
   ```

7. ```
    chmod +x deploy.sh  
    chown ubuntu:ubuntu script.sh
    ```

- Manage file permissions and ownership — very common in CI/CD and provisioning tasks.

8. find /var/log -name "*.log" -mtime +7

- Locate files based on name, date, type, etc. Great for automating cleanup or audits.

9. curl -I http://localhost:8080

- Test web endpoints, APIs, or service availability from the command line.

10. rsync -avz /app/ user@server:/backup/

- Efficient file syncing and backup — much faster and more reliable than scp for large directories.


