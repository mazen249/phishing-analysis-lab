# 🎣 Phishing Analysis Lab

## 📌 Overview
This project documents my complete phishing email analysis workflow. I analyzed multiple suspicious emails, extracted malicious indicators, and used various professional security tools. The techniques used mirror real-world SOC analyst tasks, covering the fundamentals, real email cases, and advanced analysis tools.

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **Thunderbird** | Open and view email source |
| **CyberChef** | Decode Base64, extract URLs |
| **Messageheader (Google)** | Analyze email headers |
| **IPinfo** | IP geolocation and ownership |
| **urlscan.io** | Safe URL analysis with screenshots |
| **Talos Reputation** | IP/Domain reputation check |
| **VirusTotal** | File/URL hash reputation |
| **ANY.RUN** | Interactive malware sandbox |
| **Hybrid Analysis** | Free automated file analysis |
| **PhishTool** | Complete phishing investigation platform |
| **SHA256sum** | Calculate file hash (Linux) |

---

## 🔍 Investigation Steps (Room 1: Fundamentals)

### 1. Email Header Analysis
- Opened `email3.eml` in Thunderbird
- Viewed raw source (`Ctrl + U`)
- Extracted key fields:
  - `Return-Path:` – real sender
  - `X-Originating-IP:` – original IP
  - `Authentication-Results:` – SPF/DKIM/DMARC status

📸 **Screenshot:** Raw email source with annotated fields.

### 2. Suspicious Indicators
- **Spoofed From address** – mismatch with `Return-Path`
- **Urgent subject line** – "Immediate action required"
- **Malicious attachment** – PDF file hidden in Base64

### 3. Extracting and Decoding the Attachment
- Located `Content-Type: application/pdf` in source
- Copied Base64 string
- Used CyberChef (`From Base64` operation) to decode
- Saved as `flag.pdf`

📸 **Screenshot:** CyberChef decoding result.

### 4. Recovering the Flag
- Opened `flag.pdf`
- Found hidden flag: `THM{...}`

📸 **Screenshot:** Flag displayed in PDF.

---

## 📊 Indicators of Compromise (IOCs)

| Type | Value |
|------|-------|
| Originating IP | `203.0.113.5` (defanged: `203[.]0[.]113[.]5`) |
| Malicious Domain | `malicious[.]com` |
| Attachment Hash (MD5) | `7f83b1657ff1fc53b92dc18148a1d65d` |
| Malicious Domain (Case 2) | `biz9holdings[.]com` |
| Associated IP (Case 2) | `159.65.99.182` (DigitalOcean) |
| Phishing Domain (Case 3) | `documentssagov[.]com` |
| Exploited Vulnerability (Excel) | `CVE-2017-11882` (Equation Editor) |

---

## 🧠 Lessons Learned

- How to read email headers like `Received`, `Return-Path`, and `Authentication-Results`
- How to extract and decode Base64 attachments using CyberChef
- Identifying phishing techniques: spoofing, urgency, domain mismatch
- Defanging URLs and IPs for safe analysis (`hxxp://`, `[.]`)
- Using sandbox environments (ANY.RUN, Hybrid Analysis) for safe file execution
- Understanding SPF, DKIM, DMARC authentication results
- Recognizing malicious Excel attachments exploiting `CVE-2017-11882`

---

## 🚀 Next Steps

- Automate attachment extraction with Python
- Integrate with VirusTotal API for reputation checks
- Build a phishing alert dashboard

---

## 📂 Files in this Repository

| File | Description |
|------|-------------|
| `email3.eml` | Original suspicious email |
| `flag.pdf` | Decoded attachment |
| `screenshots/` | All screenshots from investigation |
| `iocs.md` | List of Indicators of Compromise |

---

## 🔗 References

- [TryHackMe – Phishing Analysis Fundamentals](https://tryhackme.com/room/phishinganalysisfundamentals)
- [TryHackMe – Phishing Emails in Action](https://tryhackme.com/room/phishingemailsinaction)
- [TryHackMe – Phishing Analysis Tools](https://tryhackme.com/room/phishinganalyticstools)
- [CyberChef – From Base64](https://gchq.github.io/CyberChef/)
- [ANY.RUN](https://any.run)
- [Hybrid Analysis](https://hybrid-analysis.com)
- [urlscan.io](https://urlscan.io)
- [VirusTotal](https://virustotal.com)

---

## 📸 Screenshots

| Filename | Content |
|----------|---------|
| `01-raw-email-source.png` | Raw email source |
| `02-email-header-fields.png` | Key fields (Return-Path, X-Originating-IP) |
| `03-cyberchef-base64-decode.png` | CyberChef Base64 decoding |
| `04-pdf-flag.png` | Hidden flag inside PDF |
| `05-iocs-summary.png` | Summary of IOCs |

