# Panduan Kolaborasi Git Workflow

Panduan ini dibuat agar semua anggota tim memiliki alur kerja yang seragam, aman, dan rapi saat berkolaborasi di repository ini.

---

## Struktur Branch

| Branch | Deskripsi |
|--------|------------|
| `main` | Branch utama (production). Tidak boleh diubah langsung. |
| `dev` | Branch pengembangan utama. Semua fitur baru merge ke sini. |
| `feature/*` | Branch turunan untuk masing-masing fitur. Contoh: `feature/login-page`, `feature/dashboard-api`. |

---

## Alur Kerja Developer

### 1.Clone repository
```bash
git clone https://github.com/bebeksalju/ArekArekERP.git
cd ArekArekERP
```

### 2.Pindah ke branch dev
```bash
git checkout dev
```

### 3.Buat branch baru untuk fitur
```bash
git checkout -b feature/nama-fitur
```

### 4.Lakukan perubahan dan commit
```bash
git add .
git commit -m "feat: tambahkan halaman login"
```

### 5.Push branch ke GitHub
```bash
git push origin feature/nama-fitur
```

### 6.Buat Pull Request (PR)
- Buka repo di GitHub.
- Klik **“Compare & Pull Request”**.
- Target merge ke branch `dev`.
- Tambahkan deskripsi singkat perubahanmu.
- Klik **“Create Pull Request”**.

### 7.Review & Approval
- Minimal **1 approval** sebelum merge.
- Reviewer memastikan code sesuai standar.
- Setelah disetujui, PR di-merge ke `dev`.
- Merge ke `main` hanya oleh maintainer setelah testing final.

---

## Branch Protection Rules (yang berlaku di repo ini)

- Tidak bisa langsung push ke `main` dan `dev`.
- Semua perubahan harus lewat **Pull Request (PR)**.
- Minimal **1 approval review** sebelum merge.
- **Status check** (build/test) harus lulus.
- **Code Owner Review** wajib untuk file tertentu.
- Semua **conversation** di PR harus diselesaikan.
- Approval otomatis dibatalkan jika ada commit baru di PR.

---

## Tips Kolaborasi

- Gunakan pesan commit yang singkat dan bermakna.
- Hindari commit langsung di `main` atau `dev`.
- Selalu update branch `dev` lokal:
  ```bash
  git checkout dev
  git pull origin dev
  ```
- Jika branch feature tertinggal dari dev:
  ```bash
  git checkout feature/nama-fitur
  git pull origin dev
  git merge dev
  ```

---

## Alur Lengkap

```bash
# 1. Checkout ke dev
git checkout dev

# 2. Buat branch baru untuk fitur
git checkout -b feature/login-page

# 3. Coding dan commit
git add .
git commit -m "feat: tambah halaman login"

# 4. Push ke repo
git push origin feature/login-page

# 5. Buat Pull Request (target: dev)
# 6. Tunggu review dan approval
# 7. Merge ke dev (oleh reviewer)
```

---

## Inti Utama
> Semua kerja dilakukan di branch `feature/*`,  
> di-review dulu lewat Pull Request,  
> baru bisa masuk ke `dev`, dan  
> `main` hanya di-update setelah testing & approval final.

---

**Team Collaboration Workflow**
> Dengan mengikuti aturan ini, kita bisa menjaga kualitas kode, mencegah konflik, dan mempercepat proses pengembangan bersama.
