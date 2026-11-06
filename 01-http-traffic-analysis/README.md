# Lab 01: Analyzing HTTP Traffic with Wireshark

## 📋 Lab Overview
- **Objective:** Capture and dissect unencrypted HTTP communication, analyze GET and POST request/response headers, follow TCP streams, and extract cleartext payload data.
- **Tools Used:** Wireshark v4.x, Web Browser / Sample PCAP
- **Difficulty:** Beginner to Intermediate
- **Status:** In Progress / Completed

---

## 🔍 Key Wireshark Display Filters

| Filter Syntax | Purpose / Description |
|---|---|
| `http` | Displays only Hypertext Transfer Protocol packets |
| `http.request.method == "GET"` | Filters for HTTP GET requests |
| `http.request.method == "POST"` | Filters for HTTP POST submissions (form data, logins) |
| `http.response.code == 200` | Filters for successful server responses |
| `tcp.stream eq 0` | Isolates an entire TCP conversation stream |

---

## 🧪 Hands-on Investigation & Walkthrough

### Step 1: Capture Setup & Interface Selection

**Description:**
Select the active network adapter connected to the Internet and begin packet capture before browsing an unencrypted site (e.g., `http://example.com`).

**Wireshark Display Filter:**
```wireshark
http
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 1 Evidence](screenshots/step-1-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 2: Filtering HTTP Requests

**Description:**
Apply the `http` display filter to eliminate background noise (mDNS, ARP, TLS) and isolate web traffic.

**Wireshark Display Filter:**
```wireshark
http.request.method == "GET"
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 2 Evidence](screenshots/step-2-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 3: Dissecting Request Headers

**Description:**
Inspect the Hypertext Transfer Protocol pane to analyze `Host`, `User-Agent`, `Accept-Language`, and query parameters.

**Wireshark Display Filter:**
```wireshark
http.request.method == "POST"
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 3 Evidence](screenshots/step-3-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 4: Following TCP Stream & Payload Extraction

**Description:**
Right-click on an HTTP packet and select `Follow > TCP Stream` to observe the bidirectional client-server transaction in plain text.

**Wireshark Display Filter:**
```wireshark
http.response.code == 200
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
| **Key Protocols Identified** | `HTTP` | Transport / Application Layer |

---

## 🛡️ Security Implications & Key Takeaways

Unencrypted HTTP transmits credentials, session tokens, and data payloads in cleartext across the network, making it vulnerable to sniffing and man-in-the-middle (MitM) eavesdropping.

---

## 🔗 References & Learning Material
- Wireshark User Guide: [wireshark.org/docs/dfref](https://www.wireshark.org/docs/dfref/)
- Reference Lab: [0xrajneesh/Wireshark-Projects-for-beginners](https://github.com/0xrajneesh/Wireshark-Projects-for-beginners)
