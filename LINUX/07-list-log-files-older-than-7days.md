
### How do you find and list the log files older than 7 days in the /var/log folder?

You can use the **find** command with the **-mtime** option to locate files older than 7 days:

```find /var/log -type f -mtime +7```

Breakdown of the command:
- find: The Linux command to search for files in a directory hierarchy.
- /var/log: The target directory that contains log files.
- -type f: Limits the search to files (not directories).
- -mtime +7: Filters files modified more than 7 days ago.
    - +7 means strictly older than 7 days.
    - -7 would mean newer than 7 days.


If you want to view the size and timestamp of those files:

```find /var/log -type f -mtime +7 -exec ls -lh {} \;```
If you want to delete those files:

```sudo find /var/log -type f -mtime +7 -delete```
⚠️ Be careful with deletion — make sure you’ve reviewed the list first.


## How do you find and remove log files older than 30 days using -exec in a folder?

```
sudo find /path/to/folder -type f -name "*.log" -mtime +30 -exec rm -f {} \;
```

### Breakdown of the command:
sudo: Used if the directory (like /var/log) requires root access.
find: The base command to search files.
/path/to/folder: Replace with your target directory (e.g., /var/log).
-type f: Ensures only files are matched.
-name "*.log": Filters files ending with .log.
-mtime +30: Filters files modified over 30 days ago.
-exec rm -f {} \;: Executes the rm -f command on each matched file:
{} gets replaced by the current file path.
\; indicates the end of the command.