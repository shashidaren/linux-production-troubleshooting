# INCIDENT-010: Filesystem Corruption Recovery

## Summary

A Linux server failed to mount a filesystem after an unexpected shutdown.

The system reported filesystem errors and the affected volume could not be accessed.

---

## Impact

Applications relying on the affected filesystem failed to start.

Data stored on the volume became temporarily inaccessible.

---

## Detection

System logs reported filesystem errors during boot.

Example errors observed in logs:

EXT4-fs error
filesystem needs recovery

---

## Investigation

Check system logs.

journalctl -xe

Check disk devices.

lsblk

Attempt to mount filesystem.

mount /dev/sdb1 /mnt

Mount failed due to filesystem inconsistencies.

Run filesystem check.

fsck /dev/sdb1

---

## Root Cause

The server experienced an unclean shutdown which caused filesystem inconsistencies.

This resulted in corruption within filesystem metadata.

---

## Resolution

Run filesystem repair.

fsck -y /dev/sdb1

After repair, remount the filesystem.

mount /dev/sdb1 /mnt

Verify filesystem integrity.

df -h

---

## Outcome

Filesystem was successfully repaired and mounted.

Applications were able to access data normally.

---

## Preventive Measures

Ensure proper shutdown procedures.

Monitor hardware health and disk errors.

Use journaling filesystems and regular backups.

---

## Lessons Learned

Unexpected shutdowns can lead to filesystem corruption.

Regular monitoring and backups reduce the risk of data loss.

