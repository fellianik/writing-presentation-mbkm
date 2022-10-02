# Minggu 2 : 26 - 30 September 2022

---

# Module 6 - JS Dasar - Scope and Function

## Scope

-   **Scope** adalah konsep dalam flow data variabel

-   Digunakan untuk menentukan suatu variabel bisa diakses pada scope tertentu atau tidak

-   **Blocks** adalah code yang berada di dalam `{..}` (curly braces)

-   **Global scope** adalah variabel yang dapat diakses dimanapun dalam suatu file.

-   Pendeklarasian variabel global scope yaitu _dideklarasikan di luar blokcs_

    ```javascript
    let myName = "Naomi";

    function greeting() {
        return myName; // Naomi
    }

    console.log(myName);
    /*
    Output: Naomi
    */
    ```

    > variabel `myName` dideklarasikan diluar block sehingga ketika digunakan di dalam block, variabel bisa diakses

-   **Local scope** adalah variabel yang _dideklarasikan didalam block_ seperti function, conditional, looping.

-   Local scope hanya bisa _diakses didalam blocks saja_. Tidak bisa diakses diluar blocks.

    ```javascript
    function greeting() {
        let myName = "Naomi";
        return myName; // Naomi
    }

    console.log(greeting()); //Naomi

    console.log(myName); // error, karena variabel myName adalah local variable
    ```

    > variabel `myName` dideklarasikan didalam block sehingga variabel hanya bisa dieksekusi didalam block.
    >
    > Jika variabel diakses diluar block, maka terjadi error.

## Function

-   **Function** adalah block kode dalam sebuah grup untuk menyelesaikan 1 task / 1 fitur dan bisa digunakan berulang kali.

-   Pembuatan function:

    -   Cara 1 - function classic
        ```javascript
        function myFunction() {
            // statement
        }
        ```
    -   Cara 2 - function variable
        ```javascript
        let myFunction = function () {
            // statement
        };
        ```
    -   Cara 3 - arrow function
        ```javascript
        let myFunction = (parameter) => {
            // statement
        };
        ```

-   Cara pemanggilan function:

```javascript
// namaFunction()
myFunction();
```

-   **Parameter dan Argumen**

    -   Dengan parameter, function dapat menerima sebuah inputan data dan menggunakan untuk melakukan task.
        ```javascript
        // parameternya adalah (a, b)
        function sum(a, b) {
            // parameter diperlakukan seperti variabel dalam suatu fungsi
            return a + b;
        }
        ```
    -   Argumen adalah nilai yang digunakan saat memanggil function.
    -   Jumlah argumen harus sama dengan jumlah parameter.

        ```javascript
        function sum(a, b) {
            return a + b;
        }

        console.log(sum(3, 4)); // Output : 10
        ```

    -   **Default parameter** digunakan untuk memberikan nilai awal / default pada parameter function.
    -   Default parameter digunakan agar function tidak mengalami error saat pemanggilan tanpa argumen

        ```javascript
        function greeting(name = "Kay") {
            return "Hello " + name;
        }

        console.log(greeting("Naomi")); // Output : Hello Naomi

        console.log(greeting()); // Output: Hello Kay
        ```

-   Function bisa dipanggil didalam function lain

    ```javascript
    function multiply(num1, num2) {
        return num1 * num2;
    }

    function adding(result1, result2 = 4) {
        return multiply(result1, result2) + 4;
    }

    adding(4, 5); // return : 25
    ```

---

# Module 6 - JS Dasar - Data Type Built in Prototype & Method

-   Setiap tipe data memiliki property dan method yang bisa digunakan untuk mempermudah dalam melakukan manipulasi data dalam coding.

-   Penulisan menggunakan property : `tipeData.property`

-   Penulisan menggunakan method : `tipeData.prototype.method()`

-   [Reference : MDN Data Types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures?retiredLocale=id)

-   Berikut contoh-contoh property dan method:

    -   **STRING:**

        > [MDN String Property & Method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String?retiredLocale=id)

        **_String Properties_**

        -   `String.length`

            ```javascript
            const str = "Hello world";

            console.log(`String: ${str}, String length: ${str.length}`);
            // Output: "String: Hello world, String length: 11"
            ```

            > [MDN String length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length)

        **_String Method_**

        -   `toUppercase()`

             ```javascript
              const sentence = "The quick brown fox jumps over the lazy dog.";

              console.log(sentence.toUpperCase());
              // expected output: "THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG."
              ```
              > [MDN toUpperCase](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)

        -   `toLowerCase()`

            ```javascript
            const sentence = "The quick brown fox jumps over the lazy dog.";

            console.log(sentence.toLowerCase());
            // expected output: "the quick brown fox jumps over the lazy dog."
            ```

            > [MDN toLowerCase](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)

        -   `charAt()`

            ```javascript
            const sentence = "Halo perkenalkan saya Felliani.";

            const index = 5;

            console.log(`The character at index ${index} is ${sentence.charAt(index)}`);
            // Output: "The character at index 5 is p"
            ```

            > [MDN charAt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)

        -   `includes()`

            ```javascript
            const str = "To be, or not to be, that is the question.";

            console.log(str.includes("To be")); // true
            console.log(str.includes("question")); // true
            console.log(str.includes("nonexistent")); // false
            ```

            > [MDN includes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

        -   `split()`

            ```javascript
            const str = "The quick brown fox jumps over the lazy dog.";

            const words = str.split(" ");
            console.log(words[3]);
            // expected output: "fox"

            const chars = str.split("");
            console.log(chars[8]);
            // expected output: "k"

            console.log(str.split());
            // expected output: Array ["The quick brown fox jumps over the lazy dog."]

            console.log(str.split(""));
            // Output: Array ["T", "h", "e", " ", "q", "u", "i", "c", "k", " ", "b", "r", "o", "w", "n", " ", "f", "o", "x", " ", "j", "u", "m", "p", "s", " ", "o", "v", "e", "r", " ", "t", "h", "e", " ", "l", "a", "z", "y", " ", "d", "o", "g", "."]

            console.log(str.split(" "));
            // Output: Array ["The", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog."]
            ```

            > [MDN split](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)

    -   **NUMBER:**

        > [MDN Number Property & Method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)

        **_Number Method_**

        -   `isNaN()`

            Pengertian penggunaan `isNaN`

            ```javascript
            console.log(isNaN(94));
            // Output: false

            console.log(isNaN("Hello"));
            // Output: true

            console.log(isNaN(true));
            // Output : false
            ```

            Penggunaan `Number.isNaN`

            ```javascript
            function sanitize(x) {
                if (isNaN(x)) {
                    return Number.NaN;
                }
                return x;
            }

            console.log(sanitize(8));
            // Output : 8

            console.log(sanitize("hello"));
            // Output: NaN
            ```

            > [MDN Number.isNaN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)

        -   `toString()`

            ```javascript
            const count = 10;

            console.log(count.toString()); // displays '10'
            console.log((17).toString()); // displays '17'
            console.log((17.2).toString()); // displays '17.2'
            ```

            > [MDN toString](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toString)

        -   `toFixed()`

            ```javascript
            const numObj = 12345.6789;

            console.log(numObj.toFixed()); // Returns '12346'
            console.log(numObj.toFixed(1)); // Returns '12345.7'
            console.log(numObj.toFixed(3)); // Returns '12345.679'
            console.log(numObj.toFixed(6)); // Returns '12345.678900'
            ```

            > [MDN toFixed](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed)

    -   **MATH:**

        > [MDN Number Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

        **_Math Properties_**

        -   `Math.PI`

            ```javascript
            console.log(Math.PI);
            // expected output: 3.141592653589793
            ```

            > [MDN Math.PI](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/PI)

        -   `Math.LOG2E`

            ```javascript
            console.log(Math.LOG2E);
            // expected output: 1.4426950408889634
            ```

            > [MDN Math.LOG2E](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/LOG2E)

        -   `Math.SQRT2`

            ```javascript
            console.log(Math.SQRT2);
            // expected output: 1.4142135623730951
            ```

            > [MDN Math.SQRT2](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/SQRT2)

        **_Math Method_**

        -   `Math.abs()`

            ```javascript
            console.log(Math.abs(-Infinity)); // Infinity
            console.log(Math.abs(-1)); // 1
            console.log(Math.abs(-0)); // 0
            console.log(Math.abs(0)); // 0
            console.log(Math.abs(1)); // 1
            console.log(Math.abs(Infinity)); // Infinity
            ```

            > [MDN Math.abs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs)

        -   `Math.pow()`

            ```javascript
            console.log(Math.pow(7, 2));
            // expected output: 49

            console.log(Math.pow(5, 2));
            // Output: 25

            console.log(Math.pow(4, 0.5));
            // expected output: 2
            ```

            > [MDN Math.pow](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/pow)

        -   `Math.sqrt()`

            ```javascript
            console.log(Math.sqrt(9)); // 3
            console.log(Math.sqrt(49)); //7
            ```

            > [MDN Math.sqrt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt)

        -   Pembulatan Angka (`Math.round()`, `Math.floor()`, `Math.ceil`)

            ```javascript
            console.log(Math.round(123.123)); // 123
            console.log(Math.floor(4.9)); //4
            console.log(Math.ceil(4.2)); // 5
            ```

            > [MDN Math.round](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round)
            >
            > [MDN Math.floor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
            >
            > [MDN Math.ceil](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil)

        -   `Math.random()`

            ```javascript
            function getRandomInt(max) {
                return Math.floor(Math.random() * max);
            }

            console.log(getRandomInt(3));
            // expected output: 0, 1 or 2

            console.log(getRandomInt(1));
            // expected output: 0

            console.log(Math.random());
            // expected output: a number from 0 to <1
            ```

            > [MDN Math.random](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random)

-   Membuat method baru untuk tipe data

    Contoh:

    ```javascript
    String.prototype.reverse = function () {
        let s = "";
        for (let i = String(this).length - 1; i >= 0; i--) {
            s = s + String(this)[i];
        }

        return s;
    };

    // Method dari string
    console.log("hallo".reverse); // ollah

    console.log("selamat datang"); //gnatad tamales
    ```

-   Object literal

    Contoh:

    ```javascript
    // obj literal
    let kucing = {
        nama: "tom",
        makanan: "ikan",
    };

    // obj
    function Kucing(nama, makanan) {
        this.nama = nama;
        this.makanan = makanan;
    }

    const tom = new Kucing("tom", "ikan");
    tom.umur = 20;
    // Kucing.prototype.age = 20

    console.log(tom.nama); // tom
    console.log(tom.umur); // 20

    const pom = new Kucing("pom", "susu");
    console.log(pom.umur); // undefined
    // Undefined karena tidak ada property umur pada object Kucing
    ```

---

# Module 6 - JS Dasar - DOM Manipulation

## DOM - Introduction

-   DOM adalah jembatan supaya bahasa pemrograman dapat berinteraksi dengan dokumen HTML
-   DOM bukan bagian dari javascript, melainkan Web API untuk membangun website
-   Dengan DOM, HTML bisa dimanipulasi menggunakan bahasa pemrograman
-   HTML DOM membentuk struktur tree
-   Hasil yang didapat dari DOM:
    -   Element
        -   hanya HTML element
        -   `<h1>`, `<span>`, `<div>`, dkk
    -   Node
        -   setiap bagian terkecil di HTML
        -   text, comment, `<span>`

## DOM - Traversing Element

`index.html`

```html
<body>
    <h1 id="title">Hallo</h1>

    <ul class="list">
        <li class="item">satu</li>
        <li class="item">dua</li>
        <li class="item">tiga</li>
    </ul>
</body>
```

> ### HTMLCollection dan NodeList
>
> HTMLCollection dan NodeList menghasilkan data yang mirip dengan array dan pengaksesan sama dengan array.
>
> HTML Collection !== Array
>
> NodeList !== Array
>
> Property dan method pada HTMLCollection:
>
> -   length
> -   item()
> -   namedItem()

### Bagian 1 - Ke bawah

-   **`getElementById`**

    ```javascript
    let title = document.getElementById("title");

    console.log(title);
    // Output : <h1 id="title">Hallo</h1>
    ```

-   **`getElementsByClassName`**

    ```javascript
    let list = document.getElementsByClassName("list");

    console.log(list);
    // Output: HTMLCollection [ul.list]

    console.log(list[0]);
    /* Output:
    <ul class="list">
        <li class="item">satu</li>
        <li class="item">dua</li>
        <li class="item">tiga</li>
    </ul>
    */

    let item = document.getElementsByClassName("item");

    console.log(item);
    // Output: HTMLCollection(3) [li.item, li.item, li.item]

    console.log(item[0]);
    /* Output:
    <li class="item">satu</li>
    */
    ```

-   **`getElementsByTagName`**

    ```javascript
    let itemByTag = document.getElementsByTagName("li");

    console.log(itemByTag[1]);
    console.log(itemByTag.item(1));
    // Output: HTMLCollection(3) [li.item, li.item, li.item]

    console.log(itemByTag.length);
    // Output: 3
    ```

-   **`querySelectorFamily`**

    ```javascript
    let listQuery = document.querySelector(".list");

    console.log(listQuery);
    /* Output:
    <ul class="list">...</ul>
    */

    let itemQuery = document.querySelector(".item");

    console.log(itemQuery);
    /* Output:
    <li class="item">...</li>
    itu .item yang pertama ditemukan
    */

    let itemQueryAll = document.querySelectorAll(".item");

    console.log(itemQueryAll);
    /*Output:
    NodeList(3) [li.item, li.item, li.item]
    */

    console.log(itemQueryAll[1]);
    /* Output:
    <li class="item">dua</li>
    */
    ```

-   **`children`**

    ```javascript
    console.log(list[0].children);
    // Output: HTMLCollection(3) [li.item, li.item, li.item]
    ```

### Bagian 2 - Ke atas

-   **`parentElement`**

    ```javascript
    console.log(itemQuery.parentElement);
    // Output: <ul class="list">...</ul>
    ```

-   **`closest()`**

    ```javascript
    console.log(itemQuery.colsest(body))
    // Output : <body>...</body>
    console.log(itemQuery.colsest(.list))
    // Output: <ul class="list">...</ul>
    ```

### Bagian 3 - Ke samping

-   **`nextElementSibling`**

    ```javascript
    console.log(itemQuery.nextElementSibling);
    // Output: <li class="item">dua</li>
    ```

-   **`previousElementSibling`**

    ```javascript
    console.log(itemQuery.previousElementSibling);
    // Output: undefined
    ```

## DOM - Manipulating Element

`index.html`

```html
<head>
    <style>
        #tess {
            width: 100px;
            height: 20px;
            background-color: brown;
        }
    </style>
</head>
<body>
    <div id="tess"></div>
    <div id="app"></div>
    <div id="end"></div>
    <div class="container">
        <a href="google.com" class="link">Google</a>
    </div>
</body>
```

`script.js`

```javascript
let app = document.getElementById("app");
```

-   **Menampilkan konten ke HTML**

    ```javascript
    app.innerHTML = "Hallo";
    app.innerText = "Apa kabar?";
    ```

    Output:

    Teks `Hallo` dan `Apa Kabar?` akan muncul di dokumen HTML

    > | Syntax      | Perbedaan                                        |
    > | ----------- | ------------------------------------------------ |
    > | `innerHTML` | bisa menambahkan tag HTML                        |
    > | `innerText` | tulisan yang dimasukkan akan menjadi sebuah teks |
    >
    > ```javascript
    > app.innerHTML = "<h1>Hallo</h1>";
    > app.innerText = "<h1>Apa kabar?</h1>";
    > ```
    >
    > Output:
    >
    > <h1>Hallo</h1>
    >
    > `<h1>Apa kabar?</h1>`

-   **Membuat dan Menambahkan Element**

    ```javascript
    // membuat element HTML
    let p = document.createElement("p");
    p.innertext = "ini adalah paragraf";

    // Menambahkan element HTML ke dalam div
    app.append(p);
    // Hasil Output sama dengan penulisan di HTML => <p>ini adalah paragraf</p>
    // letaknya pun di dalam div

    let p2 = document.createElement("p");
    p2.innerText = "paragraf ke-2";

    app.appendChild(p2);

    // append bisa input berupa data string
    app.append("menggunakan append"); // bisa jalan
    // appendChild tidak bisa input berupa string
    app.appendChild("appendChild"); // error
    ```

-   **Menghapus element**

    ```javascript
    let end = document.getElementById("end");
    end.remove();
    ```

-   **Manipulasi atribut pada element HTML**

    ```javascript
    let link = document.getElementsByClassName("link")[0];

    // melihat isi atribut pada element
    console.log(link.attribbutes);
    /* Output: 
    NamedNodeMap {0: href, 1: class, href: href, class: class, length: 2}
    */

    // mengambil nilai atribut
    console.log(link.getAtribute("href"));
    // Output: google.com

    // menambah atribut pada element
    link.setAttribute("id", "google");
    // Hasil pada HTML element adalah <a href="google.com" class="link" id="google">Google</a>
    ```

-   **Manipulasi class pada element HTML**

    ```javascript
    let container = document.getElementsByClassName("container")[0];

    console.log(continer.classList); // [] list of class

    // menambahkan class
    container.classList.add("home");

    // menghapus class
    container.classList.remove("container");
    ```

## DOM - Manipulating Styles

-   **Menambah styling**

    **Syntax:**

    ```javascript
    variableElement.style.property = "value";
    ```

    Contoh:

    ```javascript
    link.style.color = "red";
    link.style.border = "1px solid black";
    link.style.padding = "5px 20px";
    link.style.backgroundColor = "aqua";
    ```

-   **Melihat styling suatu element**

    ```javascript
    let tess = document.getElementById("tess");

    // mengambil semua styling yang terjadi
    let tessStyle = getComputedStyle(tess);

    // menampilkan value dari property height
    console.log(tessStyle.height);
    // Output : 20px
    ```

-   **Another manipulating**
    -   `createTextNode`
    -   `textContent`
    -   `p.hasAtribute()`
    -   `p.className`
    -   `p.classList.togle()`
    -   `p.style.removeProperty()`

## DOM - Event

-   DOM Event digunakan untuk melakukan interaksi pada website

-   macam-macam event (umum):

    -   click
    -   submit
    -   focus
    -   blur
    -   hover
    -   change
    -   scroll

-   3 cara memberikan event:

    -   **HTML attribute**

        ```html
        <body>
            <h1 onclick="alert('Selamat datang')">Hallo</h1>
        </body>
        ```

    -   **Event property**

        `index.html`

        ```html
        <body>
            <p id="paragraf">Click me</p>
        </body>
        ```

        `script.js`

        ```javascript
        let paragraf = document.getElementById("paragraf");

        // cara yang function sekalian sama event
        paragraf.onclick = function () {
            alert("ini adalah paragaf");
        };

        // cara yang function dipisah sama eventnya
        function tampilkanAlert() {
            alert("ini alert");
        }

        paragraf.onclick = tampilkanAlert();
        ```

    -   **`addEventListener()`**

        `index.html`

        ```html
        <body>
            <button id="btn">Klik saya</button>
        </body>
        ```

        `script.js`

        ```javascript
        let btn = document.getElementById("btn");

        // Penulisan format addEventListener(event, function())
        btn.addEventListener("click", function () {
            alert("ini dari button");
        });

        // contoh menggunakan arrow function
        btn.addEventListener("click", () => {
            confirm("ini dari button");
        });

        // cara lain
        btn.addEventListener("click", tampilkanAlert);

        // mengecek event target
        btn.addEventListener("click", function (event) {
            console.log(event.target);
        });
        // Output: <button id="btn">Klik saya</button>
        ```

## DOM - Forms

`index.html`

```html
<body>
    <div class="container">
        <form id="sign-in">
            <h1>Sign In</h1>

            <div class="field">
                <label for="username">username</label>
                <input type="text" id="username" name="username" />
            </div>

            <div class="field">
                <label for="password">password</label>
                <input type="text" id="password" name="password" />
            </div>

            <button type="submit">login</button>
        </form>
    </div>
    <div class="another">
        <button id="submitNonForm">Login</button>
    </div>
</body>
```

> **Perlakuan DOM Form**:
>
> -   seleksi
> -   form handler
> -   event

**Seleksi:**

`script.js`

```javascript
let loginForm = getElementById("sign-in");
let inputUsername = getElementById("username");
let inputPassword = getElementById("password");
let buttonNonForm = getElementById("submitNonForm");
```

**Cara mengatasi Form:**

1. `addEventListener()` lewat element button itu sendiri

    > Event = `"click"`

    ```javascript
    buttonNonForm.addEventListener("click", () => {
        console.log(inputUsername.value);
        console.log(inputPassword.value);
    });
    ```

2. `addEventListener()` lewat tag form

    > Event = `"submit"`
    >
    > Agar saat di submit tidak mengalami refresh page, maka di tambahkan parameter (event) dan menambahkan kode `event.preventDefault()`

    ```javascript
    loginForm.addEventListener("submit", (event) => {
        event.preventDefault();
        console.log(inputUsername.value);
        console.log(inputPassword.value);
    });
    ```

**Membandingkan data yang sudah dideklarasikan :**

Jika ini melakukan perbandingan data bisa dimasukkan ke function dalam `addEventListener()`

> Kasus: Jika data user yang dideklarasikan hanya 1

```javascript
const dataUser = {
    username: "admin",
    password: "qwerty123",
};

let login = inputUsername.value === dataUser.username && inputPassword.value === dataUser.password;

if (login) {
    alert("selamat anda berhasil login");
} else {
    alert("username dan password anda salah");
}
```

> Kasus : Jika data user yang dideklarasikan lebih dari 1

```javascript
const listDataUser = [
    {
        username: "wadidaw",
        password: "asdfgh1234",
    },
    {
        username: "felli",
        password: "qwerty123",
    },
    {
        username: "irwansyah",
        password: "trewq4321",
    },
];

let isLoginTrue = false;

for (let i = 0; i <= listDataUser.length - 1; i++) {
    if (inputUsername.value === listDataUser[i].username && inputPassword.value === listDataUser[i].password) {
        isLoginTrue = true;
    }
}

if (isLoginTrue === true) {
    alert("selamat anda berhasil login");
} else {
    alert("username dan password anda salah");
}
```

**Menambahkan element lain jika melakukan sesuatu pada form :**

> Contoh kasus : menampilkan teks jika input username dan password salah (tidak sesuai data)

`index.html`

```html
<p id="alert-wrong" class="hidden">Username dan password salah!!</p>
```

`style.css`

```css
.hidden {
    display: none;
}
```

`script.js`

```javascript
let alertWrong = document.getElementById("alert-wrong");

if (login) {
    alert("selamat anda berhasil login");
} else {
    alertWrong.classList.remove("hidden");
}
```

> Pada kode di atas yang terjadi:
>
> 1. Jika `inputUsername` dan `inputPassword` benar maka tampilkan `alert`
> 2. Jika inputan salah, maka class `hidden` di tag `p` akan dihapus.
> 3. Sehingga styling dan class yang menggunakan class `hidden` akan terhapus.
> 4. Hasil akhir akan memunculkan tag `p` yang berisi tulisan `Username dan password salah!!`
