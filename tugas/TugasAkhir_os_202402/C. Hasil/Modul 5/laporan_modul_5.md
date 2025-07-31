# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Contoh: Modul 5 – Audit dan Keamanan Sistem (xv6-public))`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 5 – Audit dan Keamanan Sistem (xv6-public)**:
Tugas ini berfokus pada penguatan aspek keamanan sistem melalui fitur audit log di kernel xv6. Setiap pemanggilan system call akan direkam ke dalam struktur log internal, mencatat informasi seperti PID pemanggil, nomor syscall, dan waktu `(tick)`. Selain itu, ditambahkan system call baru `get_audit_log()` untuk membaca isi log, namun aksesnya dibatasi hanya untuk proses dengan PID 1 (init) demi menjaga keamanan. Tugas ini memperkenalkan konsep logging di level kernel, validasi akses, dan perlindungan data kernel dari proses user.
---

## 🛠️ Rincian Implementasi

* Tambahkan Struktur Audit Log, di `syscall.c` (bagian global paling atas)
* Catat System Call di `syscall()`,Di fungsi syscall() `(syscall.c)`, setelah
* Tambahkan System Call `get_audit_log()`
* a. `syscall.h` – Tambahkan nomor syscall baru
* b. `user.h` – Tambahkan deklarasi
* c. `usys.S` – Tambahkan syscall
* d. `sysproc.c` – Implementasi syscall
* Program Uji: `audit.c`
* Tambahkan ke Makefile
* Build dan Jalankan:
* make clean
* make qemu-nox
* $ audit
* Access denied or error.
* a. Edit `init.c`
---

## ✅ Uji Fungsionalitas

* `audit`: untuk melihat isi log system call (jika dijalankan oleh PID 1)

---

## 📷 Hasil Uji

### 📍 Hasil Output `audit`:

```
$audit
=== Audit Log ===
[0] PID=1 SYCALL=7 TICK=1
[1] PID=1 SYCALL=7 TICK=2
[2] PID=1 SYCALL=7 TICK=2
[3] PID=1 SYCALL=7 TICK=3
```

## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* GitHub : https://github.com/Mhmmdfthn/os-NIM240202840/tree/main/Tugas%20Akhir%20/Modul%205
* ChatGPT

---
