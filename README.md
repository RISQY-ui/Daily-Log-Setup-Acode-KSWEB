# Rangkuman-Hari-ke-17-Setup-Acode-KSWEB-untuk-PHP-di-HP

# 📝 Rangkuman Hari ke-17: Setup Acode + KSWEB

## Selasa, 17 Juni 2026

---

## 🎯 Tujuan Hari Ini

Menghubungkan **Acode** (editor kode di HP) dengan **KSWEB** (server lokal di HP) agar Faris bisa edit file PHP langsung dari HP.

---

## 🚀 Langkah-Langkah Setup

### 1. Buka Acode
Buka aplikasi Acode di HP Faris.

### 2. Buka Menu Folder
Klik ikon **folder** atau **tiga garis** di pojok kiri atas.

### 3. Tambah Path / Folder
Pilih **"Add Path"** atau **"Open Folder"**, lalu klik **"Select Folder"** (atau ikon `+`).

### 4. Cari Folder `htdocs`
Cari folder dengan alamat:

```

/storage/emulated/0/htdocs

```

> ℹ️ **Catatan:** Di file manager HP, folder ini biasanya ada di **penyimpanan internal paling luar** (bukan di dalam folder Documents atau Download).

### 5. Pilih & Izinkan
- Klik **"Use this folder"** (Gunakan folder ini)
- Klik **"Allow"** (Izinkan)

---

## ❓ Kenapa Harus ke Folder `htdocs`?

| Alasan | Keterangan |
|--------|-------------|
| **KSWEB (Apache)** | Hanya mau baca file yang ada di dalam folder `htdocs` |
| **Akses Localhost** | Kalau file PHP disimpan di `htdocs`, nanti bisa diakses lewat `localhost:8000` |
| **Aman & Rapi** | Semua file web terkumpul di satu tempat |

---

## ✅ Langkah Selanjutnya

Setelah folder `htdocs` berhasil ditambahkan ke Acode:

| No | Langkah | Keterangan |
|----|---------|-------------|
| 1 | Klik folder `htdocs` di Acode | Buka folder tersebut |
| 2 | Pilih **"New File"** | Buat file baru |
| 3 | Kasih nama `vuln.php` | File PHP pertama di HP |

---

## 📊 Status Hari Ini

| Komponen | Status |
|----------|--------|
| Acode Terinstall | ✅ |
| KSWEB Terinstall | ✅ |
| Folder `htdocs` ditemukan | ✅ |
| Acode terhubung ke `htdocs` | ✅ |
| File `vuln.php` dibuat | 🔄 Belum |

---

 
