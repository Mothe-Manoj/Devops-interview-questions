### You are asked to monitor multiple services like nginx, sshd, and docker.

Write a shell script that checks the status of each service.
If a service is stopped, attempt to restart it.
Print a clearly formatted report.

## Shell Script: multi_service_monitor.sh

```
#!/bin/bash

# List of services to monitor
services=("nginx" "sshd" "docker")

# Report Header
echo "-----------------------------------"
echo "  Service Health Check Report"
echo "-----------------------------------"

# Loop through services
for service in "${services[@]}"; do
  if systemctl is-active --quiet "$service"; then
    echo "$service is ✅ RUNNING"
  else
    echo "$service is ❌ STOPPED"
    echo ""
    echo "Attempting to restart $service..."

    systemctl restart "$service" &> /dev/null

    # Check if restart was successful
    if systemctl is-active --quiet "$service"; then
      echo "$service has been ✅ restarted successfully."
    else
      echo "❌ Failed to restart $service. Manual intervention needed."
    fi
  fi
  echo "-----------------------------------"
done

```
## Detailed Explanation
- services=(...): An array of services to monitor.
- systemctl is-active: Checks if a service is running.
- systemctl restart: Tries to restart the service if it's not active.
- Conditional Restart Check: After restarting, the script confirms whether the service started successfully.
- Output Formatting: Clean section dividers and emojis provide clarity in console or logs.

To run every 10 minutes:

``` */10 * * * * /path/to/multi_service_monitor.sh >> /var/log/service_check.log 2>&1```