# INCIDENT-003: Network Timeout Issue

## Summary

Application servers experienced intermittent connectivity issues when communicating with a backend service.

---

## Impact

Application requests failed intermittently.

Users reported timeouts.

---

## Detection

Monitoring alerts indicated increased network latency.

---

## Investigation

Verify connectivity.

ping backend-server

Check open ports.

ss -tuln

Capture traffic using tcpdump.

tcpdump -i eth0 host backend-server

---

## Root Cause

Firewall rules blocked traffic between application and backend servers.

---

## Resolution

Firewall rules updated to allow required communication ports.

---

## Outcome

Application connectivity restored and errors stopped.

---

## Preventive Measures

Review firewall rule change procedures.

Add connectivity checks in monitoring systems.

