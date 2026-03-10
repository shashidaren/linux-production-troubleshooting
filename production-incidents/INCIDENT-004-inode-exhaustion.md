# INCIDENT-004: Disk Inode Exhaustion

## Summary

A Linux production server reported "disk full" errors even though disk usage appeared normal.

Applications were unable to create new files and logging services stopped functioning.

---

## Impact

Applications failed to write logs.

Temporary files could not be created.

Some background jobs failed due to filesystem write errors.

---

## Detection

Monitoring alerts indicated application failures related to filesystem write operations.

Initial checks suggested the disk still had available space.

---

## Investigation

Check filesystem disk usage.

df -h

Disk space appeared normal.

Check inode usage.

df -i

The filesystem showed 100% inode utilization.

Identify directories with large numbers of small files.

find /var -xdev -type f | wc -l

Further investigation showed log directories contained millions of small files.

---

## Root Cause

A logging process generated a large number of small files which exhausted all available filesystem inodes.

Even though disk space was available, no additional files could be created.

---

## Resolution

Remove unnecessary log files.

Clean up temporary directories.

rm -rf /var/log/application/*

Restart affected services.

systemctl restart application_service

---

## Outcome

Inodes were freed and applications resumed normal operation.

Filesystem functionality returned to normal.

---

## Preventive Measures

Implement log rotation using logrotate.

Monitor inode usage in addition to disk usage.

Add alerts for inode utilization thresholds.

---

## Lessons Learned

Disk monitoring must include inode usage metrics.

Large numbers of small files can exhaust inodes even when disk space is available.

