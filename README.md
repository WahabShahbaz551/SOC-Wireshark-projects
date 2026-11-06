# Wireshark Network Analysis & Security Portfolio

![Wireshark](https://img.shields.io/badge/Wireshark-v4.x-blue?logo=wireshark&logoColor=white)
![Focus](https://img.shields.io/badge/Domain-SOC%20Analysis%20%7C%20Incident%20Response%20%7C%20Forensics-red)
![Status](https://img.shields.io/badge/Status-Hands--on%20Labs%20In%20Progress-brightgreen)

Welcome to my **Network Traffic Analysis & Packet Inspection Portfolio**. This repository documents hands-on practical labs using [Wireshark](https://www.wireshark.org/) to dissect network communications, investigate security incidents, decrypt secured sessions, and identify indicators of compromise (IoCs).

---

## 📂 Portfolio Structure & Projects

Each directory below is an independent, end-to-end lab containing its dedicated technical write-up, display filters used, step-by-step methodology, screenshots, and findings.

| # | Project / Lab Domain | Focus Protocols & Tools | Status | Documentation Link |
|---|---|---|---|---|
| **01** | **Analyzing HTTP Traffic with Wireshark** | HTTP, TCP, Plaintext Payloads | Ready for Evidence | [View Lab Write-up](./01-http-traffic-analysis/) |
| **02** | **Detecting & Investigating Malware Traffic** | DNS, HTTP C2, Malicious Payloads, IoCs | Ready for Evidence | [View Lab Write-up](./02-malware-traffic-investigation/) |
| **03** | **Network Intrusion & Port Scan Detection** | TCP Flags (SYN/RST), Nmap Scans, DoS | Ready for Evidence | [View Lab Write-up](./03-network-intrusion-detection/) |
| **04** | **Decrypting & Analyzing SSL/TLS Traffic** | TLS Handshake, `SSLKEYLOGFILE`, Keys | Ready for Evidence | [View Lab Write-up](./04-ssl-tls-decryption/) |
| **05** | **Capturing & Analyzing VoIP Traffic** | SIP Signaling, RTP Streams, VoIP Audio | Ready for Evidence | [View Lab Write-up](./05-voip-traffic-analysis/) |

---

## 🛠️ Environment & Prerequisites

- **Packet Analyzer:** [Wireshark](https://www.wireshark.org/download.html) (v4.x+)
- **Operating System:** Kali Linux / Ubuntu / Windows 11
- **Traffic Sources:** Live capture interface, simulated attack lab, and curated `.pcap` / `.pcapng` files from:
  - [Malware-Traffic-Analysis.net](https://www.malware-traffic-analysis.net/)
  - [Wireshark Sample Captures Wiki](https://wiki.wireshark.org/SampleCaptures)

---

## 🎯 Key Skills Demonstrated

- **Protocol Deep Dives:** Deep packet inspection across Layer 3 to Layer 7 (IP, ICMP, TCP, UDP, DNS, HTTP, TLS, SIP, RTP).
- **Security Triage & Incident Analysis:** Tracing attacker reconnaissance, identifying automated port scans, and pinpointing malicious outbound C2 beacons.
- **Cryptographic Traffic Inspection:** Configuring pre-master secret key logs to inspect encrypted sessions in controlled security environments.
- **Forensic Documentation:** Structuring actionable incident response notes and compiling clear Indicators of Compromise (IoCs).

---

## 📖 References & Acknowledgments

- Lab exercises structured and adapted from the open-source curriculum by [0xrajneesh/Wireshark-Projects-for-beginners](https://github.com/0xrajneesh/Wireshark-Projects-for-beginners).
- Wireshark Official Documentation & Filter Reference: [wireshark.org/docs](https://www.wireshark.org/docs/).
# SOC-Wireshark-projects
