## Uzilla Recon

🚀 A modular passive reconnaissance toolkit focused on subdomain enumeration, keyword filtering, DNS resolution, and live host detection — built for real-world bug bounty, OSINT, and security automation.

### 📁 Structure

- `wordlists/` — Curated subdomain patterns, including `uzilla-sdms.txt` for identifying high-value targets.
- `scripts/` — Recon automation scripts (Bash, Python) to streamline enumeration and triage.

### ✅ Example Workflow

```bash
# 1. Run passive enumeration
subfinder -d target.com -o -s 'your_sources' subs.txt

# 2. This command cleans the wordlist (remove comments and empty lines) | then Filter for juicy subs
grep -vE '^#|^$' uzilla-sdms.txt | grep -if wordlists/uzilla-sdms.txt subs.txt > filtered.txt

# 3. Resolve live subdomains
dnsx -l filtered.txt -silent -o resolving.txt

# 4. Check for live HTTP(s)
httpx -l resolving.txt -o live.txt -status-code -title
```

### 📌 Coming Soon

- Automation Scripts
- Automated Recon Pipelines
- More curated lists and tool integrations