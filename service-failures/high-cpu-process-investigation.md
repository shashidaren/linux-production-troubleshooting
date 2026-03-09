# High CPU Usage Investigation

## Problem

A production Linux server experienced high CPU usage affecting application performance.

---

## Environment

Linux server running production workloads.

---

## Investigation

Check system load.

uptime

Identify CPU-consuming processes.

top

List processes sorted by CPU usage.

ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head

---

## Root Cause

A runaway application process was consuming excessive CPU resources.

---

## Resolution

Restart the affected service.

systemctl restart application_service

---

## Result

CPU usage returned to normal levels and system performance stabilized.

