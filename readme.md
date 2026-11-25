# 🎥 OverlayKu — Custom Stream Overlays

Koleksi custom overlay berbasis HTML/CSS/JS untuk kebutuhan livestreaming di **OBS Studio** dan **TikTok LIVE Studio**, dilengkapi dengan Homepage Dashboard untuk preview dan copy URL dengan cepat.

🌐 **Live Dashboard:** `https://overlayku.vercel.app`

## 📁 Struktur Folder

File `index.html` di root berfungsi sebagai Homepage Dashboard, sedangkan setiap tema overlay disimpan terpisah di dalam folder `themes/`:

```text
overlayku/
├── index.html                        # Homepage Dashboard (Preview & Copy URL)
├── README.md
└── themes/
    ├── anime-minimalist/             # Tema 1: Anime Minimalist (Ivory, Emerald, Gold)
    │   ├── running-text.html         # Running text frame
    │   ├── webcam.html               # Frame webcam
    │   ├── chatbox.html              # Frame chat box
    │   ├── topbar.html               # Socials / info bar
    │   ├── starting.html             # Layar Starting Soon / BRB
    │   ├── alertbox.html             # Template alert donasi
    │   └── tiktok-alerts.html        # Template alert follow, share, & like
    └── nama-tema-baru/               # Folder untuk tema-tema baru ke depannya
        └── ...
```

## 📐 Rekomendasi Ukuran (Canvas & Overlay)

### 1. Resolusi Canvas Stream

* **Landscape (16:9):** `1920 x 1080` px (OBS / TikTok LIVE Studio Landscape)
* **Portrait (9:16):** `1080 x 1920` px (TikTok LIVE Studio Vertikal — cukup *scale/resize* lebar overlay menyesuaikan layar)

### 2. Daftar Overlay & Ukuran Rekomendasi (`anime-minimalist`)

Gunakan ukuran (*Width x Height*) berikut saat menambahkan **Browser Source** (OBS) atau **Link** (TikTok LIVE Studio):

| Nama Overlay | Path URL | Ukuran Overlay (px) | Ukuran Widget Pasangan (px) | Posisi Layer |
| :--- | :--- | :--- | :--- | :--- |
| **Running Text Frame** | `/themes/anime-minimalist/running-text.html` | `1200 x 80` | SociaBuzz: `940 x 60` | Frame di bawah, teks di atas |
| **Webcam Frame** | `/themes/anime-minimalist/webcam.html` | `640 x 380` | Kamera (16:9): `610 x 345` | Frame di atas kamera |
| **Chat Box Frame** | `/themes/anime-minimalist/chatbox.html` | `420 x 560` | Widget Chat: `380 x 450` | Frame di bawah widget chat |
| **Top Info / Socials** | `/themes/anime-minimalist/topbar.html` | `900 x 64` | — | Bebas (atas tengah layar) |
| **Starting / BRB Screen** | `/themes/anime-minimalist/starting.html` | `1920 x 1080` | — | Fullscreen (scene terpisah) |
| **Alert Box (Donasi)** | `/themes/anime-minimalist/alertbox.html` | `640 x 240` | — | Paling atas (tengah/atas layar) |
| **TikTok Alerts** | `/themes/anime-minimalist/tiktok-alerts.html` | `460 x 110` | — | Pojok kiri/kanan layar |

> **Tips:** Untuk `tiktok-alerts.html`, tambahkan parameter `?type=follow`, `?type=share`, atau `?type=like` di belakang URL jika ingin memanggil satu jenis alert saja.

## 🚀 Cara Pemakaian

### Di TikTok LIVE Studio

1. Buka `https://overlayku.vercel.app` di browser, lalu klik tombol **Copy URL** pada overlay yang diinginkan.
2. Di TikTok LIVE Studio, klik **Add Source** > pilih **Link**.
3. Paste URL yang sudah disalin, lalu isi **Width** dan **Height** sesuai kolom **Ukuran Overlay** pada tabel di atas.
4. Atur urutan layer sesuai kolom **Posisi Layer**.

### Di OBS Studio

* Gunakan link Vercel di atas melalui **Sources > Browser**, atau centang **Local File** jika ingin langsung memanggil file HTML dari komputer.
* Untuk overlay yang berpasangan (misal *Frame Running Text* + *SociaBuzz*), blok kedua source lalu klik kanan > **Group Selected Items** agar mudah digeser bersamaan.

## 🛠️ Cara Update & Menambah Tema Baru

Repository ini terhubung langsung dengan **Vercel** (auto-deploy).

1. Buat folder tema baru di dalam `themes/` (misalnya `themes/cyberpunk/`).
2. Daftarkan tema dan file baru tersebut ke dalam array `THEMES` di file `index.html` agar muncul di Homepage Dashboard.
3. Push perubahan ke GitHub:

   ```bash
   git add .
   git commit -m "add: tema overlay baru"
   git push origin main
   ```

4. Vercel akan otomatis memperbarui `https://overlayku.vercel.app` dalam beberapa detik.