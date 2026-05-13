### /var is almost 90% full. What will be your next steps?

The /var directory is commonly used for logs, spools, caches, and runtime data — so issues here can break system processes or fill up disks silently.

My first step is to identify what’s consuming the space inside /var. Then I would clean up unnecessary files like rotated logs, caches, or orphaned packages — and put log rotation in place to avoid recurrence.

### Step 1: Inspect Disk Usage Under /var

``` sudo du -sh /var/* | sort -hr | head -10 ```

### Step 2: Clean Log Files
```
sudo journalctl --vacuum-size=200M

This tells the systemd-journald service to delete the oldest archived journal files until the total disk space used by the journal is no more than 200MB.

sudo rm -rf /var/log/*.gz /var/log/*.[0-9]

it clears the file's content without deleting the file itself or breaking the file descriptor that a running process might still be holding.

```

### Step 3: Clear Package Cache

```
sudo apt clean         # Debian/Ubuntu
sudo yum clean all     # RHEL/CentOS
```
### Step 4: Check Docker Artifacts

```
docker system df        # See what’s taking space
docker system prune -a  # Remove unused containers/images
```

### Step 5: Set Up Alerts and Monitoring