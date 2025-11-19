_🔧 Workflow Steps – Week 2 VAPT Cycle_

This document contains the full step-by-step workflow used during Week 2 activities, including scanning, recon, exploitation, and reporting. All steps follow PTES methodology and use only authorized lab environments (Metasploitable2, DVWA, Kali Linux).

1️⃣ Vulnerability Scanning Workflow
Tools Used

    -Nmap

    -Nikto

    -OpenVAS

Steps

Identify target IP using ip a or VirtualBox network details.

Run basic Nmap scan:

```
nmap -sV 192.168.0.16
```

Run Nikto web vulnerability scan:

```

nikto -h http://192.168.0.16

```

Start OpenVAS services:

sudo gvm-start

Create target & run a full vulnerability scan in OpenVAS GUI.

Export results: PDF + CSV.

Map vulnerabilities to CVSS v4.0 using NVD.

Prioritize findings (Critical → Low).

Save screenshots + results into Documentation/Scan Reports.
