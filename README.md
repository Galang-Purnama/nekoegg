# 🐾 NekoEgg Commercial Edition (IP-Based Rental Runtime)

[![Pterodactyl Egg](https://img.shields.io/badge/Pterodactyl-PTDL__v2-blue?style=for-the-badge&logo=pterodactyl)](https://pterodactyl.io/)
[![Docker Image](https://img.shields.io/badge/Docker-ghcr.io%2Fgalang--purnama%2Fnekoegg%3Alatest-2496ED?style=for-the-badge&logo=docker)](https://github.com/Galang-Purnama/NekoHost-EGG)
[![Licensing](https://img.shields.io/badge/Licensing-Pure%20IP--Whitelisting-brightgreen?style=for-the-badge&logo=shield)](https://nekohost.id)
[![Edition](https://img.shields.io/badge/Edition-Commercial%20%2F%20Rental-gold?style=for-the-badge&logo=probot)](https://nekohost.id)
[![Multi Runtime](https://img.shields.io/badge/Runtimes-Node%20%7C%20Bun%20%7C%20Deno%20%7C%20Python%20%7C%20Go%20%7C%20PHP%20%7C%20Redis-blueviolet?style=for-the-badge)](https://nekohost.id)

**NekoEgg Commercial Edition** adalah Egg Pterodactyl & Pelican all-in-one multi-runtime edisi sewa komersial. Menggabungkan ekosistem bahasa pemrograman terlengkap (Node.js, Bun, Deno, Python, Golang, PHP, Redis) dengan sistem proteksi lisensi **Pure IP-Based Whitelisting (Zero-Config untuk Penyewa)**.

---

## ⚡ Highlights

* **Zero-Config Licensing**: Otorisasi lisensi otomatis berbasis IP VPS node host saat startup. Penyewa tidak perlu memasukkan token lisensi secara manual.
* **Unified Multi-Runtime**: Ekosistem Node.js, Bun, Deno, Python (dengan Astral UV), Golang, PHP (Composer), dan embedded Redis server internal.
* **Media, OCR & Scraping Suite**: Dilengkapi Tesseract OCR (Bahasa Indo & Eng), libvips (`vips`), WebP tools lengkap, FFmpeg, ImageMagick, serta headless Chromium.
* **Host Anti-Abuse Hardening**: Proteksi aktif anti-miner, anti-torrent (DMCA), mitigasi DDoS flooder, isolasi workspace, dan sistem proteksi credentials.

---

## 📦 Runtime & Ekosistem Lengkap

| Komponen | Versi yang Didukung | Keterangan & Cara Pakai |
| :--- | :--- | :--- |
| **Node.js** | 20, 22, 24, 25, 26 *(Default: 26)* | Variabel `NODE_VERSION` / `nvm use <ver>` |
| **Bun** | Latest Stable | `bun run <file>`, `bun install` |
| **Deno** | 1.x, 2.x, latest *(Default: latest)* | Variabel `DENO_VERSION` / `deno run` |
| **Python** | 3.10, 3.11, 3.12, 3.13, 3.14 + **Astral UV** | Variabel `PYTHON_VERSION` / `uv pip install` |
| **Golang** | 1.22, 1.23, 1.24, 1.25, 1.26 *(Default: 1.26)* | Variabel `GO_VERSION` / `go run` |
| **PHP** | 8.1, 8.2, 8.3, 8.4 + **Composer** | Variabel `PHP_VERSION` / `composer install` |
| **Redis** | Internal Local Server & Remote Mode | `REDIS_MODE=local` / `redis-cli` |
| **Tesseract OCR** | Bahasa Indonesia (`ind`) & Inggris (`eng`) | `tesseract input.png output -l ind` |
| **Media Engine** | FFmpeg, SoX, WebP, Libvips, ImageMagick | Video/audio convert, WA sticker & graphics |
| **Scraper / Browser** | Chromium Headless + Fonts Emoji/CJK | Puppeteer & Playwright ready |
| **Tunneling** | Cloudflare Zero Trust, Bore TCP, Localtunnel | `cloudflared`, `bore`, `lt` |

---

## 🌐 Sistem Otorisasi Lisensi

Semua proses verifikasi lisensi berjalan secara instan dan otomatis di latar belakang:

1. **Pendaftaran Node**: Admin mendaftarkan IP Publik VPS node server ke sistem NekoHost.
2. **Booting Otomatis**: Saat container server Pterodactyl dinyalakan, engine memvalidasi status IP node secara instan.
3. **Siap Pakai**: Jika terdaftar dan aktif, server langsung berjalan lancar tanpa konfigurasi tambahan dari penyewa.

---

## 🚀 Panduan Pemasangan

1. Download file [`egg.json`](egg.json) dari repository ini.
2. Buka **Admin Panel Pterodactyl** → **Nests** → Pilih Nest → Klik **Import Egg**.
3. Pastikan konfigurasi image mengarah ke:
   ```text
   ghcr.io/galang-purnama/nekoegg:latest
   ```
4. Buat Server baru dengan Egg tersebut. Server langsung aktif seketika.

---

## 🛡️ Keamanan & Proteksi Host

NekoEgg dilengkapi sistem pengamanan multi-lapis aktif untuk menjamin stabilitas, kepatuhan, dan reputasi node host:

* **Anti-Crypto Mining**: Proteksi aktif terhadap aktivitas penambangan aset kripto terlarang.
* **DMCA & Torrent Guard**: Filter pencegahan lalu lintas client BitTorrent demi kepatuhan hukum provider host.
* **Anti-DDoS & Traffic Flood Limiter**: Mitigasi otomatis terhadap script penyerang jaringan dan anomali traffic storm.
* **Anti-Reverse Shell & Backdoor Protection**: Pengawasan cerdas terhadap aktivitas eksekusi remote shell yang tidak sah.
* **Privilege Escalation Prevention**: Pembatasan akses terhadap perintah administratif sistem demi isolasi container yang ketat.
* **Sensitive Credentials Protector**: Perlindungan hak akses file konfigurasi dan token otentikasi secara otomatis.
* **Workspace Isolation**: Isolasi direktori kerja pengguna untuk mencegah akses ke direktori sistem.
* **Resource Quota & Stability Guard**: Pembatasan alokasi proses maksimal demi menjamin stabilitas CPU dan memori node host.

---

## ⌨️ Pintasan CLI Bawaan

| Perintah | Deskripsi Fungsi |
| :--- | :--- |
| `refresh` / `sysinfo` | Menampilkan dashboard info sistem, pemakaian CPU/RAM, dan status runtime |
| `ff` | Menjalankan Fastfetch untuk detail arsitektur container |
| `myip` | Memeriksa IP publik keluar VPS secara instan |
| `ports` | Memeriksa daftar port jaringan yang sedang aktif / listening |
| `clean-cache` | Membersihkan cache npm, yarn, pnpm, pip, uv, composer & deno |
| `protect-env` | Mengunci dan mengamankan file konfigurasi & credentials |
| `pm2-save` | Menyimpan status daftar proses PM2 agar restart otomatis |
| `pm2-list` | Menampilkan tabel status semua proses PM2 yang berjalan |
| `cls` | Membersihkan layar konsol terminal |
| `test-notify` | Menguji webhook Discord / Telegram bot notification |

---

## 📞 Layanan & Dukungan

Untuk pendaftaran IP node, perpanjangan masa aktif sewa, atau konsultasi:

* 🌐 **Website:** [https://nekohost.id](https://nekohost.id)
* 📧 **Email:** `support@nekohost.id`
* 💬 **WhatsApp Admin:** [https://wa.me/6281319859673](https://wa.me/6281319859673)
* ✈️ **Telegram Dukungan:** [https://t.me/GalangP_Dev](https://t.me/GalangP_Dev)

---

<div align="center">
  <b>© 2026 NekoHost.id • All Rights Reserved</b><br>
  <i>Empowering High-Performance Runtimes with Next-Gen DRM Protection.</i>
</div>
