# DNS Forward and Reverse Lookup Validation

## Problem

Servers were experiencing connectivity issues related to DNS resolution.

---

## Environment

Linux infrastructure using internal DNS servers.

---

## Investigation

Check forward DNS lookup.

dig hostname.example.com

Check reverse DNS lookup.

dig -x 192.168.1.10

Verify hostname resolution.

nslookup hostname.example.com

---

## Root Cause

DNS records were inconsistent between forward and reverse zones.

---

## Resolution

Correct DNS zone entries to ensure forward and reverse records match.

---

## Result

DNS resolution was restored and applications dependent on hostname resolution began functioning normally.

