# Lab 03: Wireshark for Network Intrusion Detection

## 📋 Lab Overview
- **Objective:** Detect and analyze network reconnaissance and active intrusion attempts, such as Nmap port scans (SYN/FIN), brute-force authentication attacks, and traffic floods.
- **Tools Used:** Wireshark v4.x, Web Browser / Sample PCAP
- **Difficulty:** Beginner to Intermediate
- **Status:** In Progress / Completed

---

## 🔍 Key Wireshark Display Filters

| Filter Syntax | Purpose / Description |
|---|---|
| `tcp.flags.syn == 1 and tcp.flags.ack == 0` | Detects initial connection attempts (SYN scan detection) |
| `tcp.flags.reset == 1` | Identifies RST packets returned by closed ports during scanning |
| `icmp.type == 8 or icmp.type == 0` | Filters ICMP Echo Ping sweeps |
| `ftp.response.code == 530` | Filters failed authentication attempts (useful for detecting brute-force) |

---

## 🧪 Hands-on Investigation & Walkthrough

### Step 1: Detecting Reconnaissance & Port Scans

**Description:**
Identify rapid sequential connection attempts across numerous destination ports from a single source IP address.

**Wireshark Display Filter:**
```wireshark
tcp.flags.syn == 1 and tcp.flags.ack == 0
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 1 Evidence](screenshots/step-1-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 2: Analyzing TCP Flag Combinations

**Description:**
Detect stealth scan techniques such as SYN scans (`tcp.flags.syn == 1 and tcp.flags.ack == 0`), NULL scans, and XMAS scans.

**Wireshark Display Filter:**
```wireshark
tcp.flags.reset == 1
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 2 Evidence](screenshots/step-2-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 3: Investigating Brute Force Attempts

**Description:**
Filter application-layer protocol responses (e.g. FTP 530 errors or SSH handshake bursts) indicating password spraying.

**Wireshark Display Filter:**
```wireshark
icmp.type == 8 or icmp.type == 0
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 3 Evidence](screenshots/step-3-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 4: Traffic Flow & I/O Graph Analysis

**Description:**
Use `Statistics > Conversations` and `Statistics > I/O Graphs` to visualize anomalous spikes in packet rates.

**Wireshark Display Filter:**
```wireshark
ftp.response.code == 530
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 4 Evidence](screenshots/step-4-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---


## 📊 Summary of Findings & Incident Analysis

| Attribute | Recorded Value | Notes |
|---|---|---|
| **Investigated Capture File** | `sample.pcapng` | Source capture |
| **Primary Source IP** | `[Enter Source IP]` | Client machine |
| **Primary Destination IP** | `[Enter Destination IP]` | Target server |
| **Key Protocols Identified** | `NETWORK` | Transport / Application Layer |

---

## 🛡️ Security Implications & Key Takeaways

Intrusion attempts leave distinct telemetry footprints. Recognizing reconnaissance at the packet level allows SOC analysts to block offending IPs before full exploitation occurs.

---

## 🔗 References & Learning Material
- Wireshark User Guide: [wireshark.org/docs/dfref](https://www.wireshark.org/docs/dfref/)
- Reference Lab: [0xrajneesh/Wireshark-Projects-for-beginners](https://github.com/0xrajneesh/Wireshark-Projects-for-beginners)
