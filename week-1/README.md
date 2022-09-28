# Minggu 1 - 19 - 23 September 2022

---

# Module 1 - UNIX Command Line

### Command Line Interface

-   **Shell** adalah program yang digunakan untuk berkomunikasi atau memerintah sistem
-   **Command Line Interface** adalah jenis shell yang berbasis teks
-   **Terminal Emulator** adalah aplikasi untuk mengakses CLI

### Contoh CLI

-   sh
-   bash
-   zsh
-   cmd.exe

### File System

-   Mengatur bagaimana data disimpan di dalam sebuah system
-   Window dan unix-like menyusun file dan direktori menggunakan struktur yang bentuknya mirip tree

### Command

#### Navigasi

| Command            | Kepanjangan               | Keterangan                                 |
| ------------------ | ------------------------- | ------------------------------------------ |
| `pwd`              | _print working directory_ | melihat nama directory sekarang            |
| `ls`               | _lists_                   | melihat isi directory                      |
| `ls -al`           |                           | melihat isi directory beserta hidden files |
| `cd <folder-name>` | _change directory_        | untuk pindah directory                     |
| `cd ..`            |                           | untuk kembali ke directory sebelumnya      |
| `cd ~`             |                           | untuk kembali ke home directory            |

#### Membuat File & Directory

| Command                         | Keterangan                        |
| ------------------------------- | --------------------------------- |
| `touch <file-name.file-format>` | membuat sebuah file               |
| `mkdir <folder-name>`           | membuat sebuah directory / folder |

#### Membuka File

| Command                  | Keterangan                                   |
| ------------------------ | -------------------------------------------- |
| `nano <file-name>`       | membuka file di CLI                          |
| `<app-name> <file-name>` | membuka file dengan aplikasi yang ditentukan |

#### Melihat Isi File

| Command                         | Keterangan                                                              |
| ------------------------------- | ----------------------------------------------------------------------- |
| `head <file-name>`              | melihat beberapa line awal dari isi file (default = 10 baris pertama)   |
| `tail <file-name>`              | melihat beberapa line akhir dari isi file (default = 10 baris terakhir) |
| `cat <file-name>`               | melihat isi file (secara keseluruhan)                                   |
| `head \|\| tail -n <file-name>` | menampilkan isi file dengan baris yang muncul yaitu n baris             |

#### Menyalin, Memindahkan, dan Menghapus files & directory

**_Copy_**

| Command                               | Keterangan                              |
| ------------------------------------- | --------------------------------------- |
| `cp <source_file> <destination_file>` | menyalin file ke directory yang berbeda |
| `cp <file-name> <copy-file-name>`     | menyalin file di directory yang sama    |
| `cp -r <folder-name>`                 | menyalin directory / folder             |

**_Move_**

| Command                                                                     | Keterangan                                                 |
| --------------------------------------------------------------------------- | ---------------------------------------------------------- |
| `mv <old-file-name> <new-file-name>`                                        | mengubah nama file dan file berada di directory yang tetap |
| `mv <nama-file-yang-dipindah> <tujuan-pindah/nama-file(bisa_baru\|\|lama)>` | memindahkan file ke directory lain sekaligus mengubah nama |
| `mv -r <folder-name>`                                                       | memindahkan directory / folder                             |

**_Remove_**

| Command                | Keterangan                       |
| ---------------------- | -------------------------------- |
| `rm <file-name>`       | menghapus file                   |
| `rm -r <folder-name>`  | menghapus directory / folder     |
| `rm -rf <folder-name>` | menghapus directory secara paksa |

---

# Module 2 - Git & Github Dasar

-   Git merupakan version control system.
-   Git adalah aplikasi yang dapat melacak setiap perubahan yang terjadi pada suatu folder atau file.

#### Alasan menggunakan Git dan Github

-   bisa digunakan untuk pengerjaan proyek bersama (kolaborasi) tanpa harus mengcopy paste folder untuk mengupdate perubahan
-   hasil perubahan pun bisa disimpan secara online sehingga pengerjaan tim bisa tersimpan dan dapat langsung diakses oleh tim

#### Perbedaan Git dan Github

-   **Pengertian:**
    -   Git merupakan aplikasi berupa version control system.
    -   Github merupakan layanan cloud
-   **Fungsi:**
    -   Git berfungsi untuk mencatat segala perubahan file maupun directory dalam suatu repository project.
    -   Github berfungsi untuk menyimpan dan mengelola project dan disimpan dalam repository
-   **Akses:**
    -   Git dapat diakses secara offline (lokal komputer)
    -   Github dapat diakses secara online ([Web: Github.com](github.com))

### Instalasi Git

Install software GIT di [https://git-scm.com/](https://git-scm.com/)

```bash
# Cek Instalasi apakah sudah terpasang di Lokal Komputer
git --version
```

### Setup Awal Git

```bash
# SETUP AWAL
git config --global user.name "nama kalian"
git config --global user.email "email kalian"

# CEK SETUP
git config --list
```

> :warning: **email yang disetup HARUS SAMA dengan yang digunakan pada GITHUB** :warning:

### Pasang Git di Folder Project

```bash
# Jika folder sudah dibuat
git init

# Jika folder baru
git init <new-folder-name>
```

> **`git init` hanya digunakan satu kali pada sebuah folder / repositori**

### Melacak Perubahan

```bash
git status
```

> Perubahan = penambahan, penghapusan, pengeditan file / folder

---

#### Kondisi File pada Git

![IMAGE](/week-1/kondisi-file-git.jpeg)

-   ### Modified

    Modified adalah kondisi dimana revisi atau perubahan sudah dilakukan, tetapi belum ditandai (untracked) dan belum disimpan dalam version control.

-   ### Staged

    Staged adalah kondisi dimana revisi sudah ditandai (modified) namun belum disimpan di version control.

-   ### Commited
    Commit/committed adalah kondisi dimana revisi sudah disimpan pada version control.

### Menandai Perubahan

```bash
# Salah satu File
git add <file-name>

# Semua file
git add .
```

### Menambah Keterangan Perubahan dan Menyimpan Perubahan

```bash
git commit -m "...."
```

> **Ketika mengalami perubahan secara terus menerus maka melakukan `git add .` dan `git commit`**

### Melihat Hasil Commit

```bash
git log
# ATAU
git log --oneline
```

**Melihat log bisa dari berbagai sisi:**

1. Melihat log menggunakan nomor version/commit

    `git log <nomor-version||commit>`

2. Melihat log file tertentu

    `git log <file-name>`

3. Melihat log berdasarkan author

    `git log --author='...'`

### Mengecek Perubahan

```bash
git diff
```

### Mengembalikan keadaan perubahan

-   #### Membatalkan Perubahan - Belum Stagged dan Belum Commited

    ```bash
    git checkout <file-name>
    ```

-   #### Membatalkan Perubahan - Sudah Stagged namun Belum Commited

    Stagged = sudah di `git add`

    ```bash
    git reset <file-name>
    ```

-   #### Membatalkan Perubahan - Sudah Commited

    ```bash
    # File menjadi staged
    git checkout <nomor_commit> <file-name>

    # File menjadi modified dan not staged
    git reset <file-name>
    ```

#### Case Tertentu

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

#### Git Revert

Git revert akan membatalkan semua perubahan yang ada tanpa menghapus commit terakhir. Jika menggunakan git reset, commit terakhir akan hilang.

```bash
git revert -n <nomor-commit>
```

### Perbedaan `git checkout`, `git reset`, `git revert`

<p><code>git checkout</code> : <img src="/week-1/git-checkoute.jpeg" width="300"></p>
<p><code>git reset</code> : <img src="/week-1/git-reset.jpeg" width="300"></p>
<p><code>git revert</code> : <img src="/week-1/git-revert.jpeg" width="300"></p>

### Upload ke Github

```bash
# Melakukan remote dengan repository yang dipilih
git remote add origin <link_repository>

# Cara menambahkan perubahan ke dalam repository
git push -u origin main
```

> **`git remote` dilakukan sekali**

### Clone Repository dari Github ke Local

```bash
git clone <link_repository>
```

---

# Module 3 - HTML

-   HTML adalah singkatan dari Hypertext Markup Language.
-   HTML digunakan untuk menampilkan konten pada browser.
-   HTML bersifat statis. HTML hanya bertugas menampilkan konten yang diminta oleh developer.

#### Tools yang dibutuhkan

-   Browser (Chrome, Edge, Mozilla, dkk)
-   Text / Code Editor (VS Code, Sublime text, notepad++, atom, dkk)

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Judul Halaman di Bagian Tab Browser</title>
    </head>
    <body>
        <!-- ISI KONTEN HTML -->
    </body>
</html>
```

### HTML Anatomy

```html
<p>This is Paragraph</p>
```

**Keterangan:**

| Element           | Keterangan  |
| ----------------- | ----------- |
| `<p>`             | Opening tag |
| This is Paragraph | Content     |
| `</p>`            | Closing tag |
| `<p></p>`         | Element     |

### HTML Element

HTML element didefinisikan sebagai opening tag, content, dan closing tag.

contoh:

```html
<body>
    <div>
        <h1>Ini Heading</h1>
        <p>Ini Paragraf</p>
        <a>Ini anchor</a>
    </div>
</body>
```

### HTML Attributes

Attribute adalah properties dari sebuah HTML Element.
Semua HTML Element memiliki attribute.

contoh:

```html
<body>
    <!-- Tag div dengan atribut class -->
    <div class="header">
        <!-- Tag h1 dengan atribut class -->
        <h1 class="heading">Ini Heading</h1>

        <!-- Tag p dengan atribut id -->
        <p id="paragraf-1">Ini Paragraf</p>

        <!-- Tag img dengan atribut src -->
        <img scr="#" alt="Gambar" />

        <!-- Tag a dengan atribut href -->
        <a href="#">Ini anchor</a>
    </div>
</body>
```

### HTML Comment

-   Comment tidak akan dieksekusi oleh sistem.
-   Comment hanya untuk dibaca oleh sesama programmer.

```html
<!-- Ini adalah syntax Comment pada HTML -->
```

### Tag Image

```html
<img src="#" alt="xxx" />
```

**Keterangan:**

| Element            | Keterangan                                                         |
| ------------------ | ------------------------------------------------------------------ |
| `<img>`            | Element image                                                      |
| `src` _source_     | atribut untuk memberitahukan sumber gambar                         |
| `alt` _altenative_ | atribut yang menjadi penjelas dari gambar jika gambar tidak muncul |

### Tag Video

```html
<video controls>
    <source src="movie.mp4" type="video/mp4" />
</video>
```

**Keterangan:**

| Element           | Keterangan                                                  |
| ----------------- | ----------------------------------------------------------- |
| `<video></video>` | Element image                                               |
| `control`         | untuk mengatur videonya di play / pause dan indikator menit |

### HTML Table

```html
<body>
    <!-- HTML Element untuk table -->
    <table border="1">
        <!-- Baris pada tabel -->
        <tr>
            <!-- Header Table -->
            <th>Company</th>
            <th>Contact</th>
            <th>Country</th>
        </tr>

        <!-- Baris pada tabel -->
        <tr>
            <!-- Data Tabel baris ke 1 -->
            <td>John Doe</td>
            <td>0812345***</td>
            <td>Indonesia</td>
        </tr>

        <!-- Baris pada table -->
        <tr>
            <!-- Data Tabel baris ke 2 -->
            <td>Dave Win</td>
            <td>0812493***</td>
            <td>Indonesia</td>
        </tr>
    </table>
</body>
```

### HTML Form

```html
<body>
    <!-- HTML element untuk Form -->
    <form>
        <!-- Tag element div digunakan untuk membagi section agar lebih rapi dan mudah dibaca -->
        <div>
            <label for="username">Username</label> <br />
            <input type="text" placeholder="Your username" name="username" id="username" />
        </div>
        <div>
            <label for="email">Email</label> <br />
            <input type="email" placeholder="Your email" name="email" id="email" />
        </div>
        <div>
            <label for="password">password</label> <br />
            <input type="password" placeholder="Your password" name="password" id="password" />
        </div>
        <div>
            <input type="submit" value="Sign Up" />
        </div>
    </form>
</body>
```

### Semantic HTML

-   Semantic artinya penggunaan element HTML yang sesuai dengan kebutuhan konten
-   HTML semantic:
    -   `<article>`
    -   `<aside>`
    -   `<details>`
    -   `<figcaption>`
    -   `<figure>`
    -   `<footer>`
    -   `<header>`
    -   `<main>`
    -   `<mark>`
    -   `<nav>`
    -   `<section>`
    -   `<summary>`
    -   `<time>`
-   Kegunaan Semantic HTML:
    -   Meningkatkan accessibility
    -   Meningkatkan SEO
    -   Lebih mudah di maintain

### Deploy HTML

-   Deploy adalah sebuah proses untuk menyebarkan aplikasi yang sudah kita kerjakan supaya bisa digunakan oleh orang-orang
-   Cara mendeploy HTML di [Netlify.com](netlify.com):
    -   Daftar Akun
    -   Sign in
    -   Add new site di button **New Site from Git**
    -   Link to your github
    -   Authorize netlify with github
    -   Select your repository in github
    -   Configure your setting
    -   Tunggu dan Selesai. Nanti akan muncul url websitenya
    -   Untuk mengubah nama website, bisa ke **Deploy Setting** -> **Change site name**

---

# Module 4 - CSS

-   CSS adalah singkatan dari Cascading Style Sheets
-   CSS adalah bahasa yang digunakan untuk mendesain halaman website.

### CSS Structure

```css
selector {
    property: value;
}
```

-   Selector digunakan untuk menunjuk elemen HTML mana yang hendak kita ubah styling-nya menggunakan CSS.

### CSS Comment

```css
/* Ini adalah syntax comment pada CSS */
/* 
Ini adalah syntax multiple line
*/
```

### Penyisipan CSS ke dalam HTML

-   **Inline Styles**

    Inline styles adalah menambahkan CSS pada atribut HTML

    ```html
    <p style="color: coral; font-size: 90px;">Ini adalah paragraf yang menggunakan inline styles</p>
    ```

-   **Tag `<style></style>` / Internal Styles**

    Tag `<style></style>` bisa dibuat pada file HTML dan diletakkan pada `<head></head>`

    ```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8" />
            <meta http-equiv="X-UA-Compatible" content="IE=edge" />
            <meta name="viewport" content="width=device-width, initial-scale=1.0" />
            <title>Document</title>
            <style>
                p {
                    color: aqua;
                }
            </style>
        </head>
        <body>
            <p>Ini adalah paragraf</p>
        </body>
    </html>
    ```

-   **External CSS (.css) / External Styles**

    Jika membutuhkan banyak code pada CSS, untuk memisahkan code CSS di file tersendiri (extension .css) dan terpisah dari file HTML.

    File HTML `index.html`:

    ```html
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8" />
            <meta http-equiv="X-UA-Compatible" content="IE=edge" />
            <meta name="viewport" content="width=device-width, initial-scale=1.0" />
            <title>Document</title>
            <link rel="stylesheet" href="style.css" />
        </head>
        <body>
            <p>Ini adalah paragraf</p>
        </body>
    </html>
    ```

    File CSS `style.css`:

    ```css
    p {
        color: aqua;
    }
    ```

### CSS - Tag Name

-   Tag Elemen HTML secara langsung pada CSS.
-   Jika menggunakan Tag Element, maka ini bersifat global.
-   Global artinya akan mempengaruhi seluruh Tag Elemen HTML yang ada pada file tersebut
-   **Ditulis dengan nama tag HTML itu sendiri**

```css
p {
    color: aqua;
}
```

> Tag `<p></p>` adalah element HTML dan ditulis `p` sebagai selector CSS

### CSS - Class Name

-   Attribute class pada elemen HTML lalu memanggil nama class tersebut pada CSS
-   HTML yang memiliki class yang sama, akan mempunyai styling yang sama saat digunakan pada CSS
-   **Ditulis dengan menggunakan dot (.) beserta nama classnya**

```css
.title {
    color: aqua;
}
```

> Element HTML yang memiliki `class = "title"` akan ditulis `.title` sebagai selector CSS

### CSS - Mutiple Class

-   Penulisan nama class bisa lebih dari 1 dalam 1 element HTML

Contoh:

`index.html`

```html
<body>
    <h1 class="title uppercase">Hello My Name is Felli</h1>
    <h1 class="title lowercase">I'm Informatics Student</h1>
</body>
```

`style.css`

```css
.title {
    color: red;
}
.uppercase {
    text-transform: uppercase;
}
.lowercase {
    text-transform: lowercase;
}
```

> Class `uppercase` dan `lowercase` akan memiliki styling yang berbeda walaupun dia di class utama yang sama (`.title`)

### CSS - ID Name

-   Digunakan jika hanya ada 1 element pada 1 page.
-   **Ditulis dengan menggunakan slash (#) beserta nama ID nya**

```css
#navigation {
    color: aqua;
}
```

> Element HTML yang memiliki `id = "navigation"` akan ditulis `#navigation` sebagai selector CSS

#### Perbedaan ID Name dan Class Name

-   Gunakan ID Name jika hanya ada 1 elemen pada file/halaman HTML.
-   Gunakan Class Name jika akan ada beberapa element HTML yang memiliki styling/desain yang sama.

#### Chaining Selectors

Contoh kasus : Jika kita memiliki 3 tag elemen HTML pada CSS namun kita ingin ada 1 elemen HTML yang memiliki styling berbeda.

Contoh:

`index.html`

```html
<body>
    <h1>Hello My Name is Felli</h1>
    <h1>I'm Informatics Student</h1>
    <h1 class="profile">About me</h1>
</body>
```

`style.css`

```css
/* Styling berlaku untuk semua elemen dengan tag <h1> */
h1 {
    color: red;
}

/* Styling berlaku pada element dengan tag <h1> yang memiliki class profile */
h1.profile {
    color: blue;
}
```

### Nested Element

CSS memiliki konsep yaitu setiap element memiliki _parent_ dan _child_

### Hierarki CSS

-   Penulisan selector memiliki hierarki di dalam penggunaan CSS.
-   Hierarkinya dari paling bawah sampai paling prioritas:
    1. `*` yang berarti semua element
    2. Element HTML
    3. Class Name `(.)`
    4. ID Name `(#)`
    5. `!important` digunakan untuk meng-override styling sebelumnya.

**Contoh beberapa kasus:**

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
        <style>
            #special {
                color: orange;
            }
            h1 {
                color: green;
            }
            #special {
                color: blue;
            }
        </style>
    </head>
    <body>
        <h1 id="special">This is h1 with id special</h1>
        <h1>This is h1 without id</h1>
    </body>
</html>
```

> Warna dari tag `h1` dengan id `special` menjadi biru. Hal tersebut dikarenakan styling terakhir adalah style yang akan digunakan.

`styles.css`

```css
#special {
    color: orange;
}
```

`index.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
    <body>
        <h1 id="special" style="color: blue;">This is h1 with id special</h1>
        <h1>This is h1 without id</h1>
        <link rel="stylesheet" href="styles.css" />
    </body>
</html>
```

> Warna akhir dari tag `h1` dengan id `special` menjadi biru. Hal tersebut karena inline CSS akan selalu mendapatkan prioritas tertinggi (pengecualian untuk `!important`

### Multiple Selector

Contoh:

`style.css`

```css
h1,
p {
    color: red;
}
```

### Flexbox CSS

-   Flexbox adalah cara untuk mengatur layout.
-   Flexbox memiliki kemampuan untuk menyesuaikan layout secara otomatis.
-   Flexbox menjadi alternatif untuk membuat metode responsif web design.
-   **Konsep flexbox** : Flexbox memiliki 1 parent/container dan bisa beberapa child/item.

Contoh flexbox:
`index.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Flexbox</title>
        <link rel="stylesheet" href="styles.css" />
    </head>
    <body>
        <!-- PARENT -->
        <div class="container">
            <!-- CHILD -->
            <div class="item">item</div>
            <div class="item">item</div>
            <div class="item">item</div>
            <div class="item">item</div>
            <div class="item">item</div>
            <div class="item">item</div>
            <div class="item">item</div>
        </div>
    </body>
</html>
```

`style.css`

```css
.container {
    display: flex;
    border: 5px, solid purple;
}

.item {
    border: 1px solid #000;
    width: 200px;
    height: 200px;
    background-color: orange;
}
```

Hasil :

![Hasil tampilan website](/week-1/contoh-html-flexbox.jpeg)

#### Property Flexbox

##### Ordering & Orientation

-   `flex-direction`

    -   Properti `flex-direction` digunakan untuk mengatur letak item child.
    -   Value:
        -   `row` (default): secara default letak item child membentuk sebuah baris dari kiri ke kanan.
        -   `row-reverse`: letak item child membentuk sebuah baris dari kanan ke kiri
        -   `column`: letak item child membentuk sebuah baris dari atas ke bawah
        -   `column-reverse`: letak item child membentuk sebuah baris dari bawah ke atas

    ![flex_direction](/week-1/flex-direction.jpeg)

-   `flex-wrap`

    -   flex secara default akan membuat tata letak item children dalam 1 line saja. flex akan menyesuaikan space yang ada.
    -   namun jika kamu ingin membatasi jumlah item children dalam 1 line lalu item children yang lain akan pindah ke posisi line yang baru, maka kita bisa menggunakan `flex-wrap`
    -   Value:
        -   `no-wrap` (default): secara default , flex tidak menggunakan flex-wrap
        -   `wrap`: flex item akan memiliki beberapa line dari atas ke bawah jika space dalam 1 line sudah full width.
        -   `wrap-reverse`: kebalikan dari wrap yaitu lex item akan memiliki beberapa line dari bawah ke atas jika space dalam 1 line sudah full width

    ![flex_direction](/week-1/flex-wrap.jpeg)

-   `flex-flow`

    -   properti `flex-flow` digunakan sebagai shortcut untuk set up flex-direction dan flex-wrap bersamaan.
    -   Value:
        -   `row nowrap`
        -   `column wrap`
        -   `column reverse`
        -   `row-reverse wrap-reverse`

-   `order`

    -   properti `order` pada flex adalah berfungsi untuk ordering item mana yang ingin kita atur posisinya berdasarkan urutan order
    -   Value:
        -   `-1` : Item child yang di set order -1, maka item child tersebut akan berada di ordering paling awal atau paling kiri.
        -   `0`(default) : Flex secara default memiliki order 0 pada setiap item child. Ini berarti 0 akan membuat item child sesuai urutan pada html.
        -   `1` : Item child yang di set order 1, maka item child tersebut akan berada di ordering paling akhir atau paling kanan

    ![order](/week-1/order.jpeg)

##### Alignment

-   `justify-content`

    -   properti `justify-content` digunakan untuk mengatur tata letak dan space antar item child secara horizontal atau main axis.
    -   Value:
        -   `flex-start`
        -   `flex-end`
        -   `center`
        -   `space-between`
        -   `space-around`
        -   `space-evenly`

    ![justify_content](/week-1/justify-content.jpeg)

-   `align-items`

    -   properti `align-items` digunakan untuk mengatur align dari item child secara vertikal atau cross axis.
    -   Value:
        -   `flex-start`
        -   `flex-end`
        -   `center`
        -   `baseline`
        -   `stretch`

    ![align_items](/week-1/align-items.jpeg)

-   `align-self`

    -   properti `align-self` digunakan untuk mengatur align item pada masing-masing item.
    -   Value:
        -   `flex-start`
        -   `flex-end`
        -   `center`
        -   `baseline`
        -   `stretch`

    ![align_self](/week-1/align-self.jpeg)

-   `align-content`

    -   properti `align-content` memiliki konsep yang sama seperti `justify-content`
    -   `align-content` digunakan untuk mengatur tata letak dan space antar item child secara vertikal atau cross axis.
    -   `align-content` akan berjalan jika item lebih dari 1 line/baris.
    -   Value:
        -   `flex-start`
        -   `flex-end`
        -   `center`
        -   `space-between`
        -   `space-around`
        -   `space-evenly`
        -   `stretch`

    ![align_content](/week-1/align-content.jpeg)

##### Flexibility

-   `flex-grow`

    -   properti `flex-grow` dapat mengatur size suatu item child pada flexbox.
    -   value dari properti `flex-grow` adalah number dan tidak boleh negatif

    ![flex_grow](/week-1/flex-grow.jpeg)

-   `flex-shrink`

    -   `flex-shrink` adalah properti yang membuat size suatu item child mengecil secara relatif terhadap item child yang lainnya.
    -   value dari properti `flex-shrink` adalah number. Number negatif dianggap tidak valid.
    -   semakin besar value number dari properti ini, maka semakin kecil size dari suatu item child.

-   `flex-basis`

    -   `flex-basis` adalah properti yang sama fungsinya seperti `width`.
    -   `flex-basis` mengatur width dari setiap item child.
        -   jika kita telah menggunakan `width`, maka `flex-basis` akan melakukan override properti `width`.
    -   namun `flex-basis` tidak akan berjalan jika kita telah menggunakan `min-width` dan `max-width`.
    -   Value:
        -   `auto`
        -   `number`
        -   `initial`
        -   `inherit`

---

# Module 5 - Algorithm & Data Structures

-   Algoritma adalah deskripsi berupa step-step yang dibutuhkan untuk menyelesaikan suatu masalah

### Manfaat Algoritma dan Struktur Data

-   Data struktur digunakan untuk mengelola/manajemen sebuah data
-   Algoritma yang akan menyelesaikan suatu permasalahan menggunakan
    data tersebut.
-   Belajar algoritma sama aja dengan mengingat kembali alur berfikir yg terstruktur

### Ciri-ciri Algoritma

-   **Input** - memiliki 0 atau lebih input
-   **Output** - memiliki minimal 1 buah output
-   **Definisiteness** - instruksi yang jelas dan tidak ambigu
-   **Finiteness** - memiliki titik berhenti (stop)
-   **Effectiveness** - tepat sasaran dan efisien

### Jenis Proses Algoritma

-   **Sequence** - instruksi yang dijalankan secara _berurutan_
-   **Selection** - instruksi yang dijalankan jika memenuhi suatu _kondisi_
-   **Iteration** - instruksi yang _berulang_ kali dijalankan selama memenuhi suatu _kondisi_
-   **Concurrent** - instruksi yang dijalankan secara _bersamaan_

### Penulisan Algoritma

-   **Deskriptif**
    -   Penulisan ditulis seperti menulis tutorial / langkah-langkah dengan menggunakan bahasa sehari-hari
-   **Flow Chart**
    -   Penulisan algoritma disajikan dengan menggunakan diagram
    -   Penyajian algoritma lebih mudah dibaca karena memiliki tampilan visual
    -   Flowchart memiliki simbol sendiri dan memiliki arti
-   **Pseudo Code**
    -   Penulisan ditulis hampir menyerupai penulisan pada kode pemrograman
    -   Bagian-bagian pseudocode:
        -   **Judul** - penjelasan dari algoritma yang dibuat
        -   **Deklarasi** - mendefinisikan nama (variabel) yang akan digunakan
        -   **Deskripsi** - langkah-langkah penyelesaian masalah
            > Penulisan tidak ada aturan baku
    -   Pseudocode harus **jelas, simpel, konsisten, dan mudah dibaca orang lain**

### Contoh Algoritma

-   Kasus :

    -   Si A ingin menampilkan deretan nilai 0 sampai N
    -   N adalah nilai akhir yang diinputkan
    -   Jika Si A menginputkan N dengan nilai 100, maka program akan menampilkan deretan nilai 1,2,3,4,5,...,100

-   Algoritma :

    1. Membuat variabel N
    2. Input nilai N
    3. Buat deklarasi i = 0
    4. Jika i <= N maka tampilkan nilai i
    5. Tambahkan nilai i dengan 1
    6. Ulangi langkah 4
    7. Jika i > N maka perulangan berhenti
    8. Program selesai

-   Pseudocode

    ```
    STORE N WITHOUT ANY VALUE
    SET N WITH number 100

    FOR i FROM 0 TO N INCREMENT BY 1
        DISPLAY i
    END FOR
    ```

---

# Module 6 - JS Dasar - Intro Javascript

-   Javascript adalah bahasa pemrograman yang digunakan untuk logic pada sebuah website
-   JavaScript dapat berjalan melalui browser seperti chrome, mozilla, edge, dll
-   Javascript bisa dibuka di browser dengan cara :
    -   buka browser
    -   klik kanan mouse
    -   klik Inspect
    -   Di bagian tools, klik bagian Console
    -   Maka akan tampil sebuah console yang bisa digunakan secara langsung maupun hasil dari pemrograman menggunakan file html dan js

### Console.log()

-   `console.log()` adalah tempat untuk menampilkan isi sebuah variabel. Juga bisa digunakan untuk mengecek logika pemrograman, dan juga digunakan untuk debugging(untuk mengetahui error pada code) pada pemrograman web.

### Tipe Data Javascript

-   _**Primitive:**_
    -   **String**
        -   Tipe data yang menggunakan grup karakter yang ada pada di keyboard
        -   Karakter yang bisa yaitu letters (huruf), number (angka), spaces (spasi), symbol, dll
        -   Penulisan tipe data string harus diawali single quotes (`'......'`) atau double quotes (`"....."`)
        -   Contoh : `"Hello World"`
    -   **Number**
        -   Tipe data yang mengandung semua angka termasuk angka desimal
        -   Contoh : `12`, `30`, `20.75`, `-25`
    -   **Boolean**
        -   Tipe data yang hanya mempunyai 2 buah nilai yaitu `true` dan `false`
    -   **Null**
        -   Tipe data yang diartikan bahwa sebuah variabel tidak memiliki nilai
            > Null berbeda dengan string kosong karena string kosong bertipe string
    -   **Undefined**
        -   Tipe data yang mempresentasikan variabel yang tidak memiliki nilai
        -   Undefined didapat dari :
            -   Nilai pemanggilan variabel yang belum didefinisikan
            -   Nilai dari pemanggilan element array yang tidak ada
            -   Nilai dari pemanggilan property object yang tidak ada
            -   Nilai dari pemanggilan fungsi yang tidak mengembalikan nilai (return)
            -   Nilai dari parameter fungsi yang tidak memiliki argumen

-   _**Non-primitive:**_
    -   **Object**
        -   Berupa koleksi tipe data yang saling berhubungan
        -   Dapat menyimpan berbagai tipe data primitive
        -   Mempunyai key dan value

### Variabel

-   Variabel adalah tempat untuk menyimpan nilaii

-   3 cara mendefinisikan sebuah variabel di js:
    -   **`var`**
        -   `var` adalah pendefinisian agar nilai variabel bisa dinamis / dapat diubah
        -   Versi lama js
        -   Tidak mendukung kaidah global variabel dan local variabel, pendefinisian bisa double
    -   **`let`**
        -   `let` adalah versi terbaru pendefinisian agar nilai variabel bisa dinamis / dapat diubah
        -   Versi baru ES6
        -   Mendukung kaidah global variabel dan local variabel, pendefinisian hanya bisa satu kali
    -   **`const`**
        -   `const` adalah pendefinisian variabel yang nilainya tidak dapat diubah
        -   Biasanya digunakan untuk menggambarkan konstanta sebuah nilai
        -   Untuk tipe data object dan array, nilai didalamnya masih bisa di tambahkan/diubah

-   Aturan penamaan variabel:
    -   Harus mendeskripsikan tentang data yang disimpan
    -   Tidak bisa menggunakan number pada awal nama variabel
    -   Gunakan camelCase untuk penamaan yang lebih dari 1 kata. Contoh : `myName`, `myAge`

### Operator

-   **Assignment Operator**
    -   Digunakan untuk menyimpan sebuah nilai pada variabel
    -   Operatornya yaitu sama dengan (=)

-   **Mathematical Assignment Operator**
    -   Digunakan untuk melakukan operasi matematika
    -   Penulisan bisa dilakukan dengan cara `x += 3`. Berarti `x = x + 3`.
    -   Penulisan lainnya : `-=`, `*=`, `/=`

-   **Increment & Decrement**
    -   Digunakan untuk menambah / mengurangi sebesar 1 nilai
    -   Increment -> `i++`
    -   Decrement -> `i--`

-   **Aritmethic Operator**
    -   Operator yang melibatkan operasi aritmatika
    -   Penjumlahan (`+`), pengurangan (`-`), perkalian (`*`), pembagian (`/`), sisa bagi/modulus (`%`), pangkat (`**`)

-   **Comparison Operator**
    -   Operator yang digunakan untuk membandingkan satu nilai dengan nilai lainnya
    -   Hasil perbandingan bernilai antara true dan false
    -   Simbol: `<`, `>`, `<=`, `>=`, `==|===`, `!=|!==`

-   **Logical Operator**
    -   Digunakan untuk sebuah conditional pada pemrograman
    -   Hasil logical bernilai boolean antara `true` dan `false`
    -   Simbol: AND (`&&`), OR (`||`), NOT (`!`)

### Conditional

-   Conditional merupakan statement percabangan yang menggambarkan suatu kondisi

-   Jika kondisi benar (true)maka code yang didalamnya akan dijalankan

-   **IF Statement:**
    ```javascript
    if (condition) {
        // code yang dieksekusi
    }
    ```
    -   Arti: JIKA kondisi benar MAKA eksekusi kode yang dibuat
    -   Kondisi bisa berupa perbandingan, logical, boolean

-   **IF-ELSE Statement:**
    ```javascript
    if (condition) {
        // code yang dieksekusi jika kondisi benar
    } else {
        // code yang dieksekusi jika kondisi salah
    }
    ```
    -   Arti: JIKA kondisi **benar** MAKA eksekusi kode yang dibuat. JIKA kondisi **salah** MAKA eksekusi kode yang dibuat.
    -   Else akan mengeksekusi sebuah statement/code jika suatu kondisi bernilai false

-   **IF-ELSE IF Statement:**
    ```javascript
    if (condition_1) {
        // code yang dieksekusi jika kondisi 1 benar
    } else if (condition_2) {
        // code yang dieksekusi ketika kondisi 1 salah, kondisi 2 benar
    } else {
        // code yang dieksekusi jika kondisi 1 dan 2 salah
    }
    ```
    -   Arti: JIKA kondisi 1 **benar** MAKA eksekusi kode yang dibuat. JIKA kondisi 1 **salah**, akan tetapi kondisi 2 **benar** MAKA eksekusi kode yang yang dibuat. JIKA kondisi 1 dan 2 **salah** MAKA eksekusi kode yang dibuat
    -   Dapat digunakan jika memiliki berbagai kondisi

-   **Truthy and Falsy:**
    -   Truthy dan falsy digunakan untuk mengecek apakah variabel telah terisi namun tidak mementingkan nilainya.

-   **Switch Case Conditional:**
    ```javascript
    switch (expression) {
        case value_1:
            statement_1;
            break;
        case value_2:
            statement_2;
            break;
        case value_3:
            statement_3;
            break;
        default:
            default_statement;
    }
    ```
    -   Digunakan jika kondisi dan percabangan terlalu banyak

-   **Ternary Operator:**
    ```javascript
    kondisi ? statement_true : statement_else;
    ```
    -   Merupakan short-syntax untuk statement if-else

### Looping

- Looping adalah statement yang mengulang sebuah instruksi hingga kondisi terpenuhi atau jika kondisi berhenti tercapai

- **FOR LOOP:**
    ```javascript
    for(inisialisasi; kondisi; kondisi_setelahnya){
        // statement
    }
    ```
  - Digunakan jika mengetahui banyak nilai pasti untuk perulangannya

- **WHILE LOOP:**
    ```javascript
    while (expression){
        // statement
    }
    ```
  - Instruksi perulangan akan dijalankan jika kondisi bernilai `true`
  - Digunakan ketika tidak mengetahui jumlah pasti dari perulangan

- **DO WHILE:**
    ```javascript
    do {
        // statement
    } while (expression)
    ```
    - Program setidaknya menjalankan pengulangan 1 kali sebelum dilakukan pengecekan kondisi

- **Nested Loop:**
    ```javascript
    for (inisialisasi; kondisi; kondisi_setelahnya){
        for(inisialisasi; kondisi; kondisi_setelahnya){
            //statement
        }
    }
    ```
  - Jika kita membuat looping didalam looping. Maka ini dinamakan Nested Loop. Looping pertama dianalogikan sebagai baris. Looping kedua dianalogikan sebagai kolom
