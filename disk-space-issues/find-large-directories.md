# Finding Large Directories Causing Disk Usage

## Problem

A Linux server reported high disk usage and required investigation to identify which directories were consuming the most space.

---

## Environment

Linux server (RHEL / Oracle Linux)

Production system

---

## Investigation

First verify filesystem usage.

df -h

Identify large directories.

du -ahx / | sort -rh | head -20

To summarize directory sizes:

du -sh /*

Check specific directories such as /var:

du -sh /var/* | sort -h

---

## Root Cause

Large log files and application data were consuming disk space.

---

## Resolution

Clean up old logs and temporary files.

Rotate logs using logrotate configuration.

---

## Result

Disk usage reduced significantly and system returned to normal operation.

