# Disk Inode Exhaustion

## Problem

Server reported disk full errors even though disk usage appeared normal.

---

## Environment

Linux server with large number of small files.

---

## Investigation

Check disk usage.

df -h

Check inode usage.

df -i

Identify directories containing large numbers of files.

find / -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n

---

## Root Cause

Millions of small files consumed all available inodes on the filesystem.

---

## Resolution

Remove unnecessary small files.

Implement log rotation and cleanup scripts.

---

## Result

Inodes were freed and normal system operation resumed.

