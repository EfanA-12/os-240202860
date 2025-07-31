# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Contoh: Modul 4 – Subsistem Kernel Alternatif (xv6-public))`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 1 – System Call dan Instrumentasi Kernel**:
Tugas ini berfokus pada pengembangan subsistem kernel tambahan di xv6. Pertama, Anda mengimplementasikan system call baru `chmod(path, mode)` yang memungkinkan pengaturan mode file (read-only atau read-write) melalui metadata inode. Kedua, Anda membuat pseudo-device `/dev/random` yang menghasilkan data acak melalui driver sederhana, mirip dengan perangkat di sistem UNIX modern. Implementasi ini memperkenalkan konsep kontrol akses file tingkat kernel serta integrasi device driver ke dalam sistem file xv6.
---

## 🛠️ Rincian Implementasi

### Contoh untuk Modul 1:

* Bagian A – System Call `chmod()`
* Tambahkan Field `mode` ke `struct` inode, File: `fs.h`, cari `struct inode`
* Tambahkan syscall `chmod()`:
* a. `syscall.h` – Tambahkan nomor syscall baru
* b. `user.h` – Tambahkan deklarasi
* c. `usys.S` – Tambahkan syscall
* d. `syscall.c` – Daftarkan syscall
* e. `sysfile.c` – Tambahkan fungsi `sys_chmod`
* Cegah `write()` jika mode `read-only`, File: `file.c`, fungsi `filewrite()`
* Program Uji `chmodtest.c`
* Bagian B – Device Pseudo `/dev/random`
* Buat File Baru `random.c`
* Registrasi Device Driver, File: `file.c`
* Tambahkan Device Node `/dev/random`
* Program Uji `randomtest.c`
---

## ✅ Uji Fungsionalitas

* `randomtest` : Untuk menguji pseudo-device /dev/random yang telah ditambahkan ke xv6.
* `chmodtest`: untuk memastikan file `read-only` tidak bisa ditulis


---

## 📷 Hasil Uji

### 📍 Hasil Output `randomtest`:

```
96 211 202 245 68 231 78 41
```

### 📍 Hasil Output `chmodtest`:

```
Write blocked as expected
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
