# Week 3 – VAPT Practical Tasks

---

# 1. Advanced Exploitation Lab

## Tools

Metasploit, Python, Exploit-DB PoCs, Burp Suite, Tamper scripts

---

# 1.1 Activities Performed

- File Upload → Reverse Shell → Full RCE (DVWA – Metasploitable2)
- ProFTPD mod_copy exploitation for remote shell (Metasploitable3)
- phpMyAdmin preg_replace exploit → Meterpreter
- Drupalgeddon → Remote Code Execution
- Customized Python PoC for CVE‑2021‑22205 (GitLab RCE)
- Verified all incoming shells using msf multi/handler

---

## 1.2 Exploit Log

| Exploit ID | Description                         | Target IP    | Status  | Payload                     |
| ---------- | ----------------------------------- | ------------ | ------- | --------------------------- |
| 004        | File Upload → RCE Chain             | 192.168.0.11 | Success | exploit.php                 |
| 011        | ProFTPD mod_copy Backdoor → RCE     | 192.168.1.11 | Success | cmd/unix/reverse_python     |
| 012        | phpMyAdmin Auth Bypass → File Write | 192.168.1.11 | Success | php/meterpreter_reverse_tcp |
| 013        | Drupalgeddon2 Remote Code Execution | 192.168.1.11 | Success | php/meterpreter_reverse_tcp |

---

## 1.3 Custom PoC Modification Summary

The Exploit‑DB Python PoC was customized to match the target environment by modifying request headers, rewriting vulnerable parameters, and adding a custom reverse shell payload compatible with the Metasploit multi/handler. Endpoint paths were adapted to the lab systems, timing was tuned for stability, and verbose error handling plus response validation were added. Logging and payload generation were enhanced to ensure reliable exploitation across multiple hosts.

---

# 2. Web Application Testing Lab

## Tools

Burp Suite, SQLMap, OWASP ZAP, Nikto, Nmap Web Scripts

---

## 2.1 Activities

- SQL injection enumeration
- Reflected & Stored XSS testing
- CSRF checks
- Business logic flaw testing
- Cookie security analysis
- Session fixation checks
- ***

## 2.2 Expanded Test Log

| Test ID | Vulnerability                           | Severity     | Target URL                                  |
| ------- | --------------------------------------- | ------------ | ------------------------------------------- |
| 001     | SQL Injection – Login (Manual)          | **Critical** | http://192.168.0.12/login.php               |
| 002     | SQL Injection – Login (sqlmap)          | **Critical** | http://192.168.0.12/login.php               |
| 003     | SQL Injection – GET (Manual)            | **Critical** | http://192.168.0.12/vulnerabilities/sqli/   |
| 004     | Command Injection (exec)                | **Critical** | http://192.168.0.12/vulnerabilities/exec/   |
| 005     | File Upload Bypass (RCE Upload)         | **Critical** | http://192.168.0.12/vulnerabilities/upload/ |
| 006     | Weak Authentication (Password Guessing) | **High**     | http://192.168.0.12/login.php               |
| 007     | Insecure Cookie Flags                   | **High**     | http://192.168.0.12/                        |
| 008     | OWASP ZAP Active Scan                   | **High**     | http://192.168.0.12/                        |
| 009     | XSS – Reflected                         | **Medium**   | http://192.168.0.12/vulnerabilities/xss_r/  |
| 010     | Missing Security Headers                | **Medium**   | http://192.168.0.12/ (All responses)        |
| 011     | Burp Manual Interception Test           | **Info**     | http://192.168.0.12/                        |

---

# 3. Reporting Practice

## 3.1 Activities

- Prepared full PTES report
- Exported diagrams from Draw.io
- Added screenshots of exploits
- Mapped each vulnerability to CVSS
- Provided business impact analysis

---

### Findings Table

| Finding ID | Vulnerability                           | CVSS Score | Impact Summary                                              | Remediation                                              |
| ---------- | --------------------------------------- | ---------- | ----------------------------------------------------------- | -------------------------------------------------------- |
| F001       | SQL Injection – Login (Manual/Tool)     | 9.8        | Full DB compromise, credential dump, admin takeover         | Use parameterized queries, validate input, apply WAF     |
| F002       | SQL Injection – GET (Manual)            | 9.8        | Remote DB access, information leakage, full data extraction | Sanitize GET parameters, enforce strict filtering        |
| F003       | Command Injection (exec)                | 10.0       | Full system compromise, remote shell execution              | Disable dangerous PHP functions, validate OS commands    |
| F004       | File Upload Bypass → RCE                | 9.9        | Webshell upload → server takeover                           | Restrict file types, disable script execution in uploads |
| F005       | Weak Authentication (Password Guessing) | 7.5        | Accounts can be brute-forced easily                         | Enforce strong passwords, enable rate limiting, add MFA  |
| F006       | Insecure Cookie Flags                   | 7.2        | Session hijacking due to missing Secure/HttpOnly            | Add Secure, HttpOnly & SameSite flags                    |
| F007       | Missing Security Headers                | 6.5        | XSS risk, clickjacking, fingerprinting                      | Add CSP, X-Frame-Options, X-Content-Type-Options         |
| F008       | Reflected XSS                           | 6.8        | Session theft, user impersonation                           | Encode output, validate and sanitize input               |
| F009       | OWASP ZAP High Findings                 | 7.0        | Information leakage and misconfigurations                   | Patch server headers & harden configuration              |
| F010       | Burp Manual Interception Test           | Info       | HTTP request behavior observed                              | No remediation needed (informational)                    |

---

# 4. Post-Exploitation & Evidence Collection

## Tools

Meterpreter, PowerShell, Volatility, Wireshark

---

## 4.1 Actions Performed

- Privilege escalation
- LSASS dump extraction
- Network traffic capture
- File hashing for integrity
- RAM dump created

---

### Evidence Log

| Item                   | Description           | Collected By | Date       | Hash (SHA256)                                                    |
| ---------------------- | --------------------- | ------------ | ---------- | ---------------------------------------------------------------- |
| Traffic Log            | HTTP/HTTPS capture    | VATP         | 2025-11-27 | 7ad7dc4d65527dd548a42171558f5823fcdceb580b2a4d8c9d65ffcb458bf56a |
| screenshot             | credentials shot      | VAPT         | 2025-11-28 | eb2d5bae7a08b49af73e7bb1fe5d3e804ff3eeeab9dd55c2864c30d31219816b |
| metasploit_session.log | Credential extraction | VAPT         | 2025-11-27 | 5910bb3341c0b732f4abeadf5e13eeaf4587ec812d6a2a6945a69b53269da6af |
| Target_hash.txt        | tagrget file hashes   | VAPT         | 2025-11-28 | e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 |

---

# 5. Capstone Project – Full VAPT Simulation

## Tools

Kali Linux, OpenVAS, Metasploit, Burp Suite, Draw.io

---

## 5.1 Activities

- Performed network recon
- Scanned with OpenVAS
- Exploited Drupalgeddon RCE
- Uploaded post-exploitation agent
- Gained root privileges
- Created PTES report

---

# OpenVAS + Manual Exploitation Detection Log

### Target: 192.168.1.11

---

## Detection Log (Combined PTES-Aligned Findings)

| Timestamp           | Target IP    | Vulnerability / Detection                         | CVSS | Severity | PTES Phase   |
| ------------------- | ------------ | ------------------------------------------------- | ---- | -------- | ------------ |
| 2025-11-28 13:00:00 | 192.168.1.11 | ProFTPD mod_copy Backdoor → Remote Code Execution | 10.0 | Critical | Exploitation |
| 2025-11-28 13:05:10 | 192.168.1.11 | phpMyAdmin Authentication Bypass → File Write     | 10.0 | Critical | Exploitation |
| 2025-11-28 13:12:40 | 192.168.1.11 | Drupalgeddon2 Remote Code Execution               | 9.8  | Critical | Exploitation |

---

## OpenVAS Vulnerability Scan Findings

| Target IP    | Vulnerability                        | CVSS | Severity | PTES Phase             |
| ------------ | ------------------------------------ | ---- | -------- | ---------------------- |
| 192.168.1.11 | Multiple High-Risk Service Exposures | 10   | Critical | Vulnerability Analysis |
| 192.168.1.11 | Critical Remote Exposure             | 10   | Critical | Vulnerability Analysis |
| 192.168.1.11 | RCE-Capable Service                  | 10   | Critical | Vulnerability Analysis |
| 192.168.1.11 | Severe Remote Attack Surface         | 9.8  | Critical | Vulnerability Analysis |
| 192.168.1.11 | High-Risk Configuration Exposure     | 8.1  | High     | Vulnerability Analysis |
| 192.168.1.11 | Weak Security Control (Multiple)     | 7.5  | High     | Vulnerability Analysis |
| 192.168.1.11 | Weak Security Control (Multiple)     | 7.5  | High     | Vulnerability Analysis |
| 192.168.1.11 | Weak Security Control (Multiple)     | 7.5  | High     | Vulnerability Analysis |
| 192.168.1.11 | Weak Security Control (Multiple)     | 7.5  | High     | Vulnerability Analysis |
| 192.168.1.11 | Weak Security Control (Multiple)     | 7.5  | High     | Vulnerability Analysis |
| 192.168.1.11 | Medium Risk Exposure                 | 6.1  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Risk Exposure                 | 6.1  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 5.3  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 5.3  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 5.0  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 5.0  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 5.0  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 4.8  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 4.8  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 4.3  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 4.3  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 4.3  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Medium Exposure                      | 4.3  | Medium   | Vulnerability Analysis |
| 192.168.1.11 | Low Severity Exposure                | 2.6  | Low      | Vulnerability Analysis |
| 192.168.1.11 | Low Severity Exposure                | 2.6  | Low      | Vulnerability Analysis |
| 192.168.1.11 | Low Severity Exposure                | 2.1  | Low      | Vulnerability Analysis |

---

## Severity Count Summary

| Severity         | Count |
| ---------------- | ----- |
| Critical (10-8)  | 5     |
| High (7.9-7.0)   | 5     |
| Medium (6.1-4.3) | 13    |
| Low (2.6-2.1)    | 3     |

---

# End of Practical Notes
