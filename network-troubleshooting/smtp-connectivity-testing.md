# SMTP Connectivity Testing

## Problem

Email delivery issues were reported and SMTP connectivity needed to be verified.

---

## Environment

Linux mail relay server

SMTP infrastructure

---

## Investigation

Check connectivity to SMTP port.

telnet mailserver.example.com 25

Test SMTP session manually.

helo example.com
mail from:<test@example.com>
rcpt to:<user@example.com>
data
subject: test message

test message
.

quit

Verify if server accepts connections and processes mail commands correctly.

---

## Root Cause

SMTP relay configuration issue prevented messages from being accepted.

---

## Resolution

Corrected mail relay configuration in mail server settings.

---

## Result

Email delivery was successfully restored.

