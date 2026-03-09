# Filesystem Recovery Using fsck

## Problem

A Linux server failed to mount a filesystem after an unexpected shutdown.

---

## Environment

Linux server with ext filesystem.

---

## Investigation

Attempt to mount the filesystem.

mount /dev/sdb1 /mnt

Mount failed due to filesystem inconsistencies.

Run filesystem check.

fsck -y /dev/sdb1

---

## Root Cause

Filesystem corruption caused by improper shutdown or disk error.

---

## Resolution

Repair filesystem using fsck.

fsck -y /dev/sdb1

After repair, mount filesystem again.

mount /dev/sdb1 /mnt

---

## Result

Filesystem successfully repaired and mounted.

