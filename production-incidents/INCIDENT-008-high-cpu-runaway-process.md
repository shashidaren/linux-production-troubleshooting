# INCIDENT-008: High CPU Runaway Process

## Summary

A production Linux server experienced high CPU utilization which caused application performance degradation and slow system response.

---

## Impact

Applications became slow to respond.

System load increased significantly.

Users reported delays in processing requests.

---

## Detection

Monitoring alerts reported CPU usage above 90%.

System load average increased significantly.

Example command used:

uptime

---

## Investigation

Check system load.

uptime

Identify processes consuming CPU.

top

Sort processes by CPU usage.

ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head

Identify the offending process and process ID (PID).

Check process details.

ps -fp <PID>

---

## Root Cause

A runaway application process entered an infinite loop which consumed excessive CPU resources.

This caused system load to spike and impacted other running services.

---

## Resolution

Terminate the problematic process.

kill -9 <PID>

Restart the affected service.

systemctl restart application_service

Monitor system performance after restart.

top

---

## Outcome

CPU utilization returned to normal levels.

System performance stabilized and applications resumed normal operation.

---

## Preventive Measures

Implement application monitoring for abnormal CPU usage.

Add alerts for sustained high CPU utilization.

Investigate application code to prevent infinite loops.

---

## Lessons Learned

High CPU incidents often originate from runaway processes or inefficient application behavior.

Early detection through monitoring can reduce service impact.

