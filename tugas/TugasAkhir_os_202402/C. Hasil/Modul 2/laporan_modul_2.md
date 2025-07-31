# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Modul 2 – Penjadwalan CPU Lanjutan (Priority Scheduling Non-Preemptive)
l)`

---

## 📌 Deskripsi Singkat Tugas

Tuliskan deskripsi singkat dari modul yang Anda kerjakan. Misalnya:

* **Modul 2 – Penjadwalan CPU Lanjutan (Priority Scheduling Non-Preemptive)**:
Tugas ini bertujuan untuk mengubah algoritma penjadwalan proses di xv6 dari Round Robin menjadi Non-Preemptive Priority Scheduling. Mahasiswa diminta menambahkan field `priority` pada setiap proses, mengimplementasikan syscall `set_priority(int)` untuk mengatur prioritas, serta memodifikasi fungsi `scheduler()` agar selalu menjalankan proses `RUNNABLE` dengan prioritas tertinggi. Hasil implementasi diuji menggunakan program `ptest.c` untuk memastikan proses dengan prioritas lebih tinggi dijalankan terlebih dahulu.
---

## 🛠️ Rincian Implementasi
* Tambahkan `priority` ke `struct proc` di `proc.h`
* Inisialisasi `priority` saat alokasi proses di `proc.c`
* Buat syscall `set_priority(int)`
* a. Tambah nomor `syscall` di `syscall.h`
* b. Tambah deklarasi di `user.h`
* c. Tambah entri di `usys.S`
* d. Registrasikan syscall di `syscall.c` : Tambahkan deklarasi fungsi dan Tambahkan       ke array `syscalls[]`
* e. Implementasi di `sysproc.c`
* Modifikasi Fungsi scheduler() di `proc.c`
* Buat Program Pengujian: `ptest.c`
* Tambahkan `ptest` ke Makefile
* Jalankan dan Uji
---

## ✅ Uji Fungsionalitas

Tuliskan program uji apa saja yang Anda gunakan, misalnya:

* `ptest`: untuk menguji `getpinfo()`

---

## 📷 Hasil Uji

### 📍 Hasil Output ptest :

```
Booting From Hard Disk..xv6...
cpu1: starting 1
cpu0: starting 0
sb: size 1000 nblocks 941 ninodes 200 nlog 30 logstart 2 inodes8
$ ptest
Child 1 selesai  
Child 2 selesai
parent selesai
$
  
```

## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* Bingung dalam menaruh perintahnya
* Adanya tambahan code yang tidak ada di modul

---

## 📚 Referensi

* ChatGPT

---
