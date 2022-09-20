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
- `pwd` _print working directory_ - melihat nama directory sekarang 
- `ls` _lists_ - melihat isi directory
- `ls -al` - melihat isi directory beserta hidden files
- `cd <directory>` _change directory_ - untuk pindah directory

```bash
# Contoh Penggunaan
# Berpindah ke folder folder-name
cd folder-name

# Kembali ke directory sebelumnya
cd .. 
```

### Membuat File & Directory
- `touch <file-name.file-format>` - membuat sebuah file
- `mkdir <folder-name>` - membuat sebuah directory / folder

### Melihat Isi File
- `head <file-name>` - melihat beberapa line awal dari isi file (default = 10 baris pertama)
- `tail <file-name>` - melihat beberapa line akhir dari isi file (default = 10 baris terakhir)
- `cat <file-name> - melihat isi file (secara keseluruhan)

<aside>
`head -(jumlah baris yang mau ditampilkan) <namafile>` 
contoh : `head -9 nama-file` - akan menampilkan 9 baris pertama.
</aside>