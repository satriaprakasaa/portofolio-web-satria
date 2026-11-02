# 🌐 \[PERSONAL PROJECT\] Cyberpunk Network Portfolio & Edge DNS Integration

Dokumen ini berisi dokumentasi teknis, perancangan antarmuka bergaya *Cyberpunk*, serta studi kasus pengintegrasian infrastruktur jaringan/DNS untuk **Website Portofolio Pribadi Satria Prakasa Simbolon** (Mahasiswa Sistem Telekomunikasi - Spesialisasi Network & Security Engineering).

🔗 **Live Website:** <https://satriaps.my.id>

🔗 **Alternative URL:** <https://www.satriaps.my.id>

## 📸 Preview Tampilan & Dokumentasi

| Desktop View (Hero) | Terminal CLI Easter Egg |
| :---: | :---: |
| <img src="Portofolio Web Satria/docs/hero.png" width="450" alt="Desktop View"> | <img src="Portofolio Web Satria/docs/terminal.png" width="450" alt="Terminal CLI"> |

| 3D Tilt Projects | Skills |
| :---: | :---: |
| <img src="Portofolio Web Satria/docs/3d-tilt.png" width="450" alt="3D Tilt Projects"> | <img src="Portofolio Web Satria/docs/skills.png" width="450" alt="Skills Section"> |

## 📌 Ringkasan Proyek (Overview)

Proyek ini bertujuan untuk membangun platform portofolio web statis yang sangat ringan, super cepat, dan interaktif. Dibangun tanpa *build-tools* yang berat, proyek ini mendemonstrasikan optimalisasi *Single-File Application* yang dipadukan dengan desain *Glassmorphism* dan pengelolaan aset di tingkat *Edge Network*.

### ✨ Fitur Utama:

* **Interactive Particle Network:** Latar belakang *canvas* jaringan (*nodes & edges*) yang bereaksi secara dinamis terhadap pergerakan kursor (Mouse Interactivity).

* **Interactive CLI Terminal Emulator:** Widget terminal *Linux-style* tersembunyi yang merespons perintah teks input kustom (contoh: `help`, `projects`, `about`).

* **3D Tilt Project Cards:** Kartu portofolio interaktif yang merespons pergerakan kursor dengan rotasi 3D dan efek pantulan cahaya (*glare*) menggunakan `vanilla-tilt.js`.

* **Neon & Glassmorphism UI:** Desain modern dengan palet warna *cyberpunk* (Cyan & Neon Purple) serta komponen *frosted-glass*.

* **Pulsing Availability Status:** Indikator status "Open for Internships" animasi CSS secara *real-time*.

* **Direct PDF Asset Downloader:** Integrasi pengunduhan *Curriculum Vitae* (CV) tanpa *redirect*, langsung dari direktori lokal.

## 🛠️ Stack Teknologi & Infrastruktur

Berbeda dengan arsitektur sebelumnya yang menggunakan *framework* berat, versi ini dioptimasi untuk kecepatan maksimal dengan pendekatan *Vanilla*:

* **Frontend Structure:** HTML5

* **Styling:** Tailwind CSS (via CDN) & Custom CSS Keyframes

* **Interactivity:** Vanilla JavaScript (ES6)

* **Libraries:** [Vanilla-Tilt.js](https://micku7zu.github.io/vanilla-tilt.js/), FontAwesome 6

* **Hosting & Deployment:** Vercel Cloud Platform (Manual Edge Deployment)

* **DNS Architecture:** Anycast Routing (A Record & CNAME)

## 📡 Konfigurasi Network & DNS Integration

Sebagai bagian dari implementasi *Network Engineering*, domain kustom `satriaps.my.id` dikonfigurasikan secara manual untuk mengarahkan trafik dari *Registrar* ke *Vercel Edge Network*:

### 1. Tabel DNS Records

| Record Type | Hostname / Name | Value / Destination | Fungsi | 
| ----- | ----- | ----- | ----- | 
| **A Record** | `@` | `216.198.79.1` | Mengarahkan root domain ke IP Anycast Vercel | 
| **CNAME** | `www` | `97020c266769703e.vercel-dns-017.com` | Mengarahkan trafik sub-domain ke edge DNS Vercel | 

### 2. Edge Routing & SSL Verification

* **Permanent Redirection (308):** Mengarahkan seluruh trafik HTTP otomatis ke HTTPS (Strict Transport Security).

* **SSL Certificate Provisioning:** Enkripsi TLS otomatis diverifikasi dan diperbarui secara berkala oleh Vercel CA (Let's Encrypt).

## 📁 Struktur Direktori Proyek

Proyek ini sengaja menggunakan struktur *flat-directory* (tanpa folder kompleks) untuk mempermudah *maintenance* dan memungkinkan proses *deployment* instan:

```
Portofolio Web Satria
├── docs                            # Direktori untuk tangkapan layar (dokumentasi repo)
├── index.html                      # Core application (HTML, CSS, JS terintegrasi)
├── CV-Satria Prakasa Simbolon.pdf  # File aset statis CV
└── README.md                       # Dokumentasi utama proyek
```

## 🚀 Alur Deployment & Pengujian Lokal

Karena proyek ini mengadopsi arsitektur *Serverless Static Frontend*, tidak diperlukan instalasi *Node Modules* atau *Build Pipeline* yang rumit. 

### Proses Deployment (Vercel)
Website ini di-*deploy* menggunakan metode **Vercel Drag-and-Drop Dropzone**. Cukup mengunggah direktori proyek secara langsung ke dashboard Vercel, dan sistem akan mengonfigurasikan *Edge CDN* serta sertifikat SSL secara instan.

### Menjalankan di Komputer Lokal (Bagi Pengunjung)
Jika Anda ingin menguji kode ini di perangkat Anda:
1. **Unduh** repositori ini (.zip) atau gunakan perintah Git:
   ```bash
   git clone https://github.com/satriaprakasaa/portofolio-web-satria.git
   ```
2. Buka folder hasil unduhan.
3. Klik dua kali pada file `index.html` untuk menjelajah secara *offline* di browser Anda tanpa perlu konfigurasi *localhost server*.

*Didesain dan dikembangkan oleh [Satria Prakasa Simbolon](https://linkedin.com/in/satriaprakasaa).*
