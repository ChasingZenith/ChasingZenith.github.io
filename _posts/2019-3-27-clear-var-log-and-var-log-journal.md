---
layout: post
title:  "Clear /var/log and /var/log/journal"
date:   2019-3-27 20:25:20 +0800
categories: Linux log
---

# var/log

https://askubuntu.com/questions/100004/how-can-i-free-space-from-a-massive-39-5gb-var-log-folder


## /var/log/journal

https://ma.ttias.be/clear-systemd-journal/

```bash
cat /etc/systemd/journald.conf
journalctl --disk-usage
journalctl --vacuum-size=500M
journalctl --vacuum-time=30d
```

>          --disk-usage
>       Shows the current disk usage of all journal files. This shows the sum of the disk usage of all archived and active journal files.

>       --vacuum-size=, --vacuum-time=, --vacuum-files=
           Removes archived journal files until the disk space they use falls below the specified size (specified with the usual "K", "M",
           "G" and "T" suffixes), or all archived journal files contain no data older than the specified timespan (specified with the usual
           "s", "m", "h", "days", "months", "weeks" and "years" suffixes), or no more than the specified number of separate journal files
           remain. Note that running --vacuum-size= has only an indirect effect on the output shown by --disk-usage, as the latter includes
           active journal files, while the vacuuming operation only operates on archived journal files. Similarly, --vacuum-files= might not
           actually reduce the number of journal files to below the specified number, as it will not remove active journal files.
           --vacuum-size=, --vacuum-time= and --vacuum-files= may be combined in a single invocation to enforce any combination of a size, a
           time and a number of files limit on the archived journal files. Specifying any of these three parameters as zero is equivalent to
           not enforcing the specific limit, and is thus redundant.
