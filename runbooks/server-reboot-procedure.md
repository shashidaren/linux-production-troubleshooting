# Server Reboot Procedure

## Purpose

This runbook describes the standard procedure for safely rebooting a Linux production server.

---

## Pre-checks

Verify system load.

uptime

Check active users.

who

Check running services.

systemctl list-units --type=service --state=running

---

## Notify Users

Inform stakeholders before rebooting production systems.

---

## Verify Disk Status

Ensure no filesystem errors.

df -h

---

## Reboot Server

Initiate reboot.

sudo reboot

---

## Post-Reboot Verification

Check system uptime.

uptime

Verify critical services.

systemctl status service_name

Confirm application functionality.

---

## Rollback

If services fail to start after reboot, review logs.

journalctl -xe

