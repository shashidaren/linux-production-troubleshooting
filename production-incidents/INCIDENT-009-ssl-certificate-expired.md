# INCIDENT-009: SSL Certificate Expired

## Summary

Users reported security warnings when accessing a web application over HTTPS.

Browsers displayed certificate errors indicating the SSL certificate had expired.

---

## Impact

Users could not securely access the application.

Browsers blocked or warned about the connection.

API integrations using HTTPS also failed.

---

## Detection

Monitoring alerts detected HTTPS endpoint failures.

Users reported browser warnings indicating an expired certificate.

---

## Investigation

Check HTTPS connectivity.

curl -I https://example.com

Inspect SSL certificate using OpenSSL.

openssl s_client -connect example.com:443

Check certificate expiration date.

openssl s_client -connect example.com:443 2>/dev/null | openssl x509 -noout -dates

Verify certificate configuration on the web server.

Check web server configuration files.

---

## Root Cause

The SSL certificate installed on the web server had expired.

Certificate renewal was not completed before the expiration date.

---

## Resolution

Renew the SSL certificate using the certificate provider.

Install the updated certificate on the web server.

Restart the web service.

systemctl restart nginx

Verify certificate installation.

openssl s_client -connect example.com:443

---

## Outcome

HTTPS access was restored.

Users were able to access the application securely without warnings.

---

## Preventive Measures

Implement automated certificate renewal.

Add monitoring alerts for certificate expiration.

Maintain certificate inventory with expiration tracking.

---

## Lessons Learned

SSL certificate expiration can cause service outages.

Automated renewal and monitoring are critical for preventing certificate-related incidents.

