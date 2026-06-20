# 🏗️ Collab Board

<p align="center">
  <img src="https://img.shields.io/badge/Laravel-11-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" />
  <img src="https://img.shields.io/badge/Livewire-3-4E56A6?style=for-the-badge&logo=livewire&logoColor=white" />
  <img src="https://img.shields.io/badge/Firebase-Realtime_DB-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" />
  <img src="https://img.shields.io/badge/PHP-8.4-777BB4?style=for-the-badge&logo=php&logoColor=white" />
</p>

<p align="center">
  Real-time collaborative architecture board — dibuat untuk demo <strong>Batam DEV</strong>.<br/>
  Audience scan QR code, tambah komponen, dan liat canvas bergerak bareng secara live.
</p>

---

## ✨ Demo

> 🚧 Work in progress — dibangun live di Batam DEV

---

## 💡 Ide

Daripada presentasi satu arah, bagaimana kalau **semua orang ikut mendesain sistemnya bareng**?

1. Presenter tampilkan QR code di layar
2. Audience scan → buka di HP masing-masing
3. Audience pilih komponen arsitektur (Database, API, Queue, dll)
4. Komponen langsung muncul di canvas presenter — **tanpa refresh**

---

## 🧱 Tech Stack

| Layer | Teknologi |
|---|---|
| Backend | Laravel 11 |
| Realtime | Firebase Realtime Database |
| Frontend Presenter | Livewire 3 + Alpine.js |
| Frontend Audience | Blade + Vanilla JS |
| Canvas | Konva.js |
| QR Code | `simplesoftwareio/simple-qrcode` |
| Firebase PHP | `kreait/laravel-firebase` |

---

## 🚀 Instalasi

### Prerequisites

- PHP >= 8.4
- Composer
- Node.js >= 18
- Akun Firebase (gratis)

### Setup

```bash
# Clone repo
git clone https://github.com/irwanda/collab-board.git
cd collab-board

# Install dependencies
composer install
npm install

# Setup environment
cp .env.example .env
php artisan key:generate

# Jalankan
php artisan serve
npm run dev
```

### Firebase Setup

1. Buat project di [Firebase Console](https://console.firebase.google.com)
2. Aktifkan **Realtime Database**
3. Download service account key → simpan ke `storage/app/firebase/credentials.json`
4. Isi variabel Firebase di `.env` (lihat `.env.example`)

---

## 🗂️ Struktur Project

```
collab-board/
├── app/
│   ├── Http/Controllers/
│   │   ├── SessionController.php     # Kelola sesi & QR code
│   │   └── ComponentController.php   # Handle komponen canvas
│   ├── Livewire/
│   │   └── PresenterCanvas.php       # Layar presenter (big screen)
│   └── Services/
│       └── FirebaseService.php       # Wrapper Firebase operations
├── resources/views/
│   ├── welcome.blade.php             # Buat sesi baru
│   ├── presenter.blade.php           # Layar besar
│   └── audience.blade.php            # View HP audience
└── routes/web.php
```

---

## 🗺️ Alur Data

```
Audience (HP)
    │
    │  HTTP POST (add component)
    ▼
Laravel Backend
    │  validate & write
    ▼
Firebase Realtime DB ──── real-time listen ────▶ Presenter Canvas
```

---

## 🧩 Component Types

`client` · `api` · `database` · `cache` · `queue` · `load_balancer` · `storage` · `note`

---

## 📄 License

MIT — bebas dipakai dan dimodifikasi.

---

<p align="center">
  Dibuat dengan ☕ untuk <a href="#">Batam DEV Community</a>
</p>
