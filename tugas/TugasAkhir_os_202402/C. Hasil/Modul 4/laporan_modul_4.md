# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Modul 4 – Subsistem Kernel Alternatif (xv6-public))`

---

## 📌 Deskripsi Singkat Tugas

* **Modul 4 – Subsistem Kernel Alternatif (xv6-public)l**:
Tugas ini berfokus pada pengembangan subsistem kernel tambahan di xv6. Pertama, Anda mengimplementasikan system call baru `chmod(path, mode)` yang memungkinkan pengaturan mode file (read-only atau read-write) melalui metadata inode. Kedua, Anda membuat pseudo-device `/dev/random` yang menghasilkan data acak melalui driver sederhana, mirip dengan perangkat di sistem UNIX modern. Implementasi ini memperkenalkan konsep kontrol akses file tingkat kernel serta integrasi device driver ke dalam sistem file xv6.
---

## 🛠️ Rincian Implementasi

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

* Awalnya menambahkan `mode` ke `struct dinode` menyebabkan `mkfs` gagal (`assert (BSIZE % sizeof(dinode)) == 0`).
* Salah menulis inisialisasi `devsw[3]` menyebabkan `randomtest` gagal `cannot open /dev/random`.
* Fungsi `randomread` tidak dipanggil karena `devsw[3]` hanya diisi di `fileinit()`, padahal perlu diinisialisasi global.

---

## 📚 Referensi

* GitHub : https://github.com/Mhmmdfthn/os-NIM240202840/tree/main/Tugas%20Akhir%20/Modul%204
* ChatGPT

---
