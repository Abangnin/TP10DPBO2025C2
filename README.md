# Bismillahirrahmanirrahim

## Janji
Saya Muhammad Naufal Arbanin dengan NIM 2310850 mengerjakan soal Tugas Praktikum 10 dalam mata kuliah Desain Pemrograman Berorientasi Objek untuk keberkahanNya maka saya tidak melakukan kecurangan seperti yang telah dispesifikasikan. Aamiin.

## Desain Database
![Image](https://github.com/user-attachments/assets/3fb13d3d-aafa-4c0e-90d3-997e96dd9258)

## Penjelasan Alur 
### 1. Tambah Kebun (Create)
#### Alur:
- User buka halaman index.php?entity=kebun&action=add → menampilkan form tambah kebun (views/kebun/form.php).

- User mengisi Nama Kebun, Lokasi, dan Luas (ha).

- Klik tombol "Save" → form dikirim ke index.php?entity=kebun&action=save (via method="post").

- File index.php memanggil KebunViewModel->addKebun(), yang mengakses model Kebun->create() dan menyimpan ke database (table kebun).

- Setelah sukses, halaman redirect ke index.php?entity=kebun&action=list.

### 2. Tampilkan Daftar Kebun (Read)
#### Alur:
- Halaman index.php?entity=kebun&action=list ditampilkan.

- KebunViewModel->getKebunList() dipanggil, yang menggunakan Kebun->getAll() untuk mengambil semua data dari tabel kebun.

- Data ditampilkan dalam tabel (views/kebun/list.php) dengan kolom:

- Nama Kebun, Lokasi, Luas, Actions (Edit/Delete)

- Setiap baris menyediakan tombol Edit dan Delete.

### 3. Edit Kebun (Update)
#### Alur:
- Di halaman list kebun, user klik tombol Edit pada salah satu baris.

- Link diarahkan ke index.php?entity=kebun&action=edit&id=X.

- File index.php memanggil KebunViewModel->getKebunById($id) → mengambil data berdasarkan id_kebun.

- Data ditampilkan dalam form edit (views/kebun/form.php) dengan value sudah terisi.

- Setelah user ubah dan klik Save, data dikirim ke index.php?entity=kebun&action=update&id=X (POST).

- Data diproses melalui KebunViewModel->updateKebun() → Kebun->update().

- Redirect kembali ke list kebun.

### 4. Hapus Kebun (Delete)
#### Alur:
- Di list kebun, user klik tombol Delete.

- Link menuju: index.php?entity=kebun&action=delete&id=X.

- Konfirmasi : confirm('Yakin ingin menghapus?').

- Jika ya, KebunViewModel->deleteKebun($id) dipanggil → menghapus dari DB melalui Kebun->delete($id).

- Redirect ke list kebun.

### 5. Tambah Tanaman (Create)
#### Alur:
- User buka: index.php?entity=tanaman&action=add.

- Form views/tanaman/form.php menampilkan input:

- Nama Tanaman, Jenis, Pilih Kebun (dropdown).

- Klik "Save" → data dikirim ke index.php?entity=tanaman&action=save.

- Data disimpan melalui TanamanViewModel->addTanaman() → Tanaman->create().

- Redirect ke list tanaman.

### 6. Tampilkan Tanaman (Read)
- Halaman: index.php?entity=tanaman&action=list.

- TanamanViewModel->getTanamanList() → Tanaman->getAll() (JOIN ke kebun).

- View views/tanaman/list.php menampilkan kolom:

- Nama Tanaman, Jenis, Nama Kebun, Actions (Edit/Delete).

### 7. Tambah Panen (Create)
#### Alur:
- User buka: index.php?entity=panen&action=add.

- Form views/panen/form.php:

- Tanggal Panen, Jumlah (kg), Kualitas, Pilih Tanaman.

- Klik "Save" → data ke index.php?entity=panen&action=save.

- Diproses PanenViewModel->addPanen() → Panen->create().

- Redirect ke index.php?entity=panen.

### 8. Tampilkan Panen (Read)
#### Alur:
- Buka index.php?entity=panen&action=list.

- PanenViewModel->getPanenList() → Panen->getAll() (JOIN tanaman).

- View views/panen/list.php tampilkan:

- Nama Tanaman, Tanggal, Jumlah, Kualitas, Actions (Edit/Delete).

### 9. Edit & Delete untuk Tanaman & Panen
- Prosesnya sama persis dengan kebun:

- Tombol Edit mengarah ke ?action=edit&id=..., form akan terisi otomatis.

- Tombol Delete mengarah ke ?action=delete&id=..., konfirmasi sebelum hapus.

## Video Dokumentasi
https://github.com/user-attachments/assets/f2e76d32-c82d-42ab-987f-702fc30b6565
