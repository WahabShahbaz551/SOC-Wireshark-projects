# Lab 05: Capturing & Analyzing VoIP Traffic

## 📋 Lab Overview
- **Objective:** Dissect Voice over IP (VoIP) communications by filtering Session Initiation Protocol (SIP) signaling, inspecting Real-time Transport Protocol (RTP) audio streams, and performing audio stream playback.
- **Tools Used:** Wireshark v4.x, Web Browser / Sample PCAP
- **Difficulty:** Beginner to Intermediate
- **Status:** In Progress / Completed

---

## 🔍 Key Wireshark Display Filters

| Filter Syntax | Purpose / Description |
|---|---|
| `sip` | Filters Session Initiation Protocol signaling packets |
| `sip.Method == "INVITE"` | Identifies call initiation requests |
| `rtp` | Filters Real-time Transport Protocol voice packets |
| `rtp.p_type == 0` | Filters standard G.711 PCMU audio codec payloads |

---

## 🧪 Hands-on Investigation & Walkthrough

### Step 1: Filtering SIP Call Signaling

**Description:**
Trace call initiation (`INVITE`), status negotiation (`100 Trying`, `200 OK`), and termination (`BYE`).

**Wireshark Display Filter:**
```wireshark
sip
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 1 Evidence](screenshots/step-1-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 2: VoIP Calls Flow Analysis

**Description:**
Use `Telephony > VoIP Calls` to view the comprehensive call ladder diagram and signaling timeline.

**Wireshark Display Filter:**
```wireshark
sip.Method == "INVITE"
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 2 Evidence](screenshots/step-2-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 3: RTP Stream Quality & Jitter Inspection

**Description:**
Navigate to `Telephony > RTP > RTP Stream Analysis` to calculate packet loss, jitter, and stream health metrics.

**Wireshark Display Filter:**
```wireshark
rtp
```

**Evidence / Screenshot:**
<!-- Place your captured screenshot in the screenshots/ directory and link it below -->
![Step 3 Evidence](screenshots/step-3-evidence.png)

**Observed Details:**
- *Source IP / Port:* `[Fill in from capture]`
- *Destination IP / Port:* `[Fill in from capture]`
- *Protocol / Info:* `[Fill in from capture]`

---
### Step 4: Voice Payload Playback

**Description:**
Use the built-in Wireshark VoIP audio player to reconstruct and listen to the recorded audio stream.

**Wireshark Display Filter:**
```wireshark
rtp.p_type == 0
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
| **Key Protocols Identified** | `VOIP` | Transport / Application Layer |

---

## 🛡️ Security Implications & Key Takeaways

VoIP networks transmitting unencrypted SIP and RTP are vulnerable to unauthorized wiretapping and call reconstruction. Secure VoIP standards (SRTP and TLS/SIPS) should be enforced.

---

## 🔗 References & Learning Material
- Wireshark User Guide: [wireshark.org/docs/dfref](https://www.wireshark.org/docs/dfref/)
- Reference Lab: [0xrajneesh/Wireshark-Projects-for-beginners](https://github.com/0xrajneesh/Wireshark-Projects-for-beginners)
