# 🔥 Week 4 – Advanced VAPT (Full Documentation)

This folder contains the full theoretical + practical work for Week 4 of the VAPT program.

---

# 📚 1. Documentation Included

All documents are stored inside `/Documentation`:

- Week4_Theory.pdf
- Week4_Practical_Labs.pdf
- Advanced Exploitation Notes
- API Security Notes
- Privilege Escalation Notes
- Network Protocol Attacks Notes
- Mobile Application Pentesting Notes
- Capstone Report (PTES Standard)

---

# 🧪 2. Practical Lab Workflows

## **2.1 Advanced Exploitation Lab**

**Tools:** Metasploit, Ghidra, Python  
**Tasks:** Exploit chaining, heap overflow PoC modification, ROP bypass

### **Exploit Log**

| Exploit ID | Description      | Target IP     | Status  | Payload     |
| ---------- | ---------------- | ------------- | ------- | ----------- |
| 007        | XSS to RCE Chain | 192.168.1.100 | Success | Meterpreter |

**Summary (50 words):**  
Modified a Python PoC to manipulate buffer boundaries, enabling controlled EIP overwrite. Built an exploit chain using XSS session hijack → admin takeover → plugin RCE. Used ROP to bypass ASLR and executed reliable shellcode for final Meterpreter session.

---

## **2.2 API Security Testing Lab**

**Tools:** Burp Suite, Postman, SQLMap\*\*

### **API Test Log**

| Test ID | Vulnerability     | Severity | Endpoint   |
| ------- | ----------------- | -------- | ---------- |
| 008     | BOLA              | Critical | /api/users |
| 009     | GraphQL Injection | High     | /graphql   |

**Summary (50 words):**  
Enumerated API endpoints and exploited BOLA to access unauthorized user records. Performed GraphQL query fuzzing to dump schema and extract objects. Manipulated API tokens with Burp Suite to bypass authorization checks.

---

## **2.3 Privilege Escalation & Persistence Lab**

**Tools:** LinPEAS, PowerSploit\*\*

### **Privilege Escalation Log**

| Task ID | Technique    | Target IP     | Status  | Outcome    |
| ------- | ------------ | ------------- | ------- | ---------- |
| 010     | SUID Exploit | 192.168.1.150 | Success | Root Shell |

**Persistence Summary (50 words):**  
Added cron persistence by placing reverse-shell script in `/etc/cron.d/backup`. The script executes every minute, re-establishing access. Low detection risk and no service interruption.

---

## **2.4 Network Protocol Attacks Lab**

**Tools:** Responder, Ettercap, Wireshark\*\*

### **Attack Log**

| Attack ID | Technique | Target IP     | Status  | Outcome   |
| --------- | --------- | ------------- | ------- | --------- |
| 015       | SMB Relay | 192.168.1.200 | Success | NTLM Hash |

**MitM Summary (50 words):**  
Performed ARP spoofing using Ettercap to intercept HTTP traffic. Captured credentials, session tokens, and cookies. Used SSLStrip to downgrade HTTPS to HTTP where possible.

---

## **2.5 Mobile App Pentesting Lab**

**Tools:** MobSF, Frida, Drozer\*\*

### **Mobile Test Log**

| Test ID | Vulnerability    | Severity | Target App |
| ------- | ---------------- | -------- | ---------- |
| 016     | Insecure Storage | High     | test.apk   |

**Summary (50 words):**  
Static analysis revealed sensitive data stored in plaintext SharedPreferences. Using Frida hooks, bypassed authentication logic and intercepted API calls. Analyzed exposed exported activities with Drozer.

---

# 🎯 3. Capstone VAPT Project

### **PTES Log**

| Timestamp           | Target IP     | Vulnerability | PTES Phase   |
| ------------------- | ------------- | ------------- | ------------ |
| 2025-08-30 15:00:00 | 192.168.1.200 | VSFTPD RCE    | Exploitation |

### **150-Word Non-Technical Summary**

A simulated penetration test was performed on the target system to identify security weaknesses that attackers could exploit. The assessment uncovered several high-risk issues, including a remote code execution vulnerability in the FTP service, insecure API endpoints, and weak access controls. These vulnerabilities allowed unauthorized access, system compromise, and exposure of sensitive information. The goal was to evaluate real-world risk, demonstrate attack paths, and recommend improvements. Key fixes include patching outdated services, enforcing strict authentication, and deploying monitoring tools to detect abnormal system activity.

---

# 📥 4. Folder Index
