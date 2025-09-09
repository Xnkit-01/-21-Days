# 📅 Day 5 – Reconnaissance

## ✅ What I Learned Today

* **Subdomain Enumeration**

  * Definition: Finding hidden subdomains like `admin.example.com` or `api.example.com`.
  * Tools I explored: `subfinder`, `assetfinder`, `amass`, `crt.sh`.
  * Learned how to filter only live subdomains using `httprobe`.

* **Directory & File Enumeration**

  * Understood how to brute-force hidden directories and files.
  * Practiced using `gobuster` with wordlists from **SecLists**.
  * Learned to save results into organized files (`dirs.txt`).

* **Recon Workflow**

  * Step 1: Gather subdomains
  * Step 2: Check which ones are alive
  * Step 3: Enumerate directories on alive subdomains
  * Step 4: Expand attack surface using OSINT (Google dorks, GitHub, Shodan)

* **Documentation**

  * Wrote a structured **Recon Methodology** file with tools, commands, and workflow.
  * Learned the importance of saving outputs (`subdomains.txt`, `alive.txt`, `dirs.txt`) for future reference.

## 🔜 Next Step

Move on to **active scanning & enumeration** with `nmap` to identify open ports, services, and technologies.
