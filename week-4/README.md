# Minggu 4 : 10 - 13 Oktober 2022

> Materi async await dan fetch ada di week-3.md

---

# Module 7 - Git & Github Lanjutan

-   Membuat branch baru agar fitur" tidak bercampur.
-   Cara kolaborasi
    -   Membuat repo dan dibuat publik
    -   Tambahkan anggota agar bisa mengakses
    -   Buat branch dev dan jadikan default
    -   Anggota melakukan clone pada repo ke local computer
    -   melakukan `git pull` untuk update kode terbaru
    -   Anggota membuat branch baru sesuai tugasnya (`git branch`)
    -   Anggota mengerjakan kode di dalam branch masing"
    -   jika fitur sudah selesai, lakukan `git merge` dengan dev untuk menghindari conflic
    -   selanjutnya di push ke branch masing"

**Langkah-Langkah COLAB di bash:**

```bash
# GIT CLONE
git clone <url-git-repo>

# cd ke folder
cd <nama-folder-git>

# Pindah branch (pilih salah satu)
# git switch <nama-branch>
# git checkout <nama-branch>
git switch dev

# membuat sekaligus pindah
git checkout -b dev

# membuat branch baru
# git branch <nama-branch-baru>
git branch felli-login

# Melakukan coding

# Menambahkan checkpoint file
git add .

# Menambah keterangan
git commit -m "keterangan"

# Push perubahan ke branch
# git push -u origin <nama-branch-masing-masing>
git push -u origin felli-login

# Melakukan pull request di github
# branch felli-login ke branch dev

# team lead melakukan merge pull request

# Hasil: isi dari branch akan masuk ke branch utama
```

-   pull request adalah permintaan untuk menggabungkan branch yg di buat ke branch lain(utama)

**Update branch dev:**

```bash
# Pindah ke branch utama
git switch dev

# Update branch utama
git pull

# balik ke branch sendiri
git switch felli-login

# Ambil branch sendiri dari dev
# menggabungkan branch dev ke branch sendiri (dev ke felli-login)
git merge dev

# tambahkan perubahan

# lakukan perulangan dari git add hingga pull request
```

**Penanganan Conflic:**

-   Conflic terjadi jika sebuah file terjadi perubahan dan dilakukan oleh lebih dari 2 orang
-   Si A sudah pull request dan si B juga pull request dan ternyata si B terjadi conflic

```bash
# mengambil data terbaru dari dev
# karna si A sudah merge bareng dev

git switch dev
git pull
git switch felli-login
git merge dev

# Akan tampil pilihan yang mana yang conflic dan memilih apa yg seharunya dipake
# accept current change
# accept incoming change
# accept both change

# lakukan perubahan yang benar

git add .
git commit -m "..."
git push felli-login

# pull request
# melihat perubahan (team lead)
# di merge pull requestnya
```

---

# Module 9 - Responsive Web Design

-   Responsive web design bertujuan membuat desain website dapat di akses dalam device apapun
-   Viewport adalah bagian dari responsive. Area website yang dapat diakses oleh user.
-   Setting viewport:
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    ```
-   Penggunaan `max-width` membantu responsive
-   CSS Units:
    > [W3School CSS Units](https://www.w3schools.com/CSSref/css_units.asp)
    -   Absolute:
        cm|mm|in|px|pt|pc
        --|--|--|--|--|--
    -   Relative
        em|ex|ch|rem|vw|vh|vmin|vmax|%
        --|--|--|---|--|--|----|----|-
        > Perbedaan % dan vw.
        >
        > % bergantung parent element
        >
        > vw bergantung dengan viewport device
-   Breakpoint merupakan perubahan yang terjadi pada tampilan saat berganti device / ukuran width tertentu
-   Media query merupakan cara untuk penggunaan breakpoint
-   Media query di tulis di CSS dengan syntax:
    ```css
    @media not|only mediatype and (expressions) {
        CSS-Code;
    }
    ```
    ```html
    <!-- Cara Lain -->
    <link rel="stylesheet" media="mediatype and|not|only (expressions)" href="print.css" />
    ```
-   Cara-cara responsive:
    -   meta viewport
    -   max-width
    -   relative unit
    -   media query
    -   flex
    -   grid

---

# Module 10 - Bootstrap

-   Link Bootstrap : https://getbootstrap.com/
-   Teman-teman bootstrap : MUI, bulma, thailwind
-   Cara HTML bisa tersambung ke Bootstrap : https://getbootstrap.com/docs/5.2/getting-started/introduction/#quick-start
-   Bootstrap memiliki template element yang sudah disediakan contohnya dari form, component, warna, table, layout, dll.
-   Styling bootstrap kebanyakan tinggal memanggil namanya dan dituliskan dalam class elemen HTML nya.
-   **Layout - Breakpoint Bootstrap** : https://getbootstrap.com/docs/5.2/layout/breakpoints/#available-breakpoints
-   **Layout - container** (_sering digunakan untuk penggunaan default grid system_): https://getbootstrap.com/docs/5.2/layout/containers/
-   **Layout - Grid System** : https://getbootstrap.com/docs/5.2/layout/grid/
-   **Layout - Column system**: https://getbootstrap.com/docs/5.2/layout/columns/
