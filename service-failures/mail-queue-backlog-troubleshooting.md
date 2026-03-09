# Mail Queue Backlog Troubleshooting

## Problem

A mail relay server began experiencing delayed email delivery due to a rapidly growing mail queue.

---

## Environment

Linux SMTP relay server

Postfix mail infrastructure

---

## Investigation

Check mail queue size.

mailq

Or:

postqueue -p

Inspect mail logs.

tail -f /var/log/maillog

Identify deferred messages.

grep deferred /var/log/maillog

Test SMTP connectivity to destination mail servers.

telnet destination-mail-server 25

---

## Root Cause

Remote mail servers were rejecting or delaying connections, causing messages to accumulate in the queue.

---

## Resolution

Corrected mail routing configuration and verified outbound SMTP connectivity.

Flushed the mail queue.

postqueue -f

---

## Result

Mail queue processed successfully and normal email delivery resumed.

