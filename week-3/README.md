# Minggu 3 : 3 - 7 Oktober 2022

---

# Module 8 - JS Intermediate - Array dan Multidimensional Array

## Array

> [MDN Dokumentasi Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

### Pengertian

-   Array adalah tipe data list order yang dapat menyimpan tipe data apapun di dalamnya.
-   Array dapat menyimpan tipe data String, Number, Boolean, dan lainnya.
-   Penulisan array menggunakan tanda kurung kotak `[]` dan isinya dipisahkan dengan tanda koma `,`

Contoh:

```javascript
// List judul Anime
// 1. Detective Conan
// 2. One Piece
// 3. Naruto

// Array
let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

// Beda tipe data
let randomData = ["Felli", 19, true];
```

### Mengakses Array

-   Data array dihitung menggunakan index dan dimulai dari **data ke-0**.
-   **Data pertama adalah index ke-0**

Contoh:

```javascript
let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

console.log(judulAnime[0]); // 'Detective Conan'
console.log(judulAnime[1]); // 'One Piece'
console.log(judulAnime[2]); // 'Naruto'
```

### Update Array

```javascript
let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

judulAnime[2] = "Sword Art Online";

console.log(judulAnime); // ["Detective Conan", "One Piece", "Sword Art Online"];
```

### Const in Array

-   Jika menggunakan let, kita dapat mengubah array dengan array baru dan konten nilai yang ada di dalam array dengan nilai lain
-   Const tidak bisa melakukan update data. Namun pada Array kita dapat melakukan update konten nilai di dalam array (mutable).
-   Yang tidak bisa adalah mengubah array dengan array yang baru jika menggunakan const

```javascript
const judulAnime = ["Detective Conan", "One Piece", "Naruto"];

// Mengubah array menjadi array baru
judulAnime = ["Sword Art Online"]; // Error

// Mengubah array menjadi string
judulAnime = "Sword Art Online"; // Error
```

### Properti Array

-   Array memiliki 5 properti yang sering digunakan yaitu constructor, length, index, input, dan prototype.
-   Properties adalah fitur yang sudah disediakan oleh Javascript untuk memudahkan developer.
-   Panjang Array

    Syntax:

    ```javascript
    arrayName.length;
    ```

    Contoh:

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    console.log(judulAnime.length); // 3
    ```

### Method Array

-   Array memiliki method atau biasa disebut built-in methods.
-   Artinya Javascript sudah memudahkan kita dengan menyediakan function/method umum yang bisa kita gunakan.

-   `push()`

    **Menambahkan** data di **akhir** array

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    judulAnime.push("Sword Art Online");
    console.log(judulAnime); // ["Detective Conan", "One Piece", "Naruto", "Sword Art Online"];
    ```

-   `unshift()`

    **Menambahkan** data pada **index pertama** array

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    judulAnime.unshift("Sword Art Online");
    console.log(judulAnime); // ["Sword Art Online", "Detective Conan", "One Piece", "Naruto"]
    ```

-   `pop()`

    **Menghapus** data di **akhir** array

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    judulAnime.pop();
    console.log(judulAnime); // ["Detective Conan", "One Piece"]
    ```

-   `shift()`

    **Menghapus** data di **index pertama** array

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    judulAnime.shift();
    console.log(judulAnime); // ["One Piece", "Naruto"]
    ```

-   `splice()`

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto", "Sword Art Online", "Kaito Kid"];

    /*
    0, "Detective Conan", 
    1, "One Piece", 
    2, "Naruto", 
    3, "Sword Art Online", 
    4, "Kaito Kid"
    */

    judulAnime.splice(2);
    /* Output:
    ["Detective Conan", "One Piece"];
    */

    judulAnime.splice(2, 1);
    /* Output:
    ["Detective Conan", "One Piece", "Sword Art Online", "Kaito Kid"];
    */

    judulAnime.splice(2, 1, "Fairy Tail");
    /* Output:
    ["Detective Conan", "One Piece", "Fairy Tail", "Sword Art Online", "Kaito Kid"];
    */

    judulAnime.splice(2, 0, "Fairy Tail");
    /* Output:
    ["Detective Conan", "One Piece", "Fairy Tail", "Naruto", "Sword Art Online", "Kaito Kid"];
    */
    ```

-   `slice()`

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto", "Sword Art Online", "Kaito Kid"];

    /*
    0, "Detective Conan", 
    1, "One Piece", 
    2, "Naruto", 
    3, "Sword Art Online", 
    4, "Kaito Kid"
    */

    // SLICE INDEX KE 2 DAN DIAKHIRI INDEX KE 3
    judulAnime.slice(2, 3);
    // ["Naruto"]

    judulAnime.slice(2, 4);
    // ["Naruto", "Sword Art Online"]

    judulAnime.slice(2);
    // ["Naruto", "Sword Art Online", "Kaito Kid"]
    ```

-   `sort()`

    Mengurutkan nilai array

    ```javascript
    const number = [3, 1, 5, 7, 2];

    number.sort();

    console.log(number);
    // [1,2,3,5,7]
    ```

### Array Loop

-   `for loop`

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto", "Sword Art Online", "Kaito Kid"];

    // ascending
    for (let i = 0; i < judulAnime.length - 1; i++) {
        console.log(judulAnime[i]);
    }
    // descending
    for (let i = judulAnime.length - 1; i >= 0; i--) {
        console.log(judulAnime[i]);
    }
    ```

-   `for of`

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto", "Sword Art Online", "Kaito Kid"];

    for (let anime of judulAnime) {
        console.log(anime);
    }
    ```

-   `forEach()`

    -   `forEach()` tidak bisa mengembalikan nilai

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto", "Sword Art Online", "Kaito Kid"];

    judulAnime.forEach((anime) => {
        console.log(anime);
    });

    judulAnime.forEach((anime, index) => {
        console.log(index, anime);
    });
    ```

-   `map()`

    -   `map()` bisa mengembalikan nilai (bisa menggunakan `return`)

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto", "Sword Art Online", "Kaito Kid"];

    judulAnime.map((anime) => {
        console.log(anime);
    });
    ```

## Multidimensional Array

### Pengertian

-   Multidimensional Array bisa dianalogikan dengan array of array.
-   Ada array didalam array.
-   Syntax:

    ```javascript
    let inventory = [
        ["Kaos", 10],
        ["Celana", 12],
        ["Jaket", 14],
        ["Topi", 9],
    ];

    console.log(inventory);
    /*
    0 : ["Kaos", 10]
    1 : ["Celana", 12]
    2 : ["Jaket", 14]
    3 : ["Topi", 9]
    */
    ```

### Mengakses Array

```javascript
let inventory = [
    ["Kaos", 10],
    ["Celana", 12],
    ["Jaket", 14],
    ["Topi", 9],
];

console.log(inventory[0][1]); // 10

console.log(inventory[2][0]); // Jaket

console.log(inventory[3]); // ["Topi", 9]
```

### Perulangan Array

```javascript
let inventory = [
    ["Kaos", 10],
    ["Celana", 12],
    ["Jaket", 14],
    ["Topi", 9],
];

// forEach()
inventory.forEach(baris){
    baris.forEach(kolom){
        console.log(kolom);
    }
}

// for loop
for (let i = 0; i <= inventory.length - 1; i++){
    for (let j = 0; i <= inventory[i].length - 1; j++){
        console.log(inventory[j]);
    }
}

/*Output:
Kaos
10
Celana
12
Jaket
14
Topi
9
*/
```

---

# Module 8 - JS Intermediate - Object

-   Object adalah sebuah tipe data pada variabel yang menyimpan properti dan fungsi (method)
-   Properti adalah data lengkap dari sebuah object.
-   Method adalah action dari sebuah object.

## Membuat Object

```javascript
let nama_obj = {
    property1: "value",
    property2: "value2",
};

let siswa = {
    nama: "terra",
    umur: 17,
    hobi: "memancing",
    nomorHandphone: 082367599,
};

console.log(siswa);
```

## Akses Object

-   Ada 2 cara yaitu **dot notation** dan **bracket**

```javascript
let siswa = {
    nama: "terra",
    umur: 17,
    hobi: "memancing",
    nomorHandphone: 082367599,
};

// dot notation
console.log(siswa.nama); // terra

// bracket
console.log(siswa[umur]); // 17

// menggunakan variabel
let properti = "umur";
console.log(siswa[properti]); // 17
```

## Menambah Property

-   Langsung menambahkan dengan membuat properti baru dan diisi dengan nilainya

```javascript
let buku = {
    judul: "mantan jadi manten",
    penulis: "hayati",
    jumlahHalaman: 250,
};

buku.tahun = 2022;
buku.terjual = 3000;
console.log(buku);
/*
{
    judul: "mantan jadi manten",
    penulis: "hayati",
    jumlahHalaman: 250,
    tahun : 2022,
    tejual: 3000
};
*/

buku["penerbit"] = "gramedia";
console.log(buku);
/*
{
    judul: "mantan jadi manten",
    penulis: "hayati",
    jumlahHalaman: 250,
    tahun : 2022,
    tejual: 3000,
    penerbit: "gramedia"
};
*/
```

## Update Object

-   Menggunakan tanda assign `=`

```javascript
let hewan = {
    nama: "kucing",
    kaki: 4,
    warna: "putih",
};

hewan.nama = "kelinci";
hewan.warna = "kuning";
console.log(hewan);
/*
{
    nama: "kelinci",
    kaki: 4,
    warna: "kuning",
}
*/

// JIKA MENGGUNAKAN CONST
const bunga = {
    nama: "Lily",
};
bunga.nama = "melati";
console.log(bunga);
// {nama: "melati"}
```

## Delete Object

-   Menggunakan keyword `delete`

```javascript
let hewan = {
    nama: "kucing",
    kaki: 4,
    warna: "putih",
};

delete hewan.kaki;
console.log(hewan);
/*
{
  nama: "kucing",
  warna: "putih"
};
*/
```

## Method

-   Method adalah function yang terdapat di dalam object

```javascript
const greeting = {
    welcome: function () {
        return "halo selamat datang";
    },
    afterPay: function () {
        return "Terimakasih sudah membeli produk kami";
    },
};

// Method welcome()
console.log(greeting.welcome());
// Output: halo selamat datang

// Method afterPay()
console.log(greeting.afterPay());
// Output: Terimakasih sudah membeli produk kami

let siswa = {
    nama: "dila",
    umur: 17,
    hobi: "membaca",
};

console.log(siswa);
// [nama, umur, hobi]

// Method keys()
console.log(Object.keys(siswa));
// Output: {"nama", "umur", "hobi"}

// Method values()
console.log(Object.values(siswa));
// Output: {'dila', 17, "membaca"}
```

## Nested Object

```javascript
let buku = {
    judul: "tips jago javascript",
    tahun: 2022,
    penulis: {
        penulis1: {
            nama: "Reyhan",
            umur: 28,
            kota: "jakarta",
        },
        penulis2: {
            nama: "aby",
            umur: 25,
            kota: "bandung",
        },
    },
};

console.log(buku.penulis.penulis1.nama);
// Output: Reyhan

console.log(buku.penulis.penulis2.umur);
// Output: 25
```

## Looping

-   Looping khusus untuk object yaitu `for in`

```javascript
let siswa = {
    nama: "Reyhan",
    umur: 22,
    asal: "jakarta",
    hobi: "membaca",
};

for (let key in siswa) {
    console.log(key);
}
/* Output: 
nama
umur
asal
hobi
*/

for (let key in siswa) {
    console.log(siswa[key]);
}
/* Output: 
Reyhan
22
jakarta
membaca
*/

let buku = {
    judul: "tips jago javascript",
    tahun: 2022,
    penulis: {
        penulis1: {
            nama: "Reyhan",
            umur: 28,
            kota: "jakarta",
        },
        penulis2: {
            nama: "aby",
            umur: 25,
            kota: "bandung",
        },
    },
};

for (let key in buku.penulis.penulis1) {
    console.log(buku.penulis.penulis1[key], "----ini dari nested");
}
/* Output:
Reyhan ----ini dari nested
28 '----ini dari nested'
jakarta ----ini dari nested
*/
```

## Array of Object

-   Object berada di dalam Array

```javascript
let users = [
    {
        nama: "dila",
        umur: 17,
        alamat: "bandung",
    },

    {
        nama: "audzan",
        umur: 18,
        alamat: "jakarta",
    },
    {
        nama: "dolton",
        umur: 16,
        alamat: "sulawesi",
    },
];

console.log(users);

// Menambahkan property baru menggunakan map
let data = users.map((el) => {
    el.status = "aktif";
    return el;
});

console.log(data);
/* Ouput:
[
    {
        nama: 'dila', 
        umur: 17, 
        alamat: 'bandung', 
        status: 'aktif'
    },
    {
        nama: 'audzan', 
        umur: 18, 
        alamat: 'jakarta', 
        status: 'aktif'
    },
    {
        nama: 'dolton', 
        umur: 16, 
        alamat: 'sulawesi', 
        status: 'aktif'
    }
]
*/
```

---

# Module 8 - JS Intermediate - Rekursif

## Module

-   JS Modules adalah cara untuk memisahkan kode ke file yang berbeda
-   Keuntungan:

    -   Mudah untuk mengelola kode
    -   Kode tidak menumpuk di 1 file

-   Penggunaan Module:

    1. Tambahkan `type="module"` pada script utama
    2. Siapkan script ke-2, dst untuk melakukan export
    3. Lakukan import pada file/script utama

-   Peraturan Pengaksesan Menggunakan Export dan Import

    -   file yang di urutan atas tidak dapat di akses oleh yang di bawah
    -   file yang di bawah dapat diakses oleh yang di atas

Contoh:

```html
<!-- DI HTML -->
<!-- SCRIPT UTAMA -->
<script src="./indonesia.js" type="module"></script>

<!-- SCRIPT TAMBAHAN -->
<!-- 
    <script src="./jepang.js" type="module"></script>
    <script src="./amerika.js" type="module"></script> 
-->
```

-   `export`

    -   Menggunakan keyword `export`
    -   Dapat melakukan export pada variabel, function, class
    -   `export` dapat melakukan banyak export
    -   `export` di tangkap (import) menggunakan kurung kurawal
    -   `export default` cuma bisa 1 aja yg di export
    -   `export default` ditangkap tanpa kurung kurawal

    Contoh:

    ```javascript
    let motor = ["suzuki", "yamaha", "honda", "kawasaki"];

    const smartPhone = ["sony", "samsung", "fujitsu", "LG"];

    let entertainment = ["anime", "manga", "wibu", "dorama"];

    // Cara export langsung di variabel / function
    export function sayHello() {
        console.log("hallooo");
    }

    // Membuat export di banyak variabel
    export { motor, smartPhone };

    // Membuat export dan sekaligus mengganti nama variabel
    // Menggunakan keyword as
    export { motor, smartPhone as smartPhoneJepang };

    // export default
    export default entertainment;
    ```

-   `import`

    -   menggunakan keyword `import` dan `from`
    -   variabel yang di export di tulis di dalam kurung kurawal `{}`

    Contoh:

    ```javascript
    import Entertainment, { motor as motorJepang, smartPhoneJepang, sayHello } from "./jepang.js";
    ```

    Keterangan:

    -   `Entertaiment` => sebagai export default
    -   `motor as motorJepang` => variabel `motor` akan diganti namanya menjadi `motorJepang` di file ini
    -   `smartPhoneJepang` => nama variabel yang sudah dideklarasikan di file jepang.js
    -   `from "./jepang.js"` => merupakan lokasi dari file import

## Rekursif

-   Rekursif adalah function yang memanggil dirinya sendiri sampai kondisi tertentu.
-   Biasanya digunakan untuk persoalan matematika
-   Function rekursif punya 2 case:
    -   **Base case** -> titik paling kecil (berhenti)
    -   **Recursion case** -> titik memanggil fungsi itu sendiri

Contoh:

```javascript
// menampilkan deret angka 1 2 3 4 5

function deretAngka(n) {
    if (n == 1) {
        console.log(n);
    } else {
        deretAngka(n - 1);
        console.log(n);
    }
}

deretAngka(5); // 1 2 3 4 5

// Menghitung faktorial
// 3! = 3 x 2 x 1

function faktorial(n) {
    if (n == 1) {
        return 1;
    } else {
        return n * faktorial(n - 1);
    }
}
console.log(faktorial(3)); // 6

// loop vs rekursif
function faktorialFor(n) {
    let hasil = 1;
    for (let i = n; i >= 1; i--) {
        hasil = hasil * i;
        console.log(`${i} -- ini hasil i`);
    }
    return hasil;
}

console.log(faktorialFor(3));
/*Output:
3 -- ini hasil i
2 -- ini hasil i
1 -- ini hasil i
6
*/
```

---

# Module 8 - JS Intermediate - Asynchronous

## Pengertian

## Callback

## Promise

## Async await

---

# Module 8 - JS Intermediate - Web Storage

-   Ada beberapa cara untuk menyimpan data pengguna seperti pencarian, artikel berita, dan lain-lain ke lokal (browser) menggunakan web storage seperti cookies, local storage, dan session storage.
-   Cookies adalah data kecil yang dikirim dari situs web dan disimpan di komputer kita oleh web browser saat kita menjelajah.
-   Kekurangan cookies:

    -   Setiap mengakses situs web, cookies juga kembali dikirim sehingga memperlambat aplikasi web dengan mengirimkan data yang sama.
    -   Cookies disertakan pada setiap HTTP request, sehingga mengirimkan data yang tidak dienkripsi melalui internet, maka saat ingin menyimpan data dalam cookies harus mengenkripsinya terlebih dahulu.
    -   Cookies hanya dapat menyimpan data sebanyak 4KB.
    -   Lalu cookies juga memiliki tanggal kadaluarsa.

-   Web storage digunakan untuk preferensi user, setting, score, posisi video
-   Web storage jangan digunakan untuk data sensitif (username, password), otentikasi
-   Karakteristik web storage:

    -   Menyimpan data tanpa tanggal kadaluarsa.
    -   Data tidak akan dihapus ketika web browser ditutup dan akan tersedia seterusnya selama tidak menghapus data local storage pada web browser.
    -   Dapat menyimpan data hingga 5MB.
    -   Hanya dapat menyimpan data string.

-   Menyimpan data pada local storage, menggunakan method `setItem()` yang membutuhkan 2 parameter.

    -   Parameter pertama adalah key yang ingin kita simpan
    -   Parameter kedua adalah data (value) dari key yang akan disimpan.

```javascript
localStorage.setItem("key", value);
```

Contoh:

`index.html`

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
        <style>
            body {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
            }

            form {
                display: flex;
                flex-direction: row;
            }

            form input {
                padding: 5px 10px;
            }
        </style>
    </head>
    <body>
        <form>
            <input type="text" id="searchkey" name="searchkey" placeholder="Search Something" /><br />
            <input type="submit" value="Search" onclick="onSearch()" />
        </form>
        <script></script>
    </body>
</html>
```

`script`

```html
<script>
    let searchList = [];
    function onSearch() {
        let searchValue = document.getElementById("searchkey").value;
        searchList.push(searchValue);
        // memasukkan kata pencarian ke dalam array
        // agar kata yang dicari bisa disimpan sebanyak mungkin

        let searchListString = JSON.stringify(searchList);
        // mengubah array menjadi string
        // karna local storage hanya menyimpan data berupa string

        localStorage.setItem("searchKey", searchListString);
        // menyimpan pencarian dengan key 'searchKey'
    }
</script>
```
