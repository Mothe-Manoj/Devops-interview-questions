### How do you get the list of users who logged into the system today?

``` last | grep "$(date '+%a %b %e')" | awk '{print $1}' | sort | uniq ```

## Breakdown:
last: Displays recent login history from /var/log/wtmp.
date '+%a %b %e':
Outputs today’s date in the format used by last, e.g., Thu Jun 13.
%a = abbreviated weekday, %b = abbreviated month, %e = day of month (with space-padding).
grep "$(date ...)": Filters only login entries for today.
awk '{print $1}': Extracts the usernames from the matched lines.
sort | uniq: Removes duplicates to show unique users who logged in today.
