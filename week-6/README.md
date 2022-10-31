# Minggu 6 : 24 - 28 Oktober 2022

---

# Module 11 - React.js Dasar

> [React.js](https://reactjs.org/)

## Introducing

-   React JS dibuat oleh tim dari Facebook
-   React JS adalah framework view library javascript unutk membuat tampilan (user interface) pada website
-   React JS banyak digunakan karena
    -   Fast - membuat aplikasi front-end menjadi lebih cepat walaupun harus menghandle berbagai data
    -   Modular - dapat membagi 1 tampilan pada website menjadi komponen-komponen kecil
    -   Scalable - dapat digunakan pada aplikasi berskala kecil hingga besar dan kompleks
    -   Popular - banyak perusahaan yang menggunakan teknologi React JS, banyak komunitas sehingga banyak lowongan pekerjaan dan dokumentasi

## Membuat Project React JS

Berbagai cara bisa dilakukan untuk membuat project react JS

Package Manager yang berbeda:

> [create-react-app](https://create-react-app.dev/docs/getting-started/)

-   NPX
    ```bash
    npx create-react-app my-app
    cd my-app
    npm start
    ```
-   NPM
    ```bash
    npm init react-app my-app
    cd my-app
    npm start
    ```
-   Yarn
    ```bash
    yarn create react-app my-app
    cd my-app
    yarn start
    ```

Teknologi lain:

-   Vite
    > [Vite](https://vitejs.dev/guide/)
    ```bash
    npm create vite@latest my-react-app -- --template react
    cd my-create-app
    npm install
    npm run dev
    ```

## Melakukan Koding Dalam React

-   Perubahan dilakukan dalam file `src/App.js`

-   Menambah komponen baru: `src/components/`

## Virtual DOM

-   Untuk mengubah DOM asli, digunakanlah virtual DOM
-   Virtual DOM merupakan hasil salinan dari real DOM
-   real DOM merupakan struktur berupa tree (pohon).
-   Dengan penggunaan virtual DOM, update data yang dilakukan dan render ulang akan terjadi pada 1 komponen bukan render secara keseluruhan seperti real DOM.
-   Performa React JS dengan adanya virtual DOm membuat cepat dalam melakukan render dan update perubahan.

## JSX

-   JSX adalah syntax extension untuk javascript. JSX dikembangkan untuk digunakan pada React JS.
-   Dengan menggunakan JSX dapat menggunakan HTML di dalam extention Javascript (.js)
-   Peraturan dalam JSX:

    -   Setiap file JSX hanya bisa memiliki 1 parent element

        ```jsx
        function Navbar() {
            return (
                <>
                    <h1>Hello World</h1>
                </>
            );
        }

        // ATAU

        function Navbar() {
            return (
                <div>
                    <h1>Hello World</h1>
                </div>
            );
        }
        ```

    -   Penulisan nama function / class diawali dengan huruf kapital
        ```jsx
        function Navbar() {}
        function Card() {}
        ```

-   Hal lain mengenai JSX:
    -   Penulisan class sebagai atribut HTML pada JSX dituliskan dengan `className`
    -   Bisa menggunakan syntax Javascript di dalam element HTML dengan menggunakan tanda kurung kurawal `{}`
        > Jika tidak menggunakan tanda kurung kurawal maka akan dianggap teks HTML
    -   Variabel bisa diakses dalam HTML asalkan di dalam tanda kurung kurawal `{}`
    -   Bisa melakukan koding javascript dalam function komponen _(diluar return function)_

## Component

-   Salah satu core dari React JS
-   Component membagi UI dalam satuan-satuan kecil
-   Component dibuat jika component tersebut bersifat reusable code
-   Cara membuat Component:
    -   Menggunakan function
    -   Menggunakan class
-   Membuat component biasanya di direktori `src` dan membuat folder `components`
-   Untuk membuat component, nama folder, file dan function/class **harus diawali huruf kapital**
-   Cara memanggil component:
    -   Di dalam file component harus ada `export default <nama-function>`
    -   Di dalam `App.js` (file utama), menuliskan `import <nama-function> from "./components/<nama-file>"`
    -   Pemanggilan di dalam HTMLnya yaitu dengan single tag. `<nama-function />`

### Function Component VS Class Component

| Perbedaan  | Function Component                         | Class Component                         |
| ---------- | ------------------------------------------ | --------------------------------------- |
| Pengertian | Component yang dibuat menggunakan function | Component yang dibuat menggunakan class |

Syntax Funtion Component:

```jsx
const FunctionalComponent = ({ number = 10 }) => {
    return (
        <div>
            <p>Functional Component!</p>
            <p>State is {number}</p>
        </div>
    );
};

export default FunctionalComponent;
```

Syntax Class Component:

```jsx
import React, { Component } from "react";

class ClassComponent extends Components {
    state = { number: 0 };

    componentDidMount() {
        this.setState({ number: 10 });
    }

    render() {
        const { number } = this.state;
        return (
            <div>
                <p>Functional Component!</p>
                <p>State is {number}</p>
            </div>
        );
    }
}
```

## Styling

-   Untuk styling bisa dilakukan di external CSS (file.css) dan di dalam file jsx-nya di `import "nama-file.css"`
-   Cara inline yaitu dengan
    ```jsx
    <h1 style={{ backgroundColor: "black", width: "10px" }}></h1>
    ```
    -   penulisan atribut harus `style={ {kode css} }`
    -   penulisan properti menggunakan versi camelCase bukan versi css biasanya, akan tetapi nama properti tetap sama.

## Props & State

-   Props dan state adalah sebuah object yang digunakan untuk menyimpan informasi yang memengaruhi output render
-   Props diteruskan ke komponen (mirip parameter function)
    > Props digunaan agar component memiliki data yang dinamis yang dikirim dari component lain
-   State dikelola di dalam komponen (mirip dengan variabel yang di deklarasikan dalam suatu fungsi)
    > State merupakan data lokal
-   Stateless berarti component yang tidak memiliki state. Hanya memiliki props
-   Stateful berarti memiliki state dan bisa mengirim state tersebut ke component.
-   Penggunaan state yaitu dengan `import {useState} from "react"` dan pemanggilannya yaitu dengan `useState()`
-   Pada `useState` cara penulisannya seperti berikut
    ```jsx
    const [variabel, setVariabel] = useState();
    ```
    -   Pada `variabel` hanya bisa digunakan untuk di tampilkan
    -   Pada `setVariabel` hanya bisa digunakan untuk mengubah data/nilai variabel
    -   Isi dari method `useState` adalah nilai awal dari variabel tersebut dan bisa tipe data apa saja (number, string, bool, array, object, array of object)
-   Props di definisikan di parameter function component. Props bertipe data object.

**Contoh props dan state:**

`MemberInfo.jsx`

```jsx
// -------- Menggunakan propertinya langsung sebagai parameter --------------
const MemberInfo = ({ name, age, info, imgUrl, nameColor }) => {
    return (
        <div className="profile-container">
            <img src={imgUrl} alt="" className="profile-img" />
            <div className="profile-info">
                <h2 style={{ color: nameColor }}>{name}</h2>
                <h3>{age} Tahun</h3>
                <p>{info}</p>
            </div>
        </div>
    );
};

// -------------- Menggunakan props sebagai parameter ----------------------
// const MemberInfo = (props) => {
//     return (
//         <div className="profile-container">
//             <img src={props.imgUrl} alt="" className="profile-img" />
//             <div className="profile-info">
//                 <h2 style={{ color: props.nameColor }}>{props.name}</h2>
//                 <h3>{props.age} Tahun</h3>
//                 <p>{props.info}</p>
//             </div>
//         </div>
//     );
// };

export default MemberInfo;
```

`App.jsx`

```jsx
import MemberInfo from "./components/MemberInfo";

function App() {
    const [name, setName] = useState("dila");
    const [age, setAge] = useState(22);

    return (
        <>
            <MemberInfo name={name} age={age} info={"Peserta Bootcamp Frontend Skilvul"} imgUrl={"https://www.rd.com/wp-content/uploads/2017/09/01-shutterstock_476340928-Irina-Bg.jpg"} nameColor={"red"} />

            <br />
            <button onClick={() => setName("mika")}>change name</button>
            <button onClick={() => setAge(age + 1)}>change age</button>
        </>
    );
}

export default App;
```

## Handling Event

-   Menangani event dengan elemen React sangat mirip dengan menangani event pada elemen DOM.
-   Perbedaannya adalah:
    -   React event diberi nama menggunakan camelCase, bukan huruf kecil
    -   Dengan JSX, mengisinya dengan function sebagai event handler, bukan string
    -   Tidak bisa melakukan return `false`
    -   Tidak perlu melakukan `addEventListener` pada element
-   Penulisan function pada event bisa berupa function itu sendiri atau menggunakan callback

Contoh Penggunaan dan Perbedaan Event Handler pada HTML dan React:

**HTML**

```html
<button onclick="activateLasers()">Activate Lasers</button>
```

**React**

```jsx
<button onClick={activateLasers}>Activate Lasers</button>
```

**HTML**

```html
<form onsubmit="console.log('You clicked submit.'); return false">
    <button type="submit">Submit</button>
</form>
```

**React**

```jsx
function Form() {
    function handleSubmit(e) {
        e.preventDefault();
        console.log("You clicked submit.");
    }

    return (
        <form onSubmit={handleSubmit}>
            <button type="submit">Submit</button>
        </form>
    );
}
```

**Contoh handler event:**
**App.js**

```jsx
function App() {
    const handleClick = (name) => {
        console.log("tes dari " + name);

        return (
            <>
                <h2 onClick={() => handleClick("Felli")}>Alpha</h2>
            </>
        );
    };
}
```

> Hasil dari dari kode diatas adalah teks h2 yang bertuliskan Alpha
>
> Jika tulisan Alpha di klik maka di console muncul `tes dari Felli`

## Conditional Rendering

**Contoh penggunaan `map()` pada data:**

```jsx
function ListUser() {
    const [users, setUsers] = useState([
        { name: "Alpha", umur: 17 },
        { name: "Beta", umur: 18 },
        { name: "Charlie", umur: 19 },
        { name: "Delta", umur: 20 },
    ]);

    return (
        <div>
            {/* before */}
            <Card nama="Auzan" umur="17" />
            <Card nama="Zann" umur="18" />

            {/* after */}
            {/* solusi loop data array lalu di tampilkan */}
            {users.map((item, index) => (
                <Card key={index} nama={item.name} umur={item.umur} />
            ))}
        </div>
    );
}
```

**Contoh conditional:**

```jsx
function App() {
    const [isLogin, setIsLogin] = useState(false);

    return (
        <div>
            {/* munculin button klo belum login */}
            {!isLogin && <button onClick={() => setIsLogin(true)}>Login</button>}

            <br />

            {/* jika sudah login, munculkan counter  */}
            {isLogin ? <Counter /> : <span>login dulu cuuuy...</span>}

            {/* jika sudah login, munculkan ListUser  */}
            {isLogin && <ListUser />}
        </div>
    );
}
```

## Forms

**Contoh forms dan handlernya:**

```jsx
import { useState } from "react";
import axios from "axios";

const Form = () => {
    // -------- Di buat string kosong agar bisa di isi dan bisa di ubah------
    const [name, setName] = useState("");
    const [address, setAddress] = useState("");
    const [program, setProgram] = useState("");

    // Data digunakan agar inputan yang dimasukkan tidak berjalan real live tapi bisa jalan berdasarkan inputan yang masuk
    const [data, setData] = useState({});

    //   console.log(name, address);

    const handleSubmit = (e) => {
        // Agar tidak ke refresh
        e.preventDefault();

        // CARA SIMPAN DATA LEWAT LOKAL VARIABEL
        // setData({ name, address, program });
        // setName("");
        // setAddress("");
        // setProgram("");

        // proses post data menggunakan axios
        axios
            .post("http://localhost:3000/student", {
                name,
                address,
                program,
            })
            // Agar nilai dari name, address, program masuk kedalam variabel data
            .then(() => {
                setData({ name, address, program });
                setName("");
                setAddress("");
                setProgram("");
            })
            .catch((err) => {
                console.log(err);
            });
    };

    return (
        <>
            <form action="" onSubmit={handleSubmit}>
                <label htmlFor="name">Name</label>
                <input type="text" value={name} onChange={(e) => setName(e.target.value)} />
                <label htmlFor="address">Address</label>
                <input type="text" value={address} onChange={(e) => setAddress(e.target.value)} />
                <label htmlFor="option">Program</label>
                <select value={program} onChange={(e) => setProgram(e.target.value)}>
                    <option value="">select program</option>
                    <option value="KM">KM</option>
                    <option value="SIC">SIC</option>
                    <option value="Amman">Amman</option>
                </select>
                <button type="submit">Submit</button>
            </form>

            <br />
            <h2>Name: {data.name}</h2>
            <h2>Address: {data.address}</h2>
            <h2>Program: {data.program}</h2>
        </>
    );
};

export default Form;
```

-   Penulisan atribut `for` menjadi `htmlFor`
-   Harus diberikan `onChange={ () => ()}` agar perubahan bisa terjadi dan bisa disimpan ke dalam variabel
-   `event.target.value` digunakan untuk menangkap data yang dimasukkan

## Lifecycle method

-   Setiap life cycle, dapat menambahkan efek yang diperlukan (side effect)
-   Pada class component, terdapat 3 syntax yang digunakan untuk lifecycle yaitu `componentDidMount`, `componentDidUpdate`, `componentWillUnmount`
-   istilah mudahnya:
    -   mount = bangun
    -   update = makan
    -   unmount = tidur
-   Pada function component semua lifecycle menggunakan function `useEffect()` yang di import dari React (`import {useEffect} from "react"`)
-   Penulisan `useEffect()` :

    ```jsx
    // Jalan ketika terjadi update pada component, terjadi berkali-kali (mount, update)
    useEffect(() => {});

    // Agar jalan satu kali saja (mount)
    useEffect(() => {}, []);

    // Jalan saat variabel nameVar mengalami update
    useEffect(() => {}, [nameVar]);
    ```

## Library Install

-   Install axios untuk fetch

    ```
    npm i axios
    ```

    Cara penggunaan: `import axios from "axios"`

-   Install bootstrap react untuk styling
    ```
    npm i react-bootstrap bootstrap
    ```
    > [React Bootstrap](https://react-bootstrap.github.io/)

---

# Module 12 - React.js Lanjutan

## Hooks

-   Hook ada untuk mempermudah penggunaan functional components agar bisa melakukan state, dan lifecycle lainnya
-   Syntax-syntax yang digunakan di class component bisa digunakan di dalam functional components dengan menggunakan hooks
-   Contoh Hooks : `useState()`, `useEffect()`
    -   ##### useState
        -   Digunakan untuk mempermudah penggunaan setState (dari class component)
        ```jsx
        const [variabel, setVariabel] = useState(initialValue);
        ```
        -   Array nya hanya berupa 2 element
        -   variabel = value = React tetapkan nilai saat ini ke elemen pertama
        -   setVariabel = updater function = React tetapkan fungsi updater ke elemen kedua
        -   Initial value = berikan nilai awal ke useState hook
        -   Harus import dengan cara `import {useState} from "react"`
        -   Untuk memanggil variabelnya menggunakan `varibel` dan untuk update nilai menggunakan `setVariabel`
    -   ##### useEffect
        -   Digunakan untuk lifecycle pada functional component
        -   Penggunaan useEffect, bisa di masukkan sebelum melakukan render, biasanya ditempatkan di bawah useState
        -   Melakukan import dengan cara `import {useEffect} from "react"`
    -   Hooks lainnya seperti `useContext`, `useReducer`
        > [Hooks API Reference](https://reactjs.org/docs/hooks-reference.html)
