# 🚀 CMH Panel (v2.1.0)

<p align="center">

🌐 **Languages**

[🇮🇷 فارسی](README_FA.md) • **🇺🇸 English**

</p>

<p align="center">
  <img src="https://img.shields.io/badge/Cloudflare-Workers-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare Workers">
  <img src="https://img.shields.io/badge/Cloudflare-D1-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" alt="Cloudflare D1">
  <img src="https://img.shields.io/badge/Architecture-Master--Edge-success?style=for-the-badge" alt="Architecture">
  <img src="https://img.shields.io/badge/Version-2.1.0-blue?style=for-the-badge" alt="Version">
</p>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Comprehensive Documentation](#-comprehensive-documentation)
- [Key Features](#-key-features)
- [Architecture](#️-architecture)
- [Screenshots](#-screenshots)
- [Quick Setup Guide](#-quick-setup-guide)
- [Design Philosophy](#-design-philosophy)
- [License](#-license)

---

## 📖 Overview

CMH Panel is a powerful, lightweight, and scalable proxy management panel built entirely on **Cloudflare Workers** and **Cloudflare D1**.

With the release of **v2.1.0**, CMH Panel has evolved into a full **Cluster Management System**, introducing a **Master-Edge Architecture**. You can now deploy one Master node to handle the database and UI, and multiple Edge nodes to act as load balancers — drastically reducing database read/write operations while handling massive traffic.

---

## 📚 Comprehensive Documentation

> **💡 Need help understanding the settings?**
> A complete offline guide is included in this repository.
>
> Simply open the **[Help](https://call-me-h.github.io/CMH-Panel/Help.html)** to read a detailed explanation of every section of the panel, including Edge Nodes setup, Fragment configurations, User Limits, and Telegram Bot features.

---

## ✨ Key Features

### 🏢 Master-Edge Cluster Architecture *(New in v2.1.0)*

- **Master Node:** Central hub for UI, database management, and subscription routing.
- **Edge Nodes:** Proxy load-balancers that handle traffic and sync with the Master.
- **Smart Caching:** Edge nodes use Cloudflare's Cache API to fetch profiles instantly without querying the Master constantly.
- **Bulk Usage Reporting:** Edge nodes batch traffic usage (>100 requests) before reporting to the Master, reducing D1 DB writes by up to **100x**.

### 🛡️ Core Proxy & Connections

- VLESS (Alpha) & Trojan (Beta) support via WebSockets.
- Smart custom routing and DNS resolving (DoH).
- Backup Relay support (Force proxy routing).
- Advanced Smart Fragment (Length / Interval / Packets) for DPI bypass.
- Custom client fingerprints & multiple port support (TLS / Non-TLS).

### 👥 User & Traffic Management

- Total & Daily traffic limits (GB / Requests).
- User expiration management (Days).
- In-memory usage caching to prevent database limits.
- **Multi-Account Cloudflare Analytics:** Track workers usage across multiple accounts (Master + Edges) simultaneously.

### 🤖 Telegram Bot Integration

- Manage your entire cluster directly from Telegram.
- Create, edit, and delete users on the go.
- Check live Cloudflare usage for all connected nodes.
- Pause/Resume system globally.

### 🔗 Advanced Subscription System

- Base64, Clash YAML, and raw JSON outputs.
- Dedicated modern subscription web page for clients.
- Live traffic statistics & QR Code generation.
- Dynamic naming strategies (e.g., `{PREFIX}-{PORT}-{USER}-{IP}`).

---

## ⚙️ Architecture

```
       Client (VLESS / Trojan / Fragment)
                    │
                    ▼
 ┌───────────────────────────────────────┐
 │          Load Balancing Layer         │
 │   [Edge Node 1]       [Edge Node 2]   │  ◄── Caches profiles, batches usage
 └──────────────────┬────────────────────┘
                    │
            Cache API & REST Sync
                    │
                    ▼
          ┌───────────────────┐
          │    MASTER NODE    │ ◄── Web Dashboard & Telegram Bot
          └─────────┬─────────┘
                    │
             Cloudflare D1 DB
             (Config & Usage)
```

---

## 📸 Screenshots

### User Management
![Users](images/users.png)

### Subscription Profiles
![Profiles](images/profiles.png)

### Settings & Configuration
![Settings](images/settings.png)

---

## 🚀 Quick Setup Guide

### 🤖 Method 1: Automated Deployment via Telegram Bot *(Recommended)*

Deploy the panel in seconds using our official Telegram bot — no manual setup required.

1. Get your **Cloudflare API Token** from your Cloudflare dashboard.
2. Open the Deployment Bot: [👉 Click Here to Start 👈](https://t.me/CMH_Hub_Bot)
3. Send your API token to the bot and follow the on-screen instructions.

---

### 🛠️ Method 2: Manual Deployment

1. Go to Cloudflare Dashboard → **Storage & Databases** → **D1 SQLite** and create a database (e.g., `cf_db`).
2. Create a Cloudflare Worker and paste `worker.js`.
3. Go to **Settings** → **Bindings** → **Add Binding**:
   - Type: `D1 Database`
   - Variable Name: `CMH_Hub` *(case-sensitive)*
   - Database: select your created DB.
4. Deploy and open `https://<your-worker-url>.workers.dev/cmh/dash` (default password: `admin`).

---

## 💡 Design Philosophy

CMH Panel follows one simple principle:

> **Remove what users don't need and perfect what they use every day.**

Development focuses on:

- Highly scalable architectures (Master/Edge).
- Extreme optimization of Cloudflare limits (D1 reads/writes).
- Cleaner subscriptions and a beautiful UI.
- Stable, DPI-resistant connections.

---

## 🙏 Acknowledgements

Parts of the overall structure and workflow were inspired by the **[Nahan](https://github.com/itsyebekhe/nahan)** project.
Special thanks to its developers and contributors for their valuable work.

---

## 🔒 License

Parts of this project's source code have been intentionally obfuscated/minified to protect core routing logic.

This repository is provided for deployment and public use only. Redistribution or modification for commercial purposes without permission is not allowed.

---

## 👤 Author

**CMH Hub**

💬 Telegram Channel: [CMH_Hub](https://t.me/CMH_Hub)
