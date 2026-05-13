### How do you find and delete files larger than 100MB from a given directory?

``` find /path/to/directory -type f -size +100M -exec rm -f {} \;```


## Best Practices
Always dry-run before deleting anything in production.
Consider logging deletions or compressing instead of deleting if space permits.
Automate safely with cron jobs for specific paths, e.g., /tmp or /var/cache.