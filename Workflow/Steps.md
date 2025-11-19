#🔧 Workflow Steps – Week 2 VAPT Cycle

This document contains the full step-by-step workflow used during Week 2 activities, including scanning, recon, exploitation, and reporting. All steps follow PTES methodology and use only authorized lab environments (Metasploitable2, DVWA, Kali Linux).

1️⃣ Vulnerability Scanning Workflow
Tools Used

    -Nmap

    -Nikto

    -OpenVAS

Steps

    1. Identify target IP using ip a or VirtualBox network details.

    2. Run basic Nmap scan:

    _`nmap -sV 192.168.0.16`_

    3. Run Nikto web vulnerability scan:

    *`nikto -h http://192.168.0.16`*

    4. Start OpenVAS services:

    *Greenbone Enterpriese trail*

    5. Create target & run a full vulnerability scan in OpenVAS GUI.

    6. Export results: PDF + CSV.

    7. Map vulnerabilities to CVSS v4.0 using NVD.

    8. Prioritize findings (Critical → Low).

    9. Save screenshots + results into Documentation/Scan Reports.
