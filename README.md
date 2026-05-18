# 🔐 Vaultify

<div align="center">

### Zero-Knowledge Client-Side Password Manager

Secure. Private. Fully Encrypted.  
No servers. No tracking. No subscriptions.

<br>

![Live Demo](https://img.shields.io/badge/Live_Demo-vault.parrysecurity.online-2563eb?style=for-the-badge&logo=vercel)
![Security](https://img.shields.io/badge/Security-AES--256--GCM-059669?style=for-the-badge&logo=security)
![License](https://img.shields.io/badge/License-MIT-f59e0b?style=for-the-badge&logo=opensourceinitiative)

</div>

---

# 📌 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Live Demo](#-live-demo)
- [Security Architecture](#-security-architecture)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Browser Support](#-browser-support)
- [FAQ](#-faq)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)
- [Security Disclosure](#-security-disclosure)

---

# 📖 About

**Vaultify** is a fully client-side encrypted password manager that runs entirely in your browser.

Unlike traditional password managers, Vaultify follows a **zero-knowledge architecture**, meaning:

✅ Your passwords never leave your device  
✅ No cloud storage  
✅ No analytics or telemetry  
✅ No account required  
✅ No backend servers  

Everything is encrypted locally using modern cryptography before being stored in your browser.

---

# 🚀 Features

## 🔒 Military-Grade Encryption

- AES-256-GCM Encryption
- PBKDF2 with SHA-256
- 600,000 Iterations
- Unique IV per password entry
- Random cryptographic salt generation
- Secure session-based decryption

---

## 🔐 Password Management

- Create, Read, Update & Delete passwords
- Password categories
- Notes support
- Password visibility toggle
- Secure copy-to-clipboard
- Password generator

### Categories

- Work
- Personal
- Finance
- Social
- Other

---

## 🛡️ Security Features

- Auto-lock timer
- Clipboard auto-clear
- Master password re-encryption
- Password strength meter
- Duplicate password detection
- Weak password analysis

---

## 📊 Security Dashboard

Vaultify includes a built-in password health dashboard:

- Weak password detection
- Duplicate detection
- Security recommendations
- Vault statistics

---

## 💾 Backup & Restore

- Encrypted JSON export
- Secure import functionality
- Password verification before restore

---

## 🎨 User Experience

- Dark / Light mode
- Fully responsive UI
- Real-time search
- Keyboard shortcuts
- Toast notifications
- Smooth animations

---

# 🌐 Live Demo

## 🔗 Website

👉 **https://vault.parrysecurity.online**

---

# 🧠 Security Architecture

## 🔐 How Vaultify Works

```text
┌─────────────────┐
│ Master Password │
│ (Never Stored)  │
└────────┬────────┘
         ↓
PBKDF2 + Random Salt
(600,000 Iterations)
         ↓
┌─────────────────┐
│ AES-256-GCM Key │
│ (Memory Only)   │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Encrypted Vault │
│ Unique IV Entry │
└────────┬────────┘
         ↓
┌─────────────────┐
│ localStorage    │
│ (Encrypted)     │
└─────────────────┘
```

---

## 🛡️ Zero-Knowledge Promise

Vaultify guarantees:

✅ We cannot access your passwords  
✅ We cannot reset your master password  
✅ We do not collect data  
✅ We have no servers to breach  
✅ Your encryption keys never leave your browser  

---

# ⚡ Quick Start

## Clone Repository

```bash
git clone https://github.com/parrysecurity/Vaultify-.git

cd Vaultify-
```

---

## Start Local Server

### Python 3

```bash
python3 -m http.server 8000
```

### Node.js

```bash
npx http-server -p 8000
```

---

## Open Browser

```text
http://localhost:8000
```

---

# 🛠️ Installation

# Development

## Python 3

```bash
python3 -m http.server 8000
```

## Python 2

```bash
python -m SimpleHTTPServer 8000
```

## Node.js

```bash
npx http-server -p 8000
```

## PHP

```bash
php -S localhost:8000
```

---

# 🚀 Production Deployment (Apache)

## Copy Project

```bash
sudo cp -r vaultify /var/www/html/
```

---

## Set Permissions

```bash
sudo chown -R www-data:www-data /var/www/html/vaultify

sudo chmod -R 755 /var/www/html/vaultify
```

---

## Apache Virtual Host

```apache
<VirtualHost *:443>

    ServerName vault.parrysecurity.online

    DocumentRoot /var/www/html/vaultify

    <Directory /var/www/html/vaultify>
        Options FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    SSLEngine on

    SSLCertificateFile /path/to/cert.crt
    SSLCertificateKeyFile /path/to/key.key

</VirtualHost>
```

---

# 🔐 HTTPS Requirement

Vaultify uses the **Web Crypto API**, which requires:

- HTTPS
OR
- localhost

---

## Let's Encrypt SSL

```bash
sudo apt install certbot python3-certbot-apache

sudo certbot --apache -d vault.parrysecurity.online
```

---

# 🌍 Browser Support

| Browser | Version | Status |
|---|---|---|
| Chrome | 60+ | ✅ Full Support |
| Firefox | 55+ | ✅ Full Support |
| Edge | 79+ | ✅ Full Support |
| Safari | 15+ | ✅ Full Support |
| Opera | 50+ | ✅ Full Support |
| Internet Explorer | Any | ❌ Unsupported |

---

# 🔧 Required Browser APIs

- Web Crypto API
- localStorage
- TextEncoder / TextDecoder
- ES6+

---

# ❓ FAQ

## Is Vaultify really secure?

Yes. Vaultify uses AES-256-GCM encryption with PBKDF2 key derivation and a zero-knowledge architecture.

---

## What happens if I forget my master password?

Your data cannot be recovered. Vaultify never stores or transmits your master password.

---

## Can I sync across devices?

Currently no cloud sync is implemented. Vaultify is fully local-first.

---

## Why is HTTPS required?

Modern browsers restrict cryptographic APIs to secure contexts.

---

## Is Vaultify free?

Yes. Completely free and open-source.

---

# 💻 Tech Stack

```text
┌────────────────────────────────────┐
│ Frontend                           │
├────────────────────────────────────┤
│ HTML5 │ CSS3 │ Vanilla JavaScript │
└────────────────────────────────────┘

                ↓

┌────────────────────────────────────┐
│ Cryptography                       │
├────────────────────────────────────┤
│ AES-256-GCM │ PBKDF2 │ SHA-256    │
└────────────────────────────────────┘

                ↓

┌────────────────────────────────────┐
│ Storage                            │
├────────────────────────────────────┤
│ localStorage (Encrypted Only)      │
└────────────────────────────────────┘
```

---

# ⚡ Zero Dependencies

❌ No npm packages  
❌ No frameworks  
❌ No tracking libraries  
✅ Pure Vanilla JavaScript  
✅ Lightweight & Fast  

---

# 📂 Project Structure

```text
vaultify/
│
├── index.html
├── README.md
├── LICENSE
│
└── assets/
    └── screenshots/
```

---

# 🤝 Contributing

Contributions are welcome.

## Steps

```bash
# Fork repository

# Create feature branch
git checkout -b feature/amazing-feature

# Commit changes
git commit -m "Add amazing feature"

# Push branch
git push origin feature/amazing-feature
```

Then create a Pull Request.

---

# 📜 License

MIT License © 2026 ParrySecurity

This project is licensed under the MIT License.

---

# 🐞 Security Disclosure

If you discover a vulnerability, please report responsibly.

📧 security@parrysecurity.online

Please avoid creating public security issues.

---

# 🔗 Links

🌐 Live Demo  
https://vault.parrysecurity.online

🐛 Bug Reports  
https://github.com/parrysecurity/Vaultify-/issues

💡 Feature Requests  
https://github.com/parrysecurity/Vaultify-/discussions

---

<div align="center">

# 🔐 Your Passwords. Your Encryption. Your Rules.

Made with ❤️ by ParrySecurity

⭐ Star this repository if you found it useful.

</div>
