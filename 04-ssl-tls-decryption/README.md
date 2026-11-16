# Lab 04: Decrypting & Analyzing SSL/TLS Traffic

## 📋 Lab Overview
- **Objective:** Capture encrypted HTTPS/TLSv1.3 traffic, configure the `SSLKEYLOGFILE` environment variable to log browser session keys, load the pre-master secret log into Wireshark, and inspect the decrypted HTTP/2 application payloads in plaintext.
- **Target Tested:** `https://httpbin.org/get` (Encrypted HTTPS over TLSv1.3 / HTTP/2)
- **Tools Used:** Wireshark v4.x, Mozilla Firefox, Windows 10/11
- **Investigation Role:** Tier-1 SOC Analyst / Network Forensics
- **Status:** Completed

---

## 🔍 Key Wireshark Display Filters

| Display Filter | Purpose & Description |
|---|---|
| `tls.handshake.type == 1` | Isolates TLS `Client Hello` packets to inspect SNI and cipher suites |
| `http or http2` | Filters decrypted HTTP/1.1 and HTTP/2 traffic once TLS keys are loaded |
| `http2` | Isolates decrypted HTTP/2 frames (`HEADERS`, `DATA`, `SETTINGS`) |

---

## 🧪 Forensic Walkthrough & Evidence

### Step 1: Capturing the Encrypted TLS Handshake

**Description:**
Started a live packet capture in Wireshark while browsing `https://httpbin.org/get` in Firefox. Applied the `tls.handshake.type == 1` display filter to inspect the initial `Client Hello` handshake. Because the session is encrypted with TLSv1.3, application data appears opaque without decryption keys.

**Wireshark Display Filter:**
```wireshark
tls.handshake.type == 1
```

**Evidence / Screenshot:**


**Observed Details:**
- **Client IP:** `192.168.100.2`
- **Server IP:** `44.209.237.184`
- **Protocol:** `TLSv1.3`
- **Server Name Indication (SNI):** `httpbin.org` (Frame 36)
- **Cipher Suites Offered:** 15 suites

---

### Step 2: Configuring `SSLKEYLOGFILE` in Wireshark

**Description:**
Before launching Firefox, the `SSLKEYLOGFILE` environment variable was exported (`D:\wireshark\sslkeylog.log`) to record ephemeral session keys. In Wireshark, navigated to `Edit > Preferences > Protocols > TLS` and set the `(Pre)-Master-Secret log filename` path to `D:\wireshark\sslkeylog.log`.

**Wireshark Configuration:**
`Edit > Preferences > Protocols > TLS > (Pre)-Master-Secret log filename`

**Evidence / Screenshot:**


**Observed Details:**
- **Key Log File Path:** `D:\wireshark\sslkeylog.log`
- **Security Note:** Session key logs were stored outside the repository directory and excluded from version control.

---

### Step 3: Inspecting Decrypted HTTP/2 Traffic

**Description:**
Upon applying the TLS key log in Wireshark, encrypted `Application Data` records were automatically decrypted into readable HTTP/2 frames. Filtering by `http2` revealed the underlying `GET /get` request (Frame 74) and `200 OK` JSON response (Frame 108), along with a dedicated `Decrypted TLS` byte tab.

**Wireshark Display Filter:**
```wireshark
http2
```

**Evidence / Screenshot:**


**Observed Details:**
- **Request Frame (Frame 74):** `HEADERS[3]: GET /get, WINDOW_UPDATE[3]` (`192.168.100.2` → `44.209.237.184`)
- **Response Frame (Frame 108):** `HEADERS[3]: 200 OK, DATA[3], JSON (application/json)` (`44.209.237.184` → `192.168.100.2`)
- **Decryption Proof:** `Decrypted TLS (70 bytes)` tab visible in the bottom byte pane

---

### Step 4: Following the TLS Stream (Plaintext JSON Payload)

**Description:**
Right-clicked the decrypted HTTP/2 session and selected `Follow > TLS Stream` to reconstruct the plaintext application payload. The decrypted stream exposed the full HTTP request headers (`Host`, `User-Agent`, `Accept-Encoding`) and the server's JSON response body.

**Wireshark Tool:**
`Follow > TLS Stream`

**Evidence / Screenshot:**


**Observed Details:**
- **Decrypted URL:** `https://httpbin.org/get`
- **Method:** `GET`
- **Host Header:** `httpbin.org`
- **User-Agent:** `Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:160.0) Gecko/20100101 Firefox/160.0`
- **Payload Format:** Plaintext JSON (`"args"`, `"headers"`, `"method"`, `"origin"`, `"url"`)

---

## 📊 Summary of Findings

| Attribute | Recorded Value | Notes |
|---|---|---|
| **Investigated Target** | `https://httpbin.org/get` | HTTPS endpoint using TLSv1.3 |
| **Client IP (Source)** | `192.168.100.2` | Local machine |
| **Server IP (Destination)** | `44.209.237.184` | `httpbin.org` server |
| **Negotiated Protocols** | `TLSv1.3` / `HTTP2` | Encrypted transport, multiplexed application layer |
| **Decryption Method** | `SSLKEYLOGFILE` | Pre-Master-Secret key log |

---

## 🛡️ Security Implications & SOC Defense

1. **Visibility in Enterprise SOCs:** Because modern malware and C2 channels increasingly use TLS/HTTPS, SOC teams rely on controlled TLS inspection (SSL proxies or endpoint key logging in sandboxes) to regain payload visibility.
2. **Key Protection:** `SSLKEYLOGFILE` must never be enabled on production machines or committed to repositories—anyone possessing the key log can retroactively decrypt captured TLS sessions, even with Perfect Forward Secrecy (PFS).

---

## 🔗 References
- Reference Lab: [0xrajneesh/Wireshark-Projects-for-beginners](https://github.com/0xrajneesh/Wireshark-Projects-for-beginners)
- Wireshark TLS Decryption Docs: [wiki.wireshark.org/TLS](https://wiki.wireshark.org/TLS)
