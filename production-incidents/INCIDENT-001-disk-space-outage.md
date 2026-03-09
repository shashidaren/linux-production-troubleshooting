# INCIDENT-001: Disk Space Outage

## Summary

A production Linux server experienced service disruption due to disk space exhaustion.

---

## Impact

Applications running on the server failed to write logs and temporary files.

Users experienced service degradation.

---

## Detection

Monitoring alerts reported disk utilization above 95%.

---

## Investigation

Check filesystem usage.

df -h

Identify large directories.

du -ahx / | sort -rh | head -20

Check for deleted files still consuming space.

lsof | grep deleted

---

## Root Cause

A log file was deleted but still held open by a running process, preventing disk space from being released.

---

## Resolution

Restart the affected service.

systemctl restart application_service

---

## Outcome

Disk space was reclaimed and services returned to normal operation.

---

## Preventive Measures

Implement proper log rotation using logrotate.

Add monitoring alerts for disk usage thresholds.

