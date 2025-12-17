# NextAkademi - Sistem Manajemen Data Mahasiswa

Aplikasi web CRUD (Create, Read, Update, Delete) lengkap untuk mengelola data mahasiswa menggunakan Next.js dan Strapi CMS.

![Dashboard](https://img.shields.io/badge/Next.js-16.0.10-black?style=flat-square&logo=next.js)
![Strapi](https://img.shields.io/badge/Strapi-API-blue?style=flat-square)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-Styling-06B6D4?style=flat-square&logo=tailwindcss)

## 📋 Daftar Isi

- [Fitur Utama](#-fitur-utama)
- [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
- [Prasyarat](#-prasyarat)
- [Instalasi dan Persiapan](#-instalasi-dan-persiapan)
- [Menjalankan Aplikasi](#-menjalankan-aplikasi)
- [Struktur Project](#-struktur-project)
- [API Endpoints](#-api-endpoints)
- [Screenshot](#-screenshot)
- [Troubleshooting](#-troubleshooting)

## ✨ Fitur Utama

### CRUD Lengkap
- ✅ **Create** - Tambah data mahasiswa baru via modal form
- ✅ **Read** - Tampilkan semua data mahasiswa dalam tabel
- ✅ **Update** - Edit data mahasiswa via modal form
- ✅ **Delete** - Hapus data mahasiswa dengan konfirmasi modal

### Fitur Tambahan
- 🎨 **UI Modern** - Desain clean dengan Tailwind CSS
- 🌙 **Dark Mode** - Support mode gelap otomatis
- 📱 **Responsive** - Tampilan optimal di semua device
- ⚡ **Real-time Update** - Auto-refresh setelah operasi CRUD
- 🔔 **Notifikasi** - Alert sukses/error untuk setiap operasi
- ✅ **Validasi Form** - Required validation pada semua input
- 🎯 **Modal Konfirmasi** - Konfirmasi delete dengan UI yang user-friendly

## 🛠 Teknologi yang Digunakan

### Frontend
- **Next.js 16** - React framework dengan App Router
- **React 19** - Library UI
- **Tailwind CSS** - Utility-first CSS framework
- **JavaScript (ES6+)** - Bahasa pemrograman

### Backend
- **Strapi CMS** - Headless CMS untuk API
- **REST API** - Komunikasi frontend-backend

## 📦 Prasyarat

Sebelum memulai, pastikan Anda telah menginstall:

- **Node.js** versi 18.x atau lebih tinggi ([Download](https://nodejs.org/))
- **npm** atau **yarn** (sudah termasuk dengan Node.js)
- **Strapi Backend** yang sudah berjalan di `http://localhost:1337`

## 🚀 Instalasi dan Persiapan

### 1. Clone Repository

```bash
git clone <repository-url>
cd nextakademi
```

### 2. Install Dependencies

```bash
npm install
# atau
yarn install
```

### 3. Setup Strapi Backend

Pastikan Strapi backend Anda sudah berjalan dengan collection type `mahasiswa` yang memiliki field:

| Field Name      | Type      | Required |
|----------------|-----------|----------|
| nim            | Text      | Yes      |
| nama           | Text      | Yes      |
| angkatan       | Text      | Yes      |
| jenis_kelamin  | Text      | Yes      |
| tanggal_lahir  | Date      | Yes      |
| alamat         | Text      | Yes      |
| email          | Email     | Yes      |
| state          | Text      | Yes      |

**Contoh struktur data Strapi:**
```json
{
  "data": {
    "nim": "1122102031",
    "nama": "M. Taufiq",
    "angkatan": "2022",
    "jenis_kelamin": "L",
    "tanggal_lahir": "2025-10-08",
    "alamat": "Grogol",
    "email": "mtaufiq39@yahoo.com",
    "state": "Aktif"
  }
}
```

### 4. Konfigurasi API (Opsional)

Jika Strapi backend Anda berjalan di URL yang berbeda, edit file `app/page.js` dan ubah base URL:

```javascript
// Ubah dari:
fetch('http://localhost:1337/api/mahasiswas')

// Menjadi:
fetch('http://your-strapi-url/api/mahasiswas')
```

## 🎯 Menjalankan Aplikasi

### Development Mode

```bash
npm run dev
# atau
yarn dev
```

Aplikasi akan berjalan di [http://localhost:3000](http://localhost:3000)

### Production Build

```bash
# Build aplikasi
npm run build

# Jalankan production server
npm start
```

## 📁 Struktur Project

```
nextakademi/
├── app/
│   ├── favicon.ico          # Icon aplikasi
│   ├── globals.css          # Global styles
│   ├── layout.js            # Root layout
│   └── page.js              # Halaman utama (CRUD)
├── public/                  # Static files
├── .gitignore
├── eslint.config.mjs        # ESLint config
├── jsconfig.json            # JavaScript config
├── next.config.mjs          # Next.js config
├── package.json             # Dependencies
├── postcss.config.mjs       # PostCSS config
└── README.md               # Dokumentasi ini
```

### File Penting

- **`app/page.js`** - Komponen utama yang berisi semua logika CRUD
  - State management untuk data mahasiswa
  - Fungsi CRUD (Create, Read, Update, Delete)
  - Modal components (Detail, Edit, Create, Delete)
  - API integration dengan Strapi

## 🔌 API Endpoints

Aplikasi ini menggunakan REST API dari Strapi:

| Method | Endpoint                          | Deskripsi                |
|--------|-----------------------------------|--------------------------|
| GET    | `/api/mahasiswas`                | Ambil semua data         |
| POST   | `/api/mahasiswas`                | Tambah data baru         |
| PUT    | `/api/mahasiswas/:documentId`    | Update data              |
| DELETE | `/api/mahasiswas/:documentId`    | Hapus data               |

## 📸 Screenshot

### Dashboard dengan Tombol Tambah Data
Tampilan utama dengan tabel data mahasiswa dan tombol "Tambah Data" di header.

### Modal Tambah Data
Form input untuk menambah mahasiswa baru dengan validasi lengkap.

### Modal Edit Data
Form edit dengan data yang sudah terisi untuk mengubah informasi mahasiswa.

### Modal Konfirmasi Delete
Konfirmasi delete dengan UI yang jelas dan tombol yang mudah diklik.

### Modal Detail Mahasiswa
Tampilan detail lengkap informasi mahasiswa termasuk metadata sistem.

## 🐛 Troubleshooting

### Port 3000 sudah digunakan

```bash
# Gunakan port lain
PORT=3001 npm run dev
```

### Strapi API tidak terhubung

1. Pastikan Strapi backend berjalan di `http://localhost:1337`
2. Cek CORS settings di Strapi
3. Verifikasi collection type `mahasiswa` sudah dibuat
4. Pastikan permissions untuk public access sudah diset

### Hydration Warning

Warning hydration mismatch di development mode adalah normal dan tidak mempengaruhi fungsionalitas. Ini biasanya disebabkan oleh browser extensions atau development tools.

### Error saat build

```bash
# Hapus cache dan node_modules
rm -rf .next node_modules
npm install
npm run dev
```

## 📝 Catatan Pengembangan

- Aplikasi menggunakan **Client Components** (`'use client'`) untuk interaktivitas
- Data otomatis refresh setelah setiap operasi CRUD
- Form validation menggunakan HTML5 required attributes
- Modal menggunakan fixed positioning dengan z-index 50
- Responsive design menggunakan Tailwind breakpoints (sm, md, lg)

## 🤝 Kontribusi

Kontribusi selalu diterima! Silakan buat pull request atau buka issue untuk bug reports dan feature requests.

## 📄 Lisensi

Project ini dibuat untuk keperluan pembelajaran dan pengembangan.

---

**Dibuat dengan ❤️ menggunakan Next.js dan Strapi**
