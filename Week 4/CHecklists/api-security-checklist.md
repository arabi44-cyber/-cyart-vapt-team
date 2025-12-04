# API Security Checklist

## 1. Recon & Enumeration

- [x] Identified accessible API endpoints using browser & Burp Suite
- [x] Verified request / response structure for each endpoint
- [x] Enumerated API parameters via Postman & Burp Proxy
- [x] Checked HTTP request methods allowed (GET/POST)
- [x] Reviewed cookies & session tokens

---

## 2. Authentication & Authorization

- [x] Tested login mechanism via Postman
- [x] Verified password submission & token handling
- [x] Attempted access to `/api/users/2` using another session (BOLA Test)
- [x] Checked session persistence after logout
- [ ] Tested MFA / rate limit (Not applicable in DVWA)

---

## 3. Broken Object Level Authorization (BOLA)

- [x] Used Postman to modify user ID parameter
- [x] Accessed user data without permission
- [x] Confirmed no server-side ownership validation

---

## 4. Injection (SQLi)

- [x] Tested manual payloads: `?id=1'--`, `OR 1=1--`, `UNION SELECT`
- [x] Automated exploitation using `sqlmap`
- [x] Extracted database details: DB=dvwa, Table=users
- [ ] WAF/Firewall check (Not implemented in DVWA)

---

## 5. Cross-Site Request Forgery (CSRF)

- [x] Accessed `/vulnerabilities/csrf/` password change endpoint
- [x] Observed missing anti-CSRF validation at low security
- [x] Demonstrated password change without token
- [ ] Tested secure level implementation

---

## 6. Broken Authentication

- [x] Tested login brute-force feasibility
- [ ] Wordlist attack via Hydra/Burp Intruder (not executed)

---

## 7. Security Misconfiguration

- [x] Checked server headers
- [x] Found Apache default response
- [x] Observed no security headers (HSTS, CSP, X-Frame-Options)
- [ ] Certificate validation (HTTP only - no SSL)

---

## 8. Sensitive Data Exposure

- [x] Database dump exposed stored credentials
- [x] Passwords stored in plain MD5 hash
- [ ] Encryption evaluation (not present)

---

## 9. Rate Limiting

- [ ] Tested with Intruder/Repeater automation

---

## 10. Logging & Monitoring

- [ ] No alert/flag for repetitive SQL payloads
- [ ] No session anomaly detection

---

### Status:

🟢 Completed tests  
🟡 Optional tests pending  
🔴 No security mechanisms found (expected for DVWA)
