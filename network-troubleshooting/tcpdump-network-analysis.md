# Network Traffic Analysis Using tcpdump

## Problem

An application was unable to communicate with a remote server. Network connectivity needed to be verified.

---

## Environment

Linux server

Production environment

---

## Investigation

Verify basic connectivity.

ping remote-server

Check open ports.

ss -tuln

Capture network traffic using tcpdump.

tcpdump -vvv -n -i eth0 host <destination_ip>

Capture specific port traffic.

tcpdump -i eth0 port 443

Analyze packets to confirm if traffic is leaving the server and if responses are received.

---

## Root Cause

Traffic was blocked by firewall rules on the destination system.

---

## Resolution

Firewall rules were updated to allow required traffic.

---

## Result

Network communication was successfully restored.

