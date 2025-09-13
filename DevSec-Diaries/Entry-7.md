# 🔎 Vulnerability Scanning Report  


**Tools Used:** Nessus, OpenVAS  

---

## 1. 🎯 Objective  
The purpose of this vulnerability scan was to identify potential security weaknesses in the target system(s) and practice using professional vulnerability assessment tools (Nessus & OpenVAS).  

---

## 2. 📌 Scope  
- **Target(s):**  
  - IP / Hostnames tested  
- **Scan Types:**  
  - Discovery scan  
  - Full vulnerability scan  
- **Tools:**  
  - Nessus (version X.X)  
  - OpenVAS (version X.X)  

---

## 3. ⚙️ Methodology  
1. Installed and configured Nessus / OpenVAS.  
2. Selected scan policy (basic network scan / full vulnerability scan).  
3. Launched scan against defined scope.  
4. Collected and reviewed results.  

---

## 4. 📊 Findings  

| Severity   | Vulnerability Title | Affected Host(s) | CVE ID(s) | Description | Suggested Fix |
|------------|---------------------|------------------|-----------|-------------|---------------|
| Critical   | Example Vulnerability | 192.168.1.10 | CVE-2021-XXXXX | Remote code execution possible due to ... | Apply latest security patch |
| High       | Weak SSH Algorithms | 192.168.1.15 | N/A | Weak ciphers detected in SSH service | Disable weak ciphers, use strong encryption |
| Medium     | Outdated Software   | 192.168.1.20 | CVE-2020-XXXXX | Apache version outdated | Update to latest stable version |
| Low        | Missing Security Headers | web.local | N/A | HTTP headers missing | Configure web server headers |
| Info       | Open Port Detected  | 192.168.1.25 | N/A | Service accessible | Monitor for suspicious activity |

---

## 5. 🖼️ Evidence / Screenshots  
*(Add screenshots of scan results, dashboards, or reports here)*  

---

## 6. 🛠️ Mitigations & Recommendations  
- Patch systems to the latest versions.  
- Reconfigure weak services (SSH, HTTP headers, etc.).  
- Implement continuous monitoring and regular vulnerability scanning.  
- Apply least-privilege principles to reduce attack surface.  

---

## 7. ✅ Conclusion  
The scan helped in identifying critical, high, and medium vulnerabilities within the scope. Regular scanning combined with patch management and system hardening can significantly improve the security posture.  

---
