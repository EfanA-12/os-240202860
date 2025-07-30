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
  a. Tambah nomor `syscall` di `syscall.h`
  b. Tambah deklarasi di `user.h`
  c. Tambah entri di `usys.S`
  d. Registrasikan syscall di `syscall.c` : Tambahkan deklarasi fungsi dan Tambahkan        ke array `syscalls[]`
  e. Implementasi di `sysproc.c`
* Modifikasi Fungsi scheduler() di `proc.c`
* Buat Program Pengujian: `ptest.c`
* Tambahkan `ptest` ke Makefile
* Jalankan dan Uji
---

## ✅ Uji Fungsionalitas

Tuliskan program uji apa saja yang Anda gunakan, misalnya:

* `ptest`: untuk menguji `getpinfo()`
* `rtest`: untuk menguji `getReadCount()`
* `cowtest`: untuk menguji fork dengan Copy-on-Write
* `shmtest`: untuk menguji `shmget()` dan `shmrelease()`
* `chmodtest`: untuk memastikan file `read-only` tidak bisa ditulis
* `audit`: untuk melihat isi log system call (jika dijalankan oleh PID 1)

---

## 📷 Hasil Uji

Lampirkan hasil uji berupa screenshot atau output terminal. Contoh:

### 📍 Contoh Output `cowtest`:

```
Child sees: Y
Parent sees: X
```

### 📍 Contoh Output `shmtest`:

```
Child reads: A
Parent reads: B
```

### 📍 Contoh Output `chmodtest`:

```
Write blocked as expected
```

Jika ada screenshot:

```
![hasil cowtest](./screenshots/cowtest_output.png)
```

---

## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* Salah implementasi `page fault` menyebabkan panic
* Salah memetakan alamat shared memory ke USERTOP
* Proses biasa bisa akses audit log (belum ada validasi PID)

---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---
