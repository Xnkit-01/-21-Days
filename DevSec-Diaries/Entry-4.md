# Day 4 – Reconnaissance 

## What I Learned Today

### 🔹 WHOIS
- WHOIS is used to gather **domain registration details**.  
- It only works on **root domains** (e.g., `facebook.com`) and not on subdomains like `www.facebook.com`.  
- Important info includes:
  - Registrar (company handling the domain)
  - Creation & expiration dates
  - Nameservers
  - Contact/organization details (if not hidden)

### 🔹 NSLOOKUP
- NSLOOKUP is a **DNS query tool**.  
- It can reveal:
  - **A Record** → IP address of the domain  
  - **MX Records** → Mail servers  
  - **TXT Records** → SPF, DMARC, and verification keys  
  - **NS Records** → Authoritative nameservers  
- Can be used in both single command mode and **interactive mode**.  

### 🔹 SHODAN
- Shodan is a **search engine for internet-connected devices**.  
- It can reveal:
  - Open ports and running services  
  - Software and version information  
  - Potential misconfigurations or vulnerabilities  
- Basic search query:  

### Summary
Reconnaissance was performed using **whois**, **nslookup**, and **Shodan** on the test domain.  
Key findings were noted above. These details will guide further enumeration and vulnerability testing.  

---

## Next Step
**Day 5 → Recon (Subdomains, Directory Enumeration)**
