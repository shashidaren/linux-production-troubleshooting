# Disk Recovery Using ddrescue

## Problem

A failing disk contained important data that needed to be recovered.

---

## Environment

Linux recovery system

Failing disk device

---

## Investigation

Identify disk device.

lsblk

Confirm disk errors using system logs.

dmesg

---

## Resolution

Create disk image using ddrescue.

ddrescue -d -r 3 /dev/sdb recovered_disk.img recovery.log

Mount recovered image for analysis.

mount recovered_disk.img /mnt/recovery

---

## Result

Data successfully recovered from failing disk.

