# Minggu 3 : 3 - 7 Oktober 2022

---

# Module 8 - JS Intermediate - Array dan Multidimensional Array

## Array

> [MDN Dokumentasi Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

### Pengertian

Array adalah tipe data list order yang dapat menyimpan tipe data apapun di dalamnya.

Array dapat menyimpan tipe data String, Number, Boolean, dan lainnya.

Penulisan array menggunakan tanda kurung kotak `[]` dan isinya dipisahkan dengan tanda koma `,`

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

Data array dihitung menggunakan index dan dimulai dari **data ke-0**.

Data pertama adalah index ke-0

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

Jika menggunakan let, kita dapat mengubah array dengan array baru dan konten nilai yang ada di dalam array dengan nilai lain

Const tidak bisa melakukan update data. Namun pada Array kita dapat melakukan update konten nilai di dalam array (mutable).

Yang tidak bisa adalah mengubah array dengan array yang baru jika menggunakan const

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

    Menambahkan data pada index pertama array

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    judulAnime.unshift("Sword Art Online");
    console.log(judulAnime); // ["Sword Art Online", "Detective Conan", "One Piece", "Naruto"]
    ```

-   `pop()`

    Menghapus data di akhir array

    ```javascript
    let judulAnime = ["Detective Conan", "One Piece", "Naruto"];

    judulAnime.pop();
    console.log(judulAnime); // ["Detective Conan", "One Piece"]
    ```

-   `shift()`

    Menghapus data di index pertama array

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
    Mengurutkan secara ascending

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

    `forEach()` tidak bisa mengembalikan nilai

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

    `map()` bisa mengembalikan nilai (bisa menggunakan `return`)

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

Ada 2 cara yaitu **dot notation** dan **bracket**

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

Langsung menambahkan dengan membuat properti baru dan diisi dengan nilainya

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

menggunakan tanda assign `=`

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

menggunakan keyword `delete`

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

Method adalah function yang terdapat di dalam object

## Nested Object

## Pass by reference

## Looping

## Array of Object

---

# Module 8 - JS Intermediate - Rekursif

## Module

-   export
-   import

## Rekursif

---

# Module 8 - JS Intermediate - Asynchronous

## Pengertian

## Callback

## Promise

## Async await

---

# Module 8 - JS Intermediate - Web Storage

Contoh:

```

```
