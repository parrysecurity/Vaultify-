🔐 Vaultify - Encrypted Password Vault
https://img.shields.io/badge/security-AES--256--GCM-green
https://img.shields.io/badge/license-MIT-blue
https://img.shields.io/badge/JavaScript-Vanilla-yellow
https://img.shields.io/badge/browsers-modern-brightgreen
https://img.shields.io/badge/PRs-welcome-brightgreen

Zero-knowledge, client-side password manager with military-grade encryption. All your passwords encrypted, never leaving your browser.

🌐 Live Demo: https://vault.parrysecurity.online

📖 Table of Contents
✨ Features

🔐 Security Architecture

🚀 Quick Start

💻 Technical Stack

📁 Project Structure

🔧 Installation & Deployment

🧪 Testing

🛡️ Security Best Practices

🌐 Browser Support

❓ FAQ

🤝 Contributing

📄 License

🙏 Acknowledgments

✨ Features
Core Security
✅ AES-256-GCM Encryption - Military-grade encryption for all stored passwords

✅ PBKDF2 Key Derivation - 600,000 iterations with SHA-256

✅ Zero-Knowledge Architecture - Master password never leaves your browser

✅ Local-Only Storage - Vault stored in browser's localStorage (no cloud)

✅ Session-Based Decryption - Plaintext never persisted

Password Management
🔑 Create, Read, Update, Delete - Full CRUD operations

🎲 Secure Password Generator - Cryptographically random (crypto.getRandomValues)

📊 Password Health Dashboard - Identifies weak and duplicate passwords

🏷️ Smart Categories - Work, Personal, Finance, Social, Other

🔍 Real-Time Search & Filter - Instant filtering by name, username, category

📋 One-Click Copy - Auto-clearing clipboard (10s, 30s, 1min, or never)

User Experience
🌓 Dark/Light Theme - Persistent user preference

⏰ Auto-Lock Timer - 1min, 5min, 15min, 30min, or never

⌨️ Keyboard Shortcuts - Ctrl+L (lock), Ctrl+S (search), Ctrl+N (new entry)

🔔 Toast Notifications - Visual feedback for all actions

📱 Fully Responsive - Works on desktop, tablet, and mobile

Backup & Recovery
📤 Encrypted Export - Download encrypted JSON backup

📥 Secure Import - Restore from backup with master password verification

🔑 Change Master Password - Re-encrypt entire vault with new password

🗑️ Reset Vault - Complete data wipe with confirmation

🔐 Security Architecture
Encryption Flow
text
Master Password
      ↓
   PBKDF2 (600k iterations + random salt)
      ↓
   AES-256-GCM Key
      ↓
   Individual Entry Encryption (unique IV per entry)
      ↓
   Encrypted Vault → localStorage
Key Security Properties
Never Trust the Server - No backend, no data transmission

Unique IV per Entry - Prevents pattern analysis

Random Salt per Vault - Prevents rainbow table attacks

Client-Side Only - All crypto happens in your browser

No Telemetry - Zero tracking, analytics, or external calls

Data Structure (Encrypted Vault)
json
{
  "version": "1.0",
  "salt": "base64_encoded_random_salt",
  "hint": "Optional reminder (unencrypted)",
  "settings": {
    "autoLockMinutes": 5,
    "clearClipboardSeconds": 30,
    "showStrengthMeter": true
  },
  "encVault": "AES-256-GCM encrypted entries"
}
🚀 Quick Start
Option 1: Live Demo
Simply visit https://vault.parrysecurity.online - no installation required!

Option 2: Local Development

# Clone the repository
git clone https://github.com/yourusername/vaultify.git
cd vaultify

# Start a local server (choose one)
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js (if installed)
npx http-server -p 8000

# PHP (if installed)
php -S localhost:8000

# Open in browser
open http://localhost:8000
Option 3: Production Deployment (Apache)

# Copy to Apache directory
sudo cp -r vaultify /var/www/html/

# Set permissions
sudo chown -R www-data:www-data /var/www/html/vaultify/
sudo chmod -R 755 /var/www/html/vaultify/

# Configure virtual host (optional)
sudo nano /etc/apache2/sites-available/vaultify.conf
Example virtual host configuration:

apache
<VirtualHost *:80>
    ServerName vault.parrysecurity.online
    DocumentRoot /var/www/html/vaultify
    
    <Directory /var/www/html/vaultify>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog ${APACHE_LOG_DIR}/vaultify-error.log
    CustomLog ${APACHE_LOG_DIR}/vaultify-access.log combined
</VirtualHost>

# Enable site and restart
sudo a2ensite vaultify.conf
sudo systemctl restart apache2
💻 Technical Stack
Frontend
HTML5 - Semantic markup

CSS3 - Modern styling with CSS variables for theming

Vanilla JavaScript - No frameworks, pure JS

Cryptographic APIs
Web Crypto API - crypto.subtle for AES-256-GCM and PBKDF2

crypto.getRandomValues - Secure random number generation

Storage
localStorage - Encrypted vault persistence

sessionStorage - Temporary session management

No Dependencies
Zero external npm packages

Zero third-party libraries (except FontAwesome for icons via CDN)

Fully self-contained single HTML file

📁 Project Structure
text
vaultify/
├── index.html              # Complete application (single file)
├── README.md               # This file
├── LICENSE                 # MIT License
├── .gitignore             # Git ignore rules
└── assets/
    └── screenshots/       # Documentation images
        ├── dashboard.png
        ├── add-entry.png
        └── health-report.png
🔧 Installation & Deployment
Requirements
Web Server - Apache, Nginx, or any static file server

HTTPS - Required for Web Crypto API (except localhost)

Modern Browser - See browser support below

HTTPS Configuration (Important!)
Web Crypto API's crypto.subtle requires HTTPS except on localhost.

For Production (Let's Encrypt + Apache):

# Install Certbot
sudo apt update
sudo apt install certbot python3-certbot-apache

# Obtain SSL certificate
sudo certbot --apache -d vault.parrysecurity.online

# Auto-renewal (certbot adds cron job automatically)
For Production (Let's Encrypt + Nginx):

sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d vault.parrysecurity.online
Self-Signed Certificate (Testing Only):

# Generate self-signed cert
sudo mkdir /etc/apache2/ssl
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout /etc/apache2/ssl/vaultify.key \
    -out /etc/apache2/ssl/vaultify.crt

# Configure SSL virtual host
sudo nano /etc/apache2/sites-available/vaultify-ssl.conf
Environment Variables
None! Vaultify has no backend, no API keys, no environment configuration.

🧪 Testing
Manual Test Checklist
First-time setup - Creates vault with master password

Wrong password rejection - Shows error for incorrect master password

Add entry - Saves website, username, password, category

Password generator - Creates strong passwords (8-64 chars)

Copy functions - Username/password copy with auto-clear

Search & filter - Real-time filtering by text and category

Edit entry - Updates all fields, updates timestamp

Delete entry - Removes with confirmation dialog

Auto-lock - Locks after inactivity (1-30 min options)

Export/Import - Backup and restore functionality

Change master password - Re-encrypts all entries

Health report - Identifies weak/duplicate passwords

Dark/Light mode - Toggle and persistence

Keyboard shortcuts - Ctrl+L, Ctrl+S, Ctrl+N, ESC

Browser DevTools Testing
javascript
// Test crypto availability
console.log(window.crypto.subtle); // Should return object

// Check localStorage after creating vault
console.log(localStorage.getItem('vaultpro_v1')); // Encrypted data

// Simulate 100 entries (performance test)
for(let i = 0; i < 100; i++) {
  // Add test entries via UI
}
Security Testing

# Check for HTTPS (should be required)
curl -I https://vault.parrysecurity.online

# Verify no external API calls
# Open DevTools → Network tab → Should see zero requests

# Check localStorage encryption
# Application tab → Local Storage → Data should be encrypted
🛡️ Security Best Practices
For Users
Use a strong master password - 12+ characters with mixed case, numbers, symbols

Enable auto-lock - Set to 5 minutes or less

Regular backups - Export vault after adding important passwords

Use HTTPS - Never use over HTTP (Web Crypto API requires HTTPS)

Logout on shared devices - Manually lock vault when done

For Developers
Code audit - Review crypto implementation

No modifications - Don't add external analytics or tracking

Keep dependencies minimal - Currently zero npm packages

HTTPS everywhere - Enforce secure connections

Content Security Policy - Consider adding CSP headers

Security Limitations (Transparent Disclosure)
Client-side only - No protection against device compromise

localStorage - Vulnerable to XSS (though no external scripts)

No 2FA - Single-factor authentication only

No password recovery - Lost master password = lost vault

🌐 Browser Support
Browser	Minimum Version	Status
Chrome	60+	✅ Full support
Firefox	55+	✅ Full support
Edge	79+	✅ Full support
Safari	15+	✅ Full support
Opera	50+	✅ Full support
Internet Explorer	-	❌ Not supported
Required APIs:

Web Crypto API (crypto.subtle)

TextEncoder/TextDecoder

localStorage

ES6+ JavaScript

❓ FAQ
Is Vaultify really secure?
Yes. All encryption happens locally in your browser using the Web Crypto API (AES-256-GCM). Your master password never leaves your device, and we don't have any servers to breach.

Can I sync across devices?
No. Vaultify is intentionally offline-only. Use the export/import feature to manually transfer vaults between devices.

What if I forget my master password?
Your data is unrecoverable. There's no "forgot password" feature - that would be a security vulnerability. Use the hint feature to help remember.

Is my data backed up?
Not automatically. Use the Export feature to create encrypted backups. Store backups securely (e.g., encrypted USB drive, password manager).

Can I trust the password generator?
Yes. It uses crypto.getRandomValues() - the same cryptographically secure RNG used by major browsers for TLS.

Why do I need HTTPS?
Web Crypto API's crypto.subtle requires HTTPS (or localhost) for security. This prevents man-in-the-middle attacks that could compromise encryption.

Is there a mobile app?
No. The web app is fully responsive and works on mobile browsers. Add to home screen for an app-like experience.

How many passwords can I store?
Theoretically unlimited. localStorage limits vary by browser (typically 5-10MB), which can store thousands of encrypted entries.

🤝 Contributing
We welcome contributions! Here's how you can help:

Report Bugs
Use the Issue Tracker

Include browser version, steps to reproduce, and screenshots

Suggest Features
Open an issue with the enhancement label

Describe the feature and use case

Submit Pull Requests
Fork the repository

Create a feature branch (git checkout -b feature/amazing-feature)

Commit changes (git commit -m 'Add amazing feature')

Push to branch (git push origin feature/amazing-feature)

Open a Pull Request

Development Guidelines
Maintain zero external dependencies

Preserve backward compatibility

Follow existing code style (vanilla JS, no frameworks)

Update documentation (README.md)

Test across multiple browsers

📄 License
Distributed under the MIT License. See LICENSE file for details.

text
MIT License

Copyright (c) 2024 ParrySecurity

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
🙏 Acknowledgments
Web Crypto API - For native browser encryption

FontAwesome - For beautiful icons (CDN)

Google Fonts - For DM Sans and JetBrains Mono fonts

Community - All users and contributors who prioritize security

📞 Contact & Support
Live Demo: https://vault.parrysecurity.online

Issues: GitHub Issues

Security Reports: securityparry@gmail.com

⭐ Star History
If you find Vaultify useful, please consider starring the repository on GitHub!

https://api.star-history.com/svg?repos=yourusername/vaultify&type=Date

🔐 Your passwords. Your encryption. Your rules.

Made with 🔒 by ParrySecurity
