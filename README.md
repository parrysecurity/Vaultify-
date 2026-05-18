🔐 Vaultify
Zero-knowledge, client-side password manager with military-grade encryption

https://img.shields.io/badge/Live_Demo-vault.parrysecurity.online-2563eb?style=for-the-badge&logo=vercel
https://img.shields.io/badge/Security-AES--256--GCM-059669?style=for-the-badge&logo=security
https://img.shields.io/badge/License-MIT-amber?style=for-the-badge&logo=opensourceinitiative

📌 Table of Contents
About

Features

Live Demo

Security Architecture

Quick Start

Installation

Browser Support

FAQ

License

About
Vaultify is a fully client-side, encrypted password manager that runs entirely in your browser.

No cloud, no servers, no tracking - just pure encryption with zero knowledge architecture.

Why Vaultify?
Cloud Password Managers	Vaultify
❌ Your data on their servers	✅ Your data stays in YOUR browser
❌ Subscription fees	✅ Completely free
❌ Company can be breached	✅ No servers to breach
❌ Telemetry & tracking	✅ Zero analytics
❌ Requires account	✅ No account needed
Features
🔒 Encryption
AES-256-GCM - Military-grade encryption

PBKDF2 - 600,000 iterations with SHA-256

Unique IV per entry - Prevents pattern analysis

Random salt per vault - Rainbow table protection

🔐 Password Management
Create, Read, Update, Delete passwords

Secure password generator (cryptographically random)

Password strength meter (Weak → Strong)

Categories: Work, Personal, Finance, Social, Other

🛡️ Security Features
Auto-lock timer (1min - Never)

Auto-clearing clipboard (10s - Never)

Session-based decryption (no persisted plaintext)

Master password change with automatic re-encryption

📊 Health Dashboard
Identify weak passwords

Detect duplicate passwords

Security recommendations

💾 Backup & Restore
Encrypted JSON export

Secure import with password verification

🎨 User Experience
Dark / Light theme

Real-time search & filter

Keyboard shortcuts (Ctrl+L, Ctrl+S, Ctrl+N)

Toast notifications

Fully responsive design

Live Demo
🔗 https://vault.parrysecurity.online
Try it now - no installation required!

First time?

Create a master password (strong!)

Add your first password entry

Test the password generator

Explore the health dashboard

Security Architecture
How it works

┌─────────────────┐
│ Master Password │ (Never stored, never transmitted)
└────────┬────────┘
         ↓
    PBKDF2 + Salt
   (600,000 iterations)
         ↓
┌─────────────────┐
│  AES-256-GCM    │ (Encryption key - in memory only)
│      Key        │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Individual      │ (Unique IV per password)
│ Entries         │
└────────┬────────┘
         ↓
┌─────────────────┐
│   localStorage  │ (Encrypted vault only)
└─────────────────┘
What makes it secure?
Layer	Protection
Master password	Never stored, never leaves browser
Salt	Unique per vault (prevents rainbow tables)
IV	Unique per entry (prevents pattern detection)
LocalStorage	Only encrypted data persisted
Session	Decrypted data cleared on lock
Zero-Knowledge Promise
✅ We cannot access your passwords

✅ We cannot reset your master password

✅ We have no servers to breach

✅ We collect zero data

✅ Your security is truly in your hands

Quick Start
One-minute setup

# Clone the repository
git clone https://github.com/yourusername/vaultify.git
cd vaultify

# Start a local server
python3 -m http.server 8000

# Open your browser
open http://localhost:8000
That's it! No dependencies, no build steps, no configuration.

Or use directly
Download index.html and open it with a local server (not file:// protocol).

Installation
Development Server
bash
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js
npx http-server -p 8000

# PHP
php -S localhost:8000
Production Deployment (Apache)
bash
# Copy to web directory
sudo cp -r vaultify /var/www/html/

# Set permissions
sudo chown -R www-data:www-data /var/www/html/vaultify/
sudo chmod -R 755 /var/www/html/vaultify/

# Configure virtual host (optional)
sudo nano /etc/apache2/sites-available/vaultify.conf
Virtual host configuration:

apache
<VirtualHost *:443>
    ServerName vault.parrysecurity.online
    DocumentRoot /var/www/html/vaultify
    
    <Directory /var/www/html/vaultify>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    SSLEngine on
    SSLCertificateFile /path/to/cert.crt
    SSLCertificateKeyFile /path/to/key.key
</VirtualHost>
HTTPS Requirement
Important: Web Crypto API requires HTTPS (except localhost).


# Using Let's Encrypt (Ubuntu + Apache)
sudo apt install certbot python3-certbot-apache
sudo certbot --apache -d vault.parrysecurity.online
Browser Support
Browser	Version	Status
Chrome	60+	✅ Full
Firefox	55+	✅ Full
Edge	79+	✅ Full
Safari	15+	✅ Full
Opera	50+	✅ Full
IE	Any	❌ Not supported
Required APIs
Web Crypto API (crypto.subtle)

TextEncoder / TextDecoder

localStorage

ES6+

FAQ
<details> <summary><strong>Is Vaultify really secure?</strong></summary>
Yes. All encryption uses the browser's native Web Crypto API (AES-256-GCM). Your master password never leaves your device, and there are no servers to compromise.

</details><details> <summary><strong>What if I forget my master password?</strong></summary>
Your data is unrecoverable. This is by design - there's no backdoor or password reset feature. Use the hint option to help remember.

</details><details> <summary><strong>Can I sync across devices?</strong></summary>
No. Vaultify is intentionally offline-only for security. Use the Export/Import feature to manually transfer your encrypted vault between devices.

</details><details> <summary><strong>Why do I need HTTPS?</strong></summary>
Web Crypto API's crypto.subtle requires HTTPS (or localhost) for security. This prevents man-in-the-middle attacks.

</details><details> <summary><strong>Is there a mobile app?</strong></summary>
No, but the web app is fully responsive and works on mobile browsers. Add to home screen for an app-like experience.

</details><details> <summary><strong>Does this cost money?</strong></summary>
No. Vaultify is completely free and open source. No subscriptions, no hidden costs.

</details>
Tech Stack

┌─────────────────────────────────────────────┐
│                 Frontend                     │
├─────────────────────────────────────────────┤
│  HTML5    │  CSS3    │  Vanilla JavaScript  │
└─────────────────────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────┐
│              Web Crypto API                  │
├─────────────────────────────────────────────┤
│  AES-256-GCM  │  PBKDF2  │  SHA-256         │
└─────────────────────────────────────────────┘
                      ↓
┌─────────────────────────────────────────────┐
│                 Storage                      │
├─────────────────────────────────────────────┤
│  localStorage (encrypted vault only)         │
└─────────────────────────────────────────────┘
Zero Dependencies
❌ No npm packages

❌ No external libraries (except FontAwesome CDN)

✅ Pure vanilla JavaScript

Project Structure

vaultify/
│
├── index.html              # Complete application (single file)
├── README.md               # This file
├── LICENSE                 # MIT License
│
└── assets/
    └── screenshots/        # Documentation images
Contributing
Fork the repository

Create a feature branch (git checkout -b feature/amazing)

Commit changes (git commit -m 'Add amazing feature')

Push to branch (git push origin feature/amazing)

Open a Pull Request

Guidelines:

Maintain zero external dependencies

Preserve vanilla JavaScript (no frameworks)

Keep the single-file architecture

Test across multiple browsers

License
MIT License - See LICENSE file for details.


MIT License

Copyright (c) 2024 ParrySecurity

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files...
Links
🔗 Live Demo: https://vault.parrysecurity.online

🐛 Report Bug: GitHub Issues

💡 Feature Request: GitHub Discussions

Support
Star this repo ⭐ if you find Vaultify useful!

https://img.shields.io/github/stars/yourusername/vaultify?style=social

Security Disclosure
Responsible Disclosure: For security vulnerabilities, please email security@parrysecurity.online instead of creating a public issue.

PGP Key: [Your PGP fingerprint if available]

<div align="center">
🔐 Your passwords. Your encryption. Your rules.

Made with ❤️ by ParrySecurity

</div>
