# 🕵️ Recon Methodology

## 1. Subdomain Enumeration

### Why?

Finding subdomains helps reveal hidden parts of a target, such as staging sites, APIs, or admin portals, which might be more vulnerable.

### Tools

* `subfinder` → Collects subdomains from passive sources.
* `assetfinder` → Gathers related domains and subdomains.
* `amass` → More thorough subdomain discovery.
* `crt.sh` → Check SSL certificate transparency logs manually.

### Example Commands

```bash
# Subfinder\subfinder -d target.com -o subdomains.txt

# Assetfinder
assetfinder --subs-only target.com >> subdomains.txt

# Amass (passive mode)
amass enum -passive -d target.com -o amass.txt

# Combine and clean results
cat subdomains.txt amass.txt | sort -u > all_subdomains.txt
```

### Checking Alive Domains

```bash
cat all_subdomains.txt | httprobe | tee alive.txt
```

---

## 2. Directory & File Discovery

### Why?

Uncover hidden files, folders, or endpoints that might expose sensitive info (e.g., `/admin`, `/backup`).

### Tools

* `gobuster`
* `dirsearch`

### Example Commands

```bash
# Gobuster
gobuster dir -u https://target.com -w /usr/share/seclists/Discovery/Web-Content/common.txt -o dirs.txt

# Dirsearch
python3 dirsearch.py -u https://target.com -e php,html,js -w /usr/share/seclists/Discovery/Web-Content/common.txt -o dirs.txt
```

---

## 3. OSINT (Open-Source Intelligence)

### Why?

Use publicly available information to expand recon without interacting directly with the target.

### Methods

* **Google Dorks** → e.g., `site:*.target.com`
* **GitHub searches** → Check for exposed API keys or configs.
* **Shodan/Censys** → Find internet-facing services tied to the domain.

---

## 4. Good Practices

* Save outputs clearly (`subdomains.txt`, `alive.txt`, `dirs.txt`).
* Use more than one tool for reliable results.
* Only move forward with live and verified subdomains.
* Keep structured notes so the process is repeatable.

---

## 5. Simple Recon Workflow

1. Enumerate subdomains → (`subfinder`, `assetfinder`, `amass`).
2. Verify active ones → (`httprobe`).
3. Hunt for directories → (`gobuster`, `dirsearch`).
4. Expand intel with OSINT.
5. Prepare targets for deeper scanning (`nmap`, service detection).
