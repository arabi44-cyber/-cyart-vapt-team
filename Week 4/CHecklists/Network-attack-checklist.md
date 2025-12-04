# Network Protocol Attack Checklist

## Environment Setup

- [✓] Kali Linux attacker machine configured
- [✓] Metasploitable2 target reachable (ping test)
- [✓] Both machines on same network
- [✓] Tools installed: Responder, Ettercap, Wireshark, Netcat, telnet/ftp clients

## SMB / NTLM Attack (Responder)

- [✓] Start responder on interface
- [✓] Wait for network broadcast authentication
- [✓] Capture NTLM hashes
- [✓] Export hashes for cracking if needed

## ARP Spoof + MITM (Ettercap)

- [✓] Enable IP forwarding
- [✓] Launch ARP spoofing against target and gateway
- [✓] Sniff credentials or traffic

## Protocol Testing

- [✓] FTP connection attempt
- [✓] TELNET connection attempt
- [✓] HTTP access validation
- [✓] Capture packets with Wireshark
- [✓] Analyze username/password exposure

## Reporting

- [✓] Document attack path
- [✓] Include logs, screenshots, PCAPs
- [✓] Add success/failure status for each test
