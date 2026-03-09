# Disk Space Issue Caused by Deleted Files

## Problem

A Linux production server reported very high disk usage.  
Applications began failing due to insufficient disk space.

---

## Environment

Linux server (RHEL / Oracle Linux)

Production environment

Application and log processing workloads

---

## Investigation

First, verify filesystem usage.

df -h

This confirmed that the root filesystem was almost full.

Next, identify large directories.

du -ahx / | sort -rh | head -20

However, deleting several large log files did not immediately free disk space.

To investigate further, check for deleted files still held by running processes.

lsof | grep deleted

This revealed that some processes still had open file descriptors referencing deleted log files.

---

## Root Cause

When a file is deleted but still open by a running process, the disk space is not released until the process closes the file handle or is restarted.

The application had open file handles pointing to deleted log files.

---

## Resolution

Restart the affected service to release the file handles.

systemctl restart application_service

Alternatively, restarting the application process also resolves the issue.

---

## Result

Disk space was immediately reclaimed after restarting the service.

Filesystem usage returned to normal and application functionality was restored.

---

## Lessons Learned

Large log files should be rotated properly using logrotate.

Regular disk monitoring should be implemented to detect disk usage spikes early.

