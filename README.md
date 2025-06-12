# 📖 Panduan Membuka Port 80 & 443 di Alibaba Cloud ECS

Dokumen ini menjelaskan cara membuka akses HTTP (port 80) dan HTTPS (port 443) untuk server ECS (Elastic Compute Service) di Alibaba Cloud agar website dapat diakses dari publik.

---

## ✅ Langkah 1: Masuk ke Alibaba Cloud Console

1. Kunjungi: [https://ecs.console.aliyun.com](https://ecs.console.aliyun.com)
2. Login menggunakan akun Alibaba Cloud kamu.

---

## ✅ Langkah 2: Akses Halaman **Security Groups**

1. Di menu kiri, klik **Instances**.
2. Pilih instance server kamu (misalnya `Ubuntu`).
3. Scroll ke bawah ke bagian **Network**.
4. Klik **Security Group** yang terkait (contoh: `sg-xxxxxxxx`).

---

## ✅ Langkah 3: Tambah Aturan Inbound

1. Masuk ke tab **Inbound Rules**.
2. Klik tombol **Add Rule** atau **Add Inbound Rule**.

### Tambahkan aturan berikut:

#### 🔹 Port 80 (HTTP)
- **Protocol Type:** TCP  
- **Port Range:** 80  
- **Authorization Type:** IPv4 CIDR Block  
- **Authorization Object:** `0.0.0.0/0`  
- **Description:** Allow HTTP

#### 🔹 Port 443 (HTTPS)
- **Protocol Type:** TCP  
- **Port Range:** 443  
- **Authorization Type:** IPv4 CIDR Block  
- **Authorization Object:** `0.0.0.0/0`  
- **Description:** Allow HTTPS

---

## ✅ Langkah 4: Simpan dan Coba Akses

Tunggu 10–30 detik agar perubahan aktif, lalu coba akses:

```
http://<IP_ECS_KAMU>
```

Contoh:
```
http://47.236.185.249
```

---

## 🛠️ Tips Tambahan

- Gunakan perintah `curl` di VPS untuk tes internal:
  ```bash
  curl http://localhost
  ```
- Pastikan Apache atau Nginx kamu berjalan:
  ```bash
  sudo systemctl status apache2
  ```
- 💡 Pastikan port juga tidak diblok oleh firewall internal (seperti ufw, jika digunakan).

---
