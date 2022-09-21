# Module 3 : HTML

## HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
    <body></body>
</html>
```

## HTML Anatomy

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

## HTML Element

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

## HTML Attributes

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

## HTML Comment

Comment tidak akan dieksekusi oleh sistem.
Comment hanya untuk dibaca oleh sesama programmer.

```html
<!-- Ini adalah syntax Comment -->
```

## Tag Image

```html
<img src="#" alt="xxx" />
```

**Keterangan:**

| Element            | Keterangan                                                         |
| ------------------ | ------------------------------------------------------------------ |
| `<img>`            | Element image                                                      |
| `src` _source_     | atribut untuk memberitahukan sumber gambar                         |
| `alt` _altenative_ | atribut yang menjadi penjelas dari gambar jika gambar tidak muncul |

## Tag Video

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

## HTML Table

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
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
</html>
```

## HTML Form

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
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
</html>
```

## Semantic HTML

Semantic artinya penggunaan element HTML yang sesuai dengan kebutuhan konten

HTML semantic:

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

Kegunaan Semantic HTML:

-   Meningkatkan accessibility
-   Meningkatkan SEO
-   Lebih mudah di maintain

## Deploy HTML

Deploy adalah sebuah proses untuk menyebarkan aplikasi yang sudah kita kerjakan supaya bisa digunakan oleh orang-orang

Cara mendeploy HTML di [Netlify.com](netlify.com):

-   Daftar Akun
-   Sign in
-   Add new site di button **New Site from Git**
-   Link to your github
-   Authorize netlify with github
-   Select your repository in github
-   Configure your setting
-   Tunggu dan Selesai. Nanti akan muncul url websitenya
-   Untuk mengubah nama website, bisa ke **Deploy Setting** -> **Change site name**
