# Lab 04: Decrypting & Analyzing SSL/TLS Traffic

## 📋 Lab Overview
- **Objective:** Configure Wireshark with pre-master secret key logs (`SSLKEYLOGFILE`) to decrypt TLS/HTTPS traffic and inspect the underlying plaintext protocol data in a controlled lab.
- **Tools Used:** Wireshark v4.x, Web Browser / Sample PCAP
- **Difficulty:** Beginner to Intermediate
- **Status:** In Progress / Completed

---

## 🔍 Key Wireshark Display Filters

| Filter Syntax | Purpose / Description |
|---|---|
| `tls` | Displays all Transport Layer Security packets |
| `tls.handshake.type == 1` | Client Hello message (inspects SNI and supported cipher suites) |
| `tls.handshake.type == 2` | Server Hello message (selected cipher suite and certificate exchange) |
| `http` | Displays decrypted HTTP traffic once TLS keys are loaded |

---

## 🧪 Hands-on Investigation & Walkthrough

### Step 1: Capturing Encrypted TLS Sessions

**Description:**
Capture an HTTPS web session and inspect the Client Hello, Server Hello, and encrypted `Application Data` records.

**Wireshark Display Filter:**
```wireshark
tls
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 1 Evidence](screenshots/step-1-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 2: Configuring Key Logging (`SSLKEYLOGFILE`)

**Description:**
Launch the browser with the `SSLKEYLOGFILE` environment variable configured to log session keys to a local file.

**Wireshark Display Filter:**
```wireshark
tls.handshake.type == 1
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 2 Evidence](screenshots/step-2-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 3: Loading Keys into Wireshark

**Description:**
Navigate to `Edit > Preferences > Protocols > TLS` and populate the `(Pre)-Master-Secret log filename` field with the generated key file.

**Wireshark Display Filter:**
```wireshark
tls.handshake.type == 2
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 3 Evidence](screenshots/step-3-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 4: Analyzing Decrypted Application Data

**Description:**
Verify that Wireshark generates a new `Decrypted TLS` tab and reveals the underlying cleartext HTTP requests and responses.

**Wireshark Display Filter:**
```wireshark
http
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
| **Key Protocols Identified** | `SSL` | Transport / Application Layer |

---

## 🛡️ Security Implications & Key Takeaways

While TLS provides confidentiality and integrity across public networks, enterprise SOCs and threat hunters often utilize TLS inspection to identify malicious payloads hidden inside encrypted streams.

---

## 🔗 References & Learning Material
- Wireshark User Guide: [wireshark.org/docs/dfref](https://www.wireshark.org/docs/dfref/)
- Reference Lab: [0xrajneesh/Wireshark-Projects-for-beginners](https://github.com/0xrajneesh/Wireshark-Projects-for-beginners)
