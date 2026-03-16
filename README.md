# 🔐 Locksy `v1.0.0`

> **Zero-knowledge password manager. Your vault, your rules.**  
> Built with React Native · .NET · AES-256-GCM

---

## ✦ What is Locksy?

Locksy is a personal password manager built on a **zero-knowledge architecture** — your master password never leaves your device. Every credential is encrypted client-side using AES-256-GCM before it ever touches a server.

No one can read your passwords. Not even us.

---

## ✦ What's in this release

### 🔒 Security
- **AES-256-GCM** end-to-end encryption
- **PBKDF2** key derivation from master password
- **Zero-knowledge** architecture — server only stores ciphertext
- **Screen capture protection** on credential detail view
- **Biometric unlock** — Face ID / Fingerprint
- **PIN lock** — 4-digit PIN with shuffled keypad on unlock screen
- Auto-lock when app goes to background

### 🗄️ Vault
- Create, edit, delete encrypted credentials
- Fields: site/app, username, password, category, notes
- **Password strength indicator** (5-level bar)
- **Password generator** — configurable length, uppercase, numbers, symbols
- Favorite credentials with quick filter
- Search across title and username
- Filter by category

### 🗂️ Categories
- Create custom categories with name, icon (15 presets) and color (10 presets)
- Live preview when creating
- Credential count per category
- Shared state — changes reflect instantly across all screens

### 👤 Profile
- Google OAuth login
- Master password setup on first access
- Security status overview
- Encryption details & how it works
- App version, stack, license info

### ⚙️ Settings
- Toggle **PIN lock** (configure 4-digit PIN)
- Toggle **Face ID / Fingerprint**
- PIN and biometric are mutually exclusive
- Security configs cleared on logout or uninstall
- Delete account permanently (zero-knowledge — data is unrecoverable)

---

## ✦ Tech stack

| Layer | Technology |
|---|---|
| Mobile | React Native (Expo) |
| Backend | .NET 8 / C# |
| Database | MySQL |
| Auth | Google OAuth 2.0 + JWT |
| Encryption | AES-256-GCM · PBKDF2 |
| Storage | expo-secure-store · AsyncStorage |

---

## ✦ Security model

```
Master Password
      │
      ▼
  PBKDF2 (key derivation)
      │
      ▼
  AES-256-GCM key  ──►  Encrypt credential
                               │
                               ▼
                        Ciphertext + IV
                               │
                               ▼
                         Sent to server
                      (unreadable without key)
```

The master password is stored only in `expo-secure-store` on the device.  
The server stores `encryptedPassword` + `iv` — nothing more.  
If you lose your master password, your data is **permanently unrecoverable**.

---

## ✦ Roadmap

- [ ] Auto-lock timer (configurable idle timeout)
- [ ] Failed PIN attempts lockout
- [ ] Duplicate & weak password detection
- [ ] Swipe-to-copy from credential list
- [ ] Encrypted notes (standalone, no username/password)
- [ ] Encrypted vault backup export (`.locksy` file)
- [ ] Import from CSV / Bitwarden

---

## ✦ License

**All rights reserved © 2025 Locksy**  
This software is proprietary. Unauthorized distribution or reproduction is prohibited.

---

<div align="center">

**LOCKSY** · Zero-knowledge · AES-256 · Built with ♥

</div>
