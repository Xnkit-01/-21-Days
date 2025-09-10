### Network Scanning Fundamentals

### 🔍 Recon Workflow Overview

| Phase              | Goal                                      | Tool/Command Example                     |
|-------------------|-------------------------------------------|------------------------------------------|
| Host Discovery     | Find live systems                         | `nmap -sn 192.168.1.0/24`                |
| Port Scanning      | Identify open/closed/filtered ports       | `nmap -p 1-1000 192.168.1.10`            |
| Service Detection  | Discover services & versions              | `nmap -sV 192.168.1.10`                  |
| OS Fingerprinting  | Guess OS and network stack details        | `nmap -O 192.168.1.10`                   |
| Scan Types         | Choose stealth or full-connect methods    | `nmap -sS`, `-sT`, `-sU`, `-sN`, etc.    |

---

### 🧠 Scan Type Breakdown

| Scan Type       | Description                                                                 | Stealth Level | Flag Used |
|-----------------|-----------------------------------------------------------------------------|---------------|-----------|
| SYN Scan        | Half-open scan using SYN packets                                            | High          | `-sS`     |
| TCP Connect     | Full TCP handshake (easy to detect)                                         | Low           | `-sT`     |
| UDP Scan        | Sends UDP packets to detect services                                        | Medium        | `-sU`     |
| Stealth Scans   | FIN, NULL, Xmas scans to bypass firewalls/logs                              | Very High     | `-sF`, `-sN`, `-sX` |

---

### 🛠️ Quick Notes

- Use `-Pn` to skip host discovery if ICMP is blocked.
- Combine `-sS -sV -O` for a powerful recon sweep.
- Always scan with permission—ethics matter more than exploits.

---

### 📦 Optional Add-ons

- Add a **checklist toggle** in Notion for each scan phase.
- Use **color-coded tags**: Recon, Enumeration, Fingerprinting.
- Include a **"Scan Log" template** to document findings per target.

---

