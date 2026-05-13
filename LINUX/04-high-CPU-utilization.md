### Linux Server is slow due to high CPU utilization. How will you fix it?

I would begin by identifying which processes are consuming the most CPU using tools like top, htop, or pidstat, then analyze whether it's due to a misbehaving application, runaway process, or scheduled job. Based on the findings, I’d take corrective action — either by killing the process, adjusting resource limits, or scaling the workload.

### Step 1: Check Load Average

```
uptime

14:02:03 up  3 days,  4:55,  2 users,  load average: 6.02, 4.33, 2.89

```

A load average consistently higher than the number of CPU cores indicates overutilization.


### Step 2: Identify CPU-Heavy Processes

``` top -o %CPU ```
or

``` htop ```

### Step 3: Drill Down with ps or pidstat

``` ps -eo pid,ppid,cmd,%cpu,%mem --sort=-%cpu | head```

These give detailed insight into CPU consumption over time.

### Step 4: Investigate the Cause
Based on what you see, ask:

Is it a specific app (e.g., Java, Python, Node.js)?
Is there a cron job or batch script running?
Is a service misconfigured and looping?
Is it caused by a known bug (e.g., zombie processes)?

### Step 5: Take Corrective Action
Kill or restart runaway process:

kill -9 <pid>
systemctl restart <service>

### Step 6: Implement Preventive Measures
Set CPU/memory limits in containerized apps
Use monitoring tools like Prometheus + Grafana
Configure alerts for high CPU (e.g., above 80% for 5 mins)
Refactor long-running or expensive tasks

## Real-Life Examples:
A cron script looping due to a bad condition
A Java app stuck in infinite recursion
Docker containers running unbounded scraping jobs
Antivirus or audit daemon consuming CPU after log floods
