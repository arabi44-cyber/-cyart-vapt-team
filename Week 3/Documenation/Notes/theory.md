# Week 3 – VAPT Theory Notes

## 1. Advanced Vulnerability Exploitation

### 1.1 Core Concepts

**Exploit Chains**

- A technique where multiple vulnerabilities are combined to achieve a higher-impact attack.
- Example: XSS → Session Hijacking → Privilege Escalation → RCE.

**Exploit Customization**

- Modifying publicly available PoCs to fit a specific environment.
- Includes editing payloads, headers, target versions, offsets, and shellcode.

**Obfuscation Techniques**

- Methods to disguise payloads to evade detection.
- Examples:
  - Base64/URL encoding
  - Payload splitting
  - Polymorphic JavaScript
  - WAF bypass tricks

### 1.2 Learning Outcomes

- Understand multi-stage exploit chaining.
- Customize exploits for target environments.
- Utilize Python/Metasploit for advanced exploitation.

---

## 2. Web Application Penetration Testing

### 2.1 Core Concepts

**OWASP Top 10 (2021 Focus Areas)**

- A01: Broken Access Control
- A03: Injection (SQLi, NoSQL, Command)
- A04: Insecure Design
- A07: Identification & Authentication Failures
- A08: Software & Data Integrity Failures

**Testing Techniques**

- Manual testing using Burp Suite interception, replay, manipulation.
- Automated detection using sqlmap, Nikto, OWASP ZAP.

**Secure Coding Mitigations**

- Input validation
- Prepared statements
- Strong session/token management
- Proper authentication workflows

### 2.2 Learning Outcomes

- Identify and exploit web vulnerabilities.
- Evaluate authentication/authorization weaknesses.
- Apply OWASP methodologies.

---

## 3. Reporting and Stakeholder Communication

### 3.1 Core Concepts

**PTES Report Structure**

- Executive Summary
- Scope & Methodology
- Technical Findings
- Exploitation Results
- Evidence
- Remediation

**Audience Tailoring**

- Non-technical summaries for managers.
- Technical deep dives for developers.
- Severity ratings (CVSS, Impact).

**Metrics & KPIs**

- Vulnerability count
- Exploit success rate
- Time-to-remediate
- Risk severity trend

### 3.2 Learning Outcomes

- Build clear, actionable, professional reports.
- Communicate findings effectively.

---

## 4. Post-Exploitation & Evidence Collection

### 4.1 Core Concepts

- Privilege escalation (token abuse, misconfigurations)
- Credential harvesting
- Lateral movement
- Maintaining persistence
- Chain of custody for digital evidence

### 4.2 Evidence Handling

- Calculate hashes (SHA256)
- Document timestamps
- Export network captures
- Maintain forensic accuracy

---

## 5. Full VAPT Cycle (Capstone)

### 5.1 Major Phases

- Reconnaissance (active + passive)
- Scanning (Nmap, OpenVAS)
- Exploitation (Metasploit)
- Post-exploitation
- Reporting & remediation planning

### 5.2 Learning Outcomes

- Perform end-to-end pentest.
- Write PTES-aligned reports.
- Provide actionable remediation guidance.

---

# End of Theory Notes
