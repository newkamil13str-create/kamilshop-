# KamilShop — Marketplace Digital

Marketplace digital lengkap dengan auto delivery, payment gateway Pakasir, bot Telegram, dan admin panel.

## 🚀 Tech Stack
- **Frontend**: Next.js 14 (App Router) + TypeScript + Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: Firebase Firestore + Firebase Auth
- **Payment**: Pakasir
- **Bot**: Telegraf.js (Telegram)
- **Email**: Nodemailer (Gmail SMTP)

## ⚡ Cara Setup

### 1. Clone & Install
```bash
git clone <repo>
cd kamilshop
npm install
```

### 2. Setup Firebase
1. Buat project di [Firebase Console](https://console.firebase.google.com)
2. Aktifkan **Authentication** (Email/Password)
3. Aktifkan **Firestore Database**
4. Buat **Service Account** → download JSON key
5. Isi data di `.env.local`

### 3. Setup Environment Variables
```bash
cp .env.local.example .env.local
```
Isi semua nilai di `.env.local` sesuai akun Anda.

### 4. Set Admin User
Setelah daftar akun pertama, buka Firebase Console → Firestore → `users/{uid}` → ubah `role` menjadi `"admin"`

### 5. Install tailwindcss-animate
```bash
npm install tailwindcss-animate
```

### 6. Jalankan Development
```bash
npm run dev
```

### 7. Jalankan Bot Telegram (opsional, terpisah)
```bash
npm run bot
# atau
node bot/index.js
```

## 📁 Struktur Folder
```
kamilshop/
├── app/
│   ├── (public pages)
│   ├── admin/           # Admin panel
│   ├── api/             # API Routes
│   └── globals.css
├── bot/
│   └── index.js         # Telegram bot
├── components/
│   ├── admin/
│   └── layout/
├── lib/                 # Firebase, email, telegram, utils
├── types/               # TypeScript types
└── middleware.ts
```

## 🔧 Konfigurasi Webhook Pakasir
Set webhook URL di dashboard Pakasir ke:
```
https://kamilshop.my.id/api/webhook/pakasir
```

## 🤖 Perintah Bot Telegram
```
/start       — Daftar perintah
/stats       — Statistik toko
/orders      — 10 order terbaru
/pending     — Order pending
/deliver [id] [konten] — Manual deliver
/cancelorder [id]      — Cancel order
/users       — Info user
/user [id]   — Detail user
/banuser [id] / /unbanuser [id]
/products    — List produk
/toggleproduct [id]
/updatestock [id] [jumlah]
/topproducts — 5 terlaris
```

## 🌐 Deploy ke Vercel
```bash
npm install -g vercel
vercel --prod
```
Tambahkan semua env vars di Vercel Dashboard → Settings → Environment Variables.

## 📝 Catatan Penting
- Bot Telegram hanya merespons dari `TELEGRAM_OWNER_CHAT_ID`
- OTP berlaku 5 menit, max 3x per 10 menit per email
- Auto delivery berjalan otomatis via Pakasir webhook
- Admin panel: `kamilshop.my.id/admin`
