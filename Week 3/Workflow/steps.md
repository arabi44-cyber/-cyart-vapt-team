# Week 3 Workflow Steps

---

## 1. Advanced Vulnerability Exploitation

### Tools

Metasploit, Python, Exploit-DB

### Steps

1. Configure vulnerable VM (Metasploitable2 or DVWA).
2. Identify a client-side XSS vulnerability.
3. Chain XSS → CSRF → Session Hijacking.
4. Use the stolen session to trigger RCE via Metasploit.
5. Modify an Exploit-DB PoC:
   - Update headers
   - Change payload
   - Fix version detection
6. Document:
   - Steps
   - Screenshots
   - Payloads
   - Result (Meterpreter session)

---

## 2. Web Application Penetration Testing

### Tools

Burp Suite, SQLMap, OWASP ZAP, Nikto

### Steps

1. Scan target using Nikto.
2. Use SQLMap on login form.
3. Perform manual XSS testing.
4. Test session weaknesses via Burp Suite.
5. Document vulnerabilities:
   - Description
   - Severity
   - Screenshots
   - Exploitation steps

---

## 3. Reporting Practice

### Steps

1. Create PTES-style report.
2. Add:
   - Executive Summary
   - Technical Findings
   - Impact Analysis
   - Remediation Plan
3. Create Draw.io attack-flow diagram.
4. Export as PDF.
5. Upload to `Documentation/PDFs`.

---

## 4. Post-Exploitation & Evidence Collection

### Tools

Meterpreter, Volatility, Wireshark

### Steps

1. Gain shell → elevate privileges.
2. Dump hashes / tokens.
3. Capture network traffic (Wireshark).
4. Hash evidence using SHA256.
5. Document everything in Notes + Screenshots.

---

## 5. Full VAPT Cycle (Capstone)

### Tools

Kali Linux, Metasploit, OpenVAS

### Steps

1. Run OpenVAS scan.
2. Select exploitable vulnerability.
3. Exploit via Metasploit.
4. Validate exploit success.
5. Document PTES report (200 words).
6. Add non-technical summary (100 words).
7. Export report → save in PDFs folder.

---
