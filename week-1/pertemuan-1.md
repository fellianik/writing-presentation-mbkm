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
- `rm <file-name>` - menghapus file
- `rm -r <folder-name>` _directory_ - menghapus directory / folder
- `rm -rf <folder-name>` _directory force_ - menghapus directory secara paksa


# Module 2 : Git & Github

GIT merupakan version control system. Git adalah aplikasi yang dapat melacak setiap perubahan yang terjadi pada suatu folder atau file.

## Instalasi Git
```bash
# Cek Instalasi
git --version
```

## Setup Awal Git
```bash
# SETUP AWAL
git config --global user.name "nama kalian"
git config --global user.email "email kalian"

# CEK SETUP
git config --list
```

:warning: email yang disetup HARUS SAMA dengan yang digunakan pada GITHUB :warning:


## Pasang Git di Project
```bash
# Jika folder sudah dibuat
git init

# Jika folder baru
git init <new-folder-name>
```
> `git init` hanya digunakan satu kali pada sebuah folder / repositori

## Melacak Perubahan
```bash
git status
```
> Perubahan = penambahan, penghapusan, pengeditan file / folder

____

## Kondisi File pada Git
![IMAGE](/week-1/assets/kondisi-file-git.jpeg)

- ### Untracked

- ### Modified
Modified adalah kondisi dimana revisi atau perubahan sudah dilakukan, tetapi belum ditandai (untracked) dan belum disimpan dalam version control.

- ### Staged
Staged adalah kondisi dimana revisi sudah ditandai (modified) namun belum disimpan di version control.

- ### Commited
Commit/committed adalah kondisi dimana revisi sudah disimpan pada version control.

____

## Menandai Perubahan
```bash
# Salah satu File
git add <file-name>

# Semua file
git add .
```

## Menambah Keterangan Perubahan dan Menyimpan Perubahan
```bash
git commit -m "...."
```

> Ketika mengalami perubahan secara terus menerus maka melakukan `git add .` dan `git commit`

## Melihat Hasil Commit
```bash
git log
# ATAU
git log --oneline
```

____
**Melihat log bisa dari berbagai sisi.**
1. Melihat log menggunakan nomor version/commit
    `git log <nomor-version||commit>`
2. Melihat log file tertentu
    `git log <file-name>`
3. Melihat log berdasarkan author
    `git log --author='...'`
____

## Mengecek Perubahan
```bash
git diff
```

## Mengembalikan keadaan perubahan
### Membatalkan Perubahan - Belum Stagged dan Belum Commited
```bash
git checkout <file-name>
```

### Membatalkan Perubahan - Sudah Stagged namun Belum Commited
> Stagged = sudah di `git add`
```bash
git reset <file-name>
```

### Membatalkan Perubahan - Sudah Commited
xxxx

____
### Case Tertentu
1. Mengembalikan commit hanya pada file tertentu 
```bash
# menggunakan git checkout
git checkout <nomor-commit file-name>

# menggunakan git reset
git reset <file-name>
```

2. Mengembalikan commit untuk semua file
```bash
git checkout <nomor-commit>
```

3. Jika ingin mengembalikan commit jauh ke bawah. Misal kita ingin kembali pada 3 commit sebelumnya
```bash
git checkout HEAD~3 <file-name>
```
____

### Git Revert
GIT Revert akan membatalkan semua perubahan yang ada tanpa menghapus commit terakhir. Jika menggunakan GIT Reset, commit terakhir akan hilang.
```bash
git revert -n <nomor-commit>
```

### Perbedaan `git checkout`, `git reset`, git revert
![Git checkout](/week-1/assets/git-checkoute.jpeg)
![Git reset](/week-1/assets/git-reset.jpeg)
![Git revert](/week-1/assets/git-revert.jpeg)

## Upload ke Github
```bash
git remote add origin <link resporitory>
git push -u origin main
```

> `git remote` dilakukan sekali