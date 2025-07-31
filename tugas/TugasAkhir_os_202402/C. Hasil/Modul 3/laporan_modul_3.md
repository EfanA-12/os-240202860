# 📝 Laporan Tugas Akhir

**Mata Kuliah**: Sistem Operasi
**Semester**: Genap / Tahun Ajaran 2024–2025
**Nama**: `<Efan Aryanto Adli>`
**NIM**: `<240202860>`
**Modul yang Dikerjakan**:
`(Modul 3-Manajemen Memori Tingkat Lanjut (xv6-public x86))`

---

## 📌 Deskripsi Singkat Tugas
* **Modul 3 – Manajemen Memori Tingkat Lanjut (xv6-public x86)l**:
Tugas ini bertujuan untuk mengembangkan sistem manajemen memori pada xv6 dengan dua fitur utama: Copy-on-Write (CoW) Fork dan Shared Memory. CoW mengoptimalkan fungsi `fork()` dengan membagi halaman memori secara read-only antar proses anak dan induk, lalu menyalin hanya saat ada penulisan (page fault). Shared memory memungkinkan proses berbagi halaman memori secara eksplisit menggunakan syscall `shmget()` dan `shmrelease()`, lengkap dengan reference count. Kedua fitur ini menuntut pemahaman mendalam tentang page table, page fault handling, dan kontrol akses memori antar proses.
---

## 🛠️ Rincian Implementasi

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

1. **Variabel tidak terdeklarasi saat menangani page fault** – variabel `r` tidak dikenali karena tidak dideklarasikan di awal fungsi `trap()`; solusinya dengan menambahkan `struct trapframe *r = myproc()->tf;`.
2. **Error redeklarasi fungsi atau variabel global** – terjadi ketika `shmtab[]` atau fungsi `walkpgdir()` dan `mappages()` dideklarasikan ulang di `vm.c` secara `static`, padahal sudah ada deklarasi di `defs.h`.
3. **Fork gagal karena implementasi `cowuvm()` tidak memetakan semua halaman dengan benar** – menyebabkan child process crash.


## 📚 Referensi

* CahtGPT
* GitHub : https://github.com/Mhmmdfthn/os-NIM240202840/tree/main/Tugas%20Akhir%20/Modul%203

---
