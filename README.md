# 🚀 CMH Panel

<p align="center">

🌐 **Languages**

[🇮🇷 فارسی](README_FA.md) • **🇺🇸 English**

</p>

<p align="center">
  <img src="https://img.shields.io/badge/Cloudflare-Workers-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare Workers">
  <img src="https://img.shields.io/badge/Cloudflare-D1-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare D1">
  <img src="https://img.shields.io/badge/Version-1.0.0-blue?style=for-the-badge" alt="Version">
</p>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Screenshots](#-screenshots)
- [Quick Setup Guide](#-quick-setup-guide)
- [Architecture](#️-architecture)
- [Design Philosophy](#-design-philosophy)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)
- [Author](#-author)

---

# 📖 Overview

CMH Panel is a lightweight proxy management panel built entirely on **Cloudflare Workers** and **Cloudflare D1**.

Instead of adding endless configuration options, CMH Panel focuses on the features that users actually need.

Its primary goals are:

- ⚡ Fast deployment
- 🔒 Stable connections
- 📦 Clean subscription generation
- 🚀 High compatibility with popular clients
- 🛡️ Reliable fragmentation for DPI bypass

---

# ✨ Key Features

## 🛡️ Core Proxy & Connections

- VLESS & Trojan support
- Cloudflare Edge Routing via WebSocket
- TLS & Non-TLS support
- Multiple ports
- Custom client fingerprints
- Smart Fragment (Length / Interval / Packets)

---

## 👥 User & Traffic Management

- Total & Daily traffic limits (GB / Requests)
- User expiration management
- Real-time Cloudflare Analytics
- One-click enable, disable and reset

---

## 🤖 Telegram Bot Integration

Manage the entire panel directly from Telegram.

- Create, edit and delete users
- Monitor traffic
- View Cloudflare usage
- Enable or disable the system
- No dashboard required

---

## 🔗 Subscription System

- Base64 subscriptions
- Clash YAML
- JSON output
- Dedicated subscription page
- Live traffic statistics
- QR Code generation
- One-click copy
- Anti-duplicate Clash profile naming

---

# 📸 Screenshots

### Connection Profiles & Subscriptions

![Profiles](images/profiles.png)

### User Management & Limits

![Users](images/users.png)

### Global System Settings

![Settings](images/settings.png)

---

## 🚀 Quick Setup Guide

You can deploy CMH Panel using one of the following methods:

### 🤖 Method 1: Automated Deployment via Telegram Bot (Recommended)

Deploy the panel in seconds using our official Telegram bot. No manual setup is required.

1. Get your **Cloudflare API Token** from your Cloudflare dashboard.
2. Go to our Deployment Bot: [👉 Click Here to Start 👈](https://t.me/CMH_Hub_Bot)
3. Send your API token to the bot and follow the simple on-screen instructions. The bot will handle the database creation and worker deployment automatically.

---

### 🛠️ Method 2: Manual Deployment via Cloudflare Dashboard

If you prefer to deploy manually, follow these steps:

#### 1. Database Initialization
- Navigate to Cloudflare Dashboard → **Storage & Databases** → **D1 SQLite**.
- Create a database (e.g., `cf_db`).

#### 2. Deployment & Binding
- Create a new Cloudflare Worker and paste your code.
- Go to **Settings** → **Bindings** → **Add Binding**.
- **Crucial Step:** You must add the D1 database binding exactly as follows:
  - Type: `D1 Database`
  - Variable Name: `CMH_Hub`
  - Database: Select the database you created in Step 1.
- Deploy the worker.

#### 3. Access Your Panel
- You can access your dashboard via the following URL format (replace `<your-worker-url>` with your actual worker address):
  ```text
  https://<your-worker-url>.workers.dev/cmh/dash
  ```
Login: Use the default password below:
  ```text
  admin
  ```

---

## ⚙️ Architecture
```text
Client
   │ (VLESS / Trojan / Fragment)
   ▼
Cloudflare Worker ─────► Cloudflare D1
   │                        ├── User Limits
   ├── Web Dashboard        ├── Expirations
   ├── Telegram Bot         └── System Config
   ├── Subscription Engine
   └── Proxy Gateway
            │
            ▼
      Destination Server
```

---

## 💡 Design Philosophy

CMH Panel follows one simple principle:

> Remove what users don't need and improve what they use every day.

Instead of adding countless niche features, development focuses on:

- Better connection stability
- Cleaner subscriptions
- Lightweight and modern UI
- Faster deployment
- Better overall user experience

---

## 🔒 License

The source code of this project has been intentionally obfuscated to protect its routing mechanisms and core implementation.

This repository is provided for deployment and public use only. Redistribution or modification without permission is not allowed.

---

## 🙏 Acknowledgements

Parts of the overall structure and workflow were inspired by the **[Nahan](https://github.com/itsyebekhe/nahan)** project.

Special thanks to its developers and contributors for their valuable work.

---

## 👤 Author

**CMH Hub**

💬 Telegram: **[CMH_Hub](https://t.me/CMH_Hub)**