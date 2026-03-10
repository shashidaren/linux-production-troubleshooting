# INCIDENT-007: DNS Resolution Failure

## Summary

Application servers were unable to resolve hostnames for internal and external services.

This caused application connectivity failures and service disruptions.

---

## Impact

Applications could not connect to backend services using hostnames.

API requests failed due to hostname resolution errors.

Some monitoring checks also failed.

---

## Detection

Monitoring alerts indicated service connectivity failures.

Application logs showed DNS resolution errors.

Example error:

"Temporary failure in name resolution"

---

## Investigation

Test hostname resolution.

nslookup example.com

Check DNS using dig.

dig example.com

Verify DNS server configuration.

cat /etc/resolv.conf

Check configured DNS servers.

nameserver 10.x.x.x

Test network connectivity to DNS server.

ping dns-server-ip

Capture DNS traffic to verify queries.

tcpdump -i eth0 port 53

Check local DNS cache if applicable.

systemd-resolve --status

---

## Root Cause

The configured DNS server was unreachable due to a network connectivity issue.

As a result, hostname resolution failed across multiple systems.

---

## Resolution

Updated DNS configuration to use a reachable DNS server.

Edited:

/etc/resolv.conf

Restarted network services.

systemctl restart NetworkManager

Flushed DNS cache if necessary.

systemd-resolve --flush-caches

---

## Outcome

Hostname resolution was restored.

Applications resumed normal connectivity to backend services.

---

## Preventive Measures

Configure secondary DNS servers for redundancy.

Monitor DNS server availability.

Implement alerts for DNS resolution failures.

---

## Lessons Learned

DNS is a critical dependency for many services.

Redundant DNS configuration helps prevent widespread service outages.

