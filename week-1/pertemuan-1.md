# Module 1: Unix Command Line

> [Cheat sheet Unix command line](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)

## Command Line Interface
- **Shell** adalah program yang digunakan untuk berkomunikasi atau memerintah sistem
- **Command Line Interface** adalah jenis shell yang berbasis teks
- **Terminal Emulator** adalah aplikasi untuk mengakses CLI

## File System
- Mengatur bagaimana data disimpan di dalam sebuah system
- Window dan unix-like menyusun file dan direktori menggunakan struktur yang bentuknya mirip tree

## Command
### Navigasi
_print working directory_ 
- `pwd`- melihat nama directory sekarang 

_lists_
- `ls` - melihat isi directory
- `ls -al` - melihat isi directory beserta hidden files

_change directory_
- `cd <directory>` - untuk pindah directory

```bash
# Contoh Penggunaan
# Berpindah ke folder folder-name
cd folder-name

# Kembali ke directory sebelumnya
cd .. 

# Ke Home Directory
cd ~
```

### Membuat File & Directory
- `touch <file-name.file-format>` - membuat sebuah file
- `mkdir <folder-name>` - membuat sebuah directory / folder

### Membuka File
- `nano <file-name>` - membuka file di CLI
- `<app-name> <file-name>` - membuka file dengan aplikasi yang ditentukan

### Menulis Text di Dalam File Menggunakan CLI
- `echo "....." > <file-name>` - menuliskan text di CLI dan disimpan ke dalam file 

### Melihat Isi File
- `head <file-name>` - melihat beberapa line awal dari isi file (default = 10 baris pertama)
- `tail <file-name>` - melihat beberapa line akhir dari isi file (default = 10 baris terakhir)
- `cat <file-name>` - melihat isi file (secara keseluruhan)
- `head || tail -n <file-name>` - menampilkan isi file dengan baris yang muncul yaitu n baris 

```bash
# Contoh Penggunaan
# Akan menampilkan 9 baris pertama
head -9 file-name
```

### Menyalin, Memindahkan, dan Menghapus files & directory
_copy_ 
- `cp <source_file> <destination_file>` - menyalin file ke directory yang berbeda
- `cp <file-name> <copy-file-name>` - menyalin file di directory yang sama
- `cp -r <folder-name>` _directory_- menyalin directory / folder

_move_
- `mv <old-file-name> <new-file-name>` - mengubah nama file dan file berada di directory yang tetap
- `mv <nama-file-yang-dipindah> <tujuan-pindah/nama-file(bisa_baru||lama)>` - memindahkan file ke directory lain sekaligus mengubah nama
- `mv -r <folder-name>` directory_- memindahkan directory / folder

_remove_
- `rm <file-name>` _remove_ - menghapus file
- `rm -r <folder-name>` _directory_ - menghapus directory / folder
- `rm -rf <folder-name>` _directory force_ - menghapus directory secara paksa