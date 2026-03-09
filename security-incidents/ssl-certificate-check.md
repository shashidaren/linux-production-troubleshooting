# SSL Certificate Verification

## Problem

Users reported SSL warnings when connecting to a service.

---

## Environment

Linux server hosting HTTPS services.

---

## Investigation

Check certificate details using OpenSSL.

openssl s_client -connect example.com:443

View certificate expiration date.

openssl s_client -connect example.com:443 2>/dev/null | openssl x509 -noout -dates

---

## Root Cause

SSL certificate had expired.

---

## Resolution

Renew certificate and restart web server.

systemctl restart nginx

---

## Result

SSL warnings resolved and secure connections restored.

