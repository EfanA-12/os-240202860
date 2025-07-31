# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Modul 3)`

---

## 📌 Deskripsi Singkat Tugas
* **Modul 3 – Manajemen Memori Tingkat Lanjut (xv6-public x86)l**:
Tugas ini bertujuan untuk mengembangkan sistem manajemen memori pada xv6 dengan dua fitur utama: Copy-on-Write (CoW) Fork dan Shared Memory. CoW mengoptimalkan fungsi `fork()` dengan membagi halaman memori secara read-only antar proses anak dan induk, lalu menyalin hanya saat ada penulisan (page fault). Shared memory memungkinkan proses berbagi halaman memori secara eksplisit menggunakan syscall `shmget()` dan `shmrelease()`, lengkap dengan reference count. Kedua fitur ini menuntut pemahaman mendalam tentang page table, page fault handling, dan kontrol akses memori antar proses.
---

## 🛠️ Rincian Implementasi
### Contoh untuk Modul 1:

* A. Implementasi Copy-on-Write Fork (CoW)
* Tambah `ref_count[]` dan fungsi `incref/decref` di `vm.c`, bagian global
* Tambahkan `PTE_COW` di `mmu.h`
* Modifikasi `copyuvm()` → `cowuvm()` di `vm.c`
* Ubah `fork()` di `proc.c`, Cari `np->pgdir = copyuvm(...)` → ganti
* Tangani Page Fault `T_PGFLT` di `trap.c` di dalam `trap()`
* Program Uji `cowtest.c`
* Output: Child sees: Y dan Parent sees: X
* B. Implementasi Shared Memory ala System V
* Tambah Struktur di `vm.c`
* Implementasi `shmget()` di `sysproc.c`
* Implementasi `shmrelease()` di `sysproc.c`
* Registrasi syscall Di `syscall.h`, di `user.h`, di `usys.S` dan di `syscall.c`
* Program Uji `shmtest.c`
* Output: Child reads: A dan Parent reads: B
---

## ✅ Uji Fungsionalitas

* `cowtest`: untuk menguji fork dengan Copy-on-Write
* `shmtest`: untuk menguji `shmget()` dan `shmrelease()`
---

## 📷 Hasil Uji

Lampirkan hasil uji berupa screenshot atau output terminal. Contoh:

### 📍 Hasil Output `cowtest`:

```
$cowtest
child sees: Y
parent sees: X
```

### 📍 Contoh Output `shmtest`:

```
Child reads: A
Parent reads: B
```


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
