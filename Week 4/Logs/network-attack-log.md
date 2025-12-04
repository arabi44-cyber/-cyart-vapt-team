1. Lab Environment Preparation

Before starting attacks, the environment must be prepared so that both machines can interact over the same network.

Actions Performed:

Opened VMware/VirtualBox

Powered on Kali (attacker) and Metasploitable2 (target) machines

Ensured both network adapters were set to NAT / Host-only / Bridged

Verified both received IP addresses using ifconfig and ip a

Confirmed connectivity using ping test

Observation:

ping 192.168.0.14 -c 4

Packets received successfully, confirming network communication.

2. Tool Setup & Directory Creation

You created a dedicated working folder:

mkdir Network-Protocol
cd Network-Protocol

This ensures logs, pcaps, screenshots, and notes stay organized.

3. Responder Startup & Event Listening

Responder was started and kept running for broadcast authentication attempts.

Command used:

sudo responder -I eth0

Responder output indicated it was actively poisoning SMB/MDNS/NBT-NS queries
and listening for NTLM authentication attempts.

📝 This stage is important even if the hash is triggered later on.

4. Service Enumeration (Initial Discovery)

Although brief, you scanned target manually and verified services:

FTP — Open

TELNET — Open

HTTP — Open

SMB — Responded on network broadcast (possible relay capture)

These services are known to transmit/accept credentials in plaintext (FTP, Telnet) or relayable (SMB).

5. Wireshark Monitoring

Before performing attacks, Wireshark was opened to monitor traffic.

Filter examples used:

Protocol Filter
FTP credentials ftp contains USER
Telnet & cleartext telnet
HTTP login forms http.authbasic
NTLM/SMB packets ntlmssp / smb2

This step was important for live interception visibility.

6. Live Capture & Manual Credential Observation

When connecting services (FTP, Telnet, HTTP), packets were intercepted in Wireshark.

Example finding:

USER msfadmin
PASS msfadmin

This demonstrates confidentiality compromise in unencrypted protocols.

# Network Protocol Attack Log

| Date       | Activity                                     | Tools Used                      | Result                                   | Evidence                   |
| ---------- | -------------------------------------------- | ------------------------------- | ---------------------------------------- | -------------------------- |
| 2025-12-04 | Network connectivity test to target          | ping                            | Success - Target reachable               | screenshot/terminal output |
| 2025-12-04 | Start Responder for SMB/NTLM capture         | responder -I eth0               | Running successfully                     | console output log         |
| 2025-12-04 | Target authentication test using own machine | SMB/Network broadcast           | NTLM trigger received                    | responder logs             |
| 2025-12-04 | Scan Metasploitable2 ports                   | nmap                            | Detected FTP, HTTP, Telnet open          | scan result screenshot     |
| 2025-12-04 | Service access testing                       | ftp, telnet, http access        | FTP/Telnet/HTTP successful               | connection screenshot      |
| 2025-12-04 | Lab environment prepared                     | VMware/Kali/Metasploitable2     | Both systems booted & network configured | setup screenshot           |
| 2025-12-04 | Connectivity verified                        | ping                            | Target reachable successfully            | ping output                |
| 2025-12-04 | Wireshark monitoring started                 | Wireshark                       | Live traffic captured                    | PCAP saved                 |
| 2025-12-04 | Manual credential interception               | Wireshark + plaintext protocols | USER/PASS captured in packets            | screenshot/snippet         |
