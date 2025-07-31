# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Contoh: Modul 1 – System Call dan Instrumentasi Kernel)`

---

## 📌 Deskripsi Singkat Tugas
* **Modul 1 – System Call dan Instrumentasi Kernel**:
Tugas ini bertujuan untuk memahami dan memodifikasi kernel xv6 dengan cara menambahkan dua system call baru. System call pertama, `getpinfo()`, digunakan untuk mengambil informasi semua proses aktif dalam sistem (PID, ukuran memori, dan nama). System call kedua, `getreadcount()`, digunakan untuk memantau jumlah total pemanggilan fungsi `read()` sejak sistem dinyalakan. Selain implementasi pada level kernel, tugas ini juga mencakup pembuatan program user-level `(ptest.c dan rtest.c)` untuk menguji fungsionalitas kedua system call tersebut.
---

## 🛠️ Rincian Implementasi
### Contoh untuk Modul 1:

* Tambahkan Struktur `pinfo` dan Counter `readcount` di `proc.h`dan di `sysproc.c` `(global)`
* Tambahkan Nomor System Call Baru di `syscall.h` (paling bawah)
* Registrasikan syscall di `syscall.c` dan Tambah ke array syscall
* Tambahkan ke User-Level di `user.h` dan di `usys.S`
* Implementasi Fungsi Kernel di `sysproc.c`
* Modifikasi `read()` untuk Tambah Counter di `sysfile.c, fungsi `sys_read()`
* Buat Program Penguji User-Level File: `ptest.c` (untuk `getpinfo`) dan File: `rtest.c` (untuk `getreadcount`) lalu daftarkan ke `makefile`
* Build dan Jalankan

---

## ✅ Uji Fungsionalitas
* `ptest`: untuk menguji `getpinfo()`
* `rtest`: untuk menguji `getReadCount()`
---

## 📷 Hasil Uji
### 📍 Hasil Output Ptest :

```
$ ptest
PID	MEM	NAME
1	12288	init
2	16384	sh
3	12288	ptest
```

### 📍 Hasil Output rtest :
```
$ rtest
Read Count Sebelum: 12
hello
Read Count Setelah: 13
```

## ⚠️ Kendala yang Dihadapi

Tuliskan kendala (jika ada), misalnya:

* salah memposisi Implementasi Fungsi Kernel `sysproc.c`

---

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---
