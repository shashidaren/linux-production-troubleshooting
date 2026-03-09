# Emergency Disk Cleanup

## Purpose

Procedure to quickly free disk space during critical disk usage incidents.

---

## Check Disk Usage

df -h

---

## Identify Large Directories

du -ahx / | sort -rh | head -20

---

## Identify Large Files

find / -type f -size +500M

---

## Check Deleted Files Still Consuming Space

lsof | grep deleted

---

## Remove Temporary Files

rm -rf /tmp/*

---

## Rotate Logs

logrotate -f /etc/logrotate.conf

---

## Verify Disk Space Recovery

df -h

