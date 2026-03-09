# Mail Queue Flush Procedure

## Purpose

Procedure to flush mail queue on SMTP servers.

---

## Check Queue Size

mailq

or

postqueue -p

---

## Inspect Mail Logs

tail -f /var/log/maillog

---

## Flush Mail Queue

postqueue -f

---

## Remove Specific Messages

postsuper -d ALL

---

## Verify Queue Cleared

mailq

