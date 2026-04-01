# 🎣 Phishing Analysis Lab

## 📌 Overview
This project demonstrates a complete phishing email analysis workflow. I analyzed a suspicious email (email3.eml) to identify malicious indicators and extract a hidden flag. The techniques used mirror real-world SOC analyst tasks.

## 🛠️ Tools Used
| Tool | Purpose |
|------|---------|
| **Thunderbird** | Open and view email source |
| **CyberChef** | Decode Base64 attachments |
| **Manual Analysis** | Header inspection, URL defanging |

## 🔍 Investigation Steps

### 1. Email Header Analysis
- Opened `email3.eml` in Thunderbird
- Viewed raw source (`Ctrl + U`)
- Extracted key fields:
  - `Return-Path:` – real sender
  - `X-Originating-IP:` – original IP
  - `Authentication-Results:` – SPF/DKIM/DMARC status

**📸 Screenshot:** Raw email source with annotated fields.

### 2. Suspicious Indicators
- **Spoofed From address** – mismatch with `Return-Path`
- **Urgent subject line** – "Immediate action required"
- **Malicious attachment** – PDF file hidden in Base64

### 3. Extracting and Decoding the Attachment
- Located `Content-Type: application/pdf` in source
- Copied Base64 string
- Used CyberChef (`From Base64` operation) to decode
- Saved as `flag.pdf`

**📸 Screenshot:** CyberChef decoding result.

### 4. Recovering the Flag
- Opened `flag.pdf`
- Found hidden flag: `THM{...}`

**📸 Screenshot:** Flag displayed in PDF.

## 📊 Indicators of Compromise (IOCs)
| Type | Value |
|------|-------|
| Originating IP | `203.0.113.5` (defanged: `203[.]0[.]113[.]5`) |
| Malicious Domain | `malicious[.]com` |
| Attachment Hash | `7f83b1657ff1fc53b92dc18148a1d65d` (MD5) |

## 🧠 Lessons Learned
- How to read email headers like `Received`, `Return-Path`, and `Authentication-Results`
- How to extract and decode Base64 attachments
- Identifying phishing techniques: spoofing, urgency, domain mismatch
- Defanging URLs and IPs for safe analysis

## 🚀 Next Steps
- Automate attachment extraction with Python
- Integrate with VirusTotal API for reputation checks
- Build a phishing alert dashboard

## 📂 Files in this Repository
| File | Description |
|------|-------------|
| `email3.eml` | Original suspicious email |
| `flag.pdf` | Decoded attachment |
| `screenshots/` | All screenshots from investigation |
| `iocs.txt` | List of Indicators of Compromise |

## 🔗 References
- [TryHackMe – Phishing Analysis](https://tryhackme.com/room/phishinganalysis)
- [CyberChef – From Base64](https://gchq.github.io/CyberChef/)
- [Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)

---

## 📸 **لقطات الشاشة (تضعها في مجلد `screenshots/`)**

| اسم الملف | المحتوى |
|-----------|---------|
| `01-raw-email-source.png` | المصدر الخام للبريد |
| `02-email-header-fields.png` | إبراز حقول مهمة (Return-Path, X-Originating-IP) |
| `03-cyberchef-base64-decode.png` | فك تشفير Base64 في CyberChef |
| `04-pdf-flag.png` | الـ flag داخل الـ PDF |
| `05-iocs-summary.png` | ملخص مؤشرات الاختراق |

---
## 💡 **نصيحة إضافية**

- **إذا كنت لا تريد نشر البريد الأصلي** (لأسباب أخلاقية)، يمكنك فقط تضمين لقطات
