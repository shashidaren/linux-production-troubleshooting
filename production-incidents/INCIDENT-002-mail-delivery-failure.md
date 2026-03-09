# INCIDENT-002: Mail Delivery Failure

## Summary

Users reported delayed email delivery due to mail queue buildup on the relay server.

---

## Impact

Emails were delayed and some outbound messages remained in the queue.

---

## Detection

Mail monitoring system detected a rapidly increasing mail queue.

---

## Investigation

Check mail queue.

mailq

Inspect mail logs.

tail -f /var/log/maillog

Check deferred messages.

grep deferred /var/log/maillog

Test SMTP connectivity.

telnet destination-server 25

---

## Root Cause

Remote mail servers temporarily rejected connections due to rate limiting.

---

## Resolution

Adjusted retry intervals and verified outbound connectivity.

Flush mail queue.

postqueue -f

---

## Outcome

Mail queue processed successfully and normal email delivery resumed.

---

## Preventive Measures

Improve monitoring of mail queue size.

Implement rate limiting controls.

