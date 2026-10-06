# Ultimate-Defensive-Auditor
Ultimate Defensive Auditor is a Blue Team security auditing tool written in Python. It simulates attacker reconnaissance techniques to identify misconfigurations, information leakage, and OWASP compliance gaps before real attackers find them
# Ultimate Defensive Auditor 🛡️

**[فارسی](#فارسی)** | **[English](#english)**

---

## فارسی

### معرفی
**Ultimate Defensive Auditor** یک ابزار ممیزی امنیتی دفاعی (Blue Team) نوشته شده با پایتون است. این ابزار با شبیه‌سازی تکنیک‌های شناسایی مهاجمان، ضعف‌های پیکربندی، نشت اطلاعات و عدم انطباق با استانداردهای OWASP را **قبل از اینکه هکرها پیدا کنند**، شناسایی می‌کند.

> ⚠️ **سلب مسئولیت:** این ابزار صرفاً برای مقاصد آموزشی و ممیزی امنیتی زیرساخت‌هایی که مالک آن‌ها هستید یا مجوز کتبی دارید طراحی شده است. استفاده از آن روی سیستم‌های دیگران بدون اجازه، جرم سایبری محسوب می‌شود.

### ویژگی‌ها و ترفندها
- 🔍 **شناسایی CDN/WAF:** تشخیص Cloudflare، ArvanCloud، Akamai و ...
- 📋 **ممیزی OWASP:** بررسی HSTS, CSP, X-Frame-Options, Referrer-Policy
- 🎯 **ترفند ۱ - نشت IP از DNS:** استخراج IP واقعی سرور از رکوردهای MX و SPF
- 🍯 **ترفند ۲ - اثرانگشت WAF:** شناسایی رفتار فایروال با Honeypotهای `/.env` و `/.git`
- 🔓 **ترفند ۳ - تست CORS:** بررسی اعتماد نادرست به Originهای مخرب
- ⚙️ **ترفند ۴ - متدهای HTTP:** شناسایی متد خطرناک TRACE (XST)
- 🍪 **تحلیل کوکی‌ها:** بررسی فلگ‌های Secure, HttpOnly, SameSite

### پیش‌نیازها
- Python 3.8+
- کتابخانه‌های: `requests`, `dnspython`, `tldextract`

### نصب و اجرا

#### Kali Linux / macOS
```bash
# کلون کردن ریپازیتوری
git clone https://github.com/YOUR_USERNAME/ultimate-defensive-auditor.git
cd ultimate-defensive-auditor

# ساخت محیط مجازی
python3 -m venv env
source env/bin/activate

# نصب وابستگی‌ها
pip install requests dnspython tldextract

# اجرا
python3 ultimate_audit.py https://target.com
# کلون کردن ریپازیتوری
git clone https://github.com/YOUR_USERNAME/ultimate-defensive-auditor.git
cd ultimate-defensive-auditor

# ساخت محیط مجازی
python -m venv env
.\env\Scripts\activate

# نصب وابستگی‌ها
pip install requests dnspython tldextract

# اجرا
python ultimate_audit.py https://target.com
🎯 TARGET: https://example.com
🌐 DOMAIN: example.com

============================================================
🔍 INFRASTRUCTURE & CDN FINGERPRINTING
============================================================
  ✅ CDN Detected: Server=cloudflare
  ℹ️  Cache Status: HIT

============================================================
🔍 TRICK 1: ORIGIN IP LEAKAGE VIA DNS (CRITICAL)
============================================================
  ⚠️  MX Record 'mail.example.com' resolves to: 203.0.113.50
      ↳ ACTION: Verify if this IP is open to public web traffic!

============================================================
🔍 TRICK 2: WAF BEHAVIORAL FINGERPRINTING (HONEYPOTS)
============================================================
  🛡️  /.env: 403 Forbidden (Cloudflare WAF Block)

✅ AUDIT COMPLETE. Review warnings and fix misconfigurations.
English
Overview
Ultimate Defensive Auditor is a Blue Team security auditing tool written in Python. It simulates attacker reconnaissance techniques to identify misconfigurations, information leakage, and OWASP compliance gaps before real attackers find them.
⚠️ Disclaimer: This tool is designed solely for educational purposes and authorized security assessments of infrastructure you own or have written permission to test. Unauthorized use against third-party systems is illegal and unethical.
Features & Tricks
🔍 CDN/WAF Detection: Identifies Cloudflare, ArvanCloud, Akamai, Fastly, Imperva, Sucuri
📋 OWASP Headers Audit: Checks HSTS, CSP, X-Frame-Options, Referrer-Policy, X-Content-Type-Options
🎯 Trick 1 - DNS Origin Leakage: Extracts real Origin IP from MX and SPF records
🍯 Trick 2 - WAF Behavioral Fingerprinting: Detects WAF behavior via honeypot paths (/.env, /.git)
🔓 Trick 3 - CORS Misconfiguration: Tests for improper trust in malicious Origins
⚙️ Trick 4 - HTTP Methods: Detects dangerous TRACE method (XST vulnerability)
🍪 Cookie Security Analysis: Validates Secure, HttpOnly, and SameSite flags
Prerequisites
Python 3.8+
Libraries: requests, dnspython, tldextract
Installation & Usage
Kali Linux / macOS
# Clone repository
git clone https://github.com/YOUR_USERNAME/ultimate-defensive-auditor.git
cd ultimate-defensive-auditor

# Create virtual environment
python3 -m venv env
source env/bin/activate

# Install dependencies
pip install requests dnspython tldextract

# Run
python3 ultimate_audit.py https://target.com
# Clone repository
git clone https://github.com/YOUR_USERNAME/ultimate-defensive-auditor.git
cd ultimate-defensive-auditor

# Create virtual environment
python -m venv env
.\env\Scripts\activate

# Install dependencies
pip install requests dnspython tldextract

# Run
python ultimate_audit.py https://target.com🎯 TARGET: https://example.com
🌐 DOMAIN: example.com

============================================================
🔍 INFRASTRUCTURE & CDN FINGERPRINTING
============================================================
  ✅ CDN Detected: Server=cloudflare
  ℹ️  Cache Status: HIT

============================================================
🔍 TRICK 1: ORIGIN IP LEAKAGE VIA DNS (CRITICAL)
============================================================
  ⚠️  MX Record 'mail.example.com' resolves to: 203.0.113.50
      ↳ ACTION: Verify if this IP is open to public web traffic!

============================================================
🔍 TRICK 2: WAF BEHAVIORAL FINGERPRINTING (HONEYPOTS)
============================================================
  🛡️  /.env: 403 Forbidden (Cloudflare WAF Block)

✅ AUDIT COMPLETE. Review warnings and fix misconfigurations.
License
MIT License
Contributing
Contributions, issues, and feature requests are welcome! Please ensure all contributions align with the defensive security purpose of this tool.
