# Minggu 7 : 31 Oktober - 4 November 2022

---

# Module 12 - React.js Lanjutan

## Proptypes

-   Prop types merupakan sebuah library yang dapat membantu kamu untuk memeriksa data props yang kamu kirim agar sesuai dengan ekspetasi. Jika tidak sesuai maka akan muncul pesan error
-   **Install prop types**

    ```bash
    npm install prop-types
    ```

-   **Import Prop types**

    ```jsx
    import PropTypes from "prop-types";
    ```

-   **Pemanggilan proptypes**
    ```jsx
    function.propTypes = {
        property = PropTypes.typeData
    }
    ```
-   **Contoh penggunaan Proptypes**

    -   **Biasa**

        ```jsx
        import PropTypes from "prop-types";

        const StudentInfo = ({ name, age }) => {
            return (
                <>
                    <h2>{name}</h2>
                    <h2>{age + 5}</h2>
                </>
            );
        };
        StudentInfo.propTypes = {
            // type data string
            name: PropTypes.string,
            // type data number
            age: PropTypes.number,
        };

        export default StudentInfo;
        ```

    -   **Tipe data bebas**

        ```jsx
        name: PropTypes.any,
        ```

    -   **Wajib di isi**

        ```jsx
        name: PropTypes.any.isRequired;
        ```

    -   **Memberikan opsi untuk type data**

        ```jsx
        age: PropTypes.oneOfType([PropTypes.string, PropTypes.number]);
        ```

    -   **Tipe data array**

        ```jsx
        data: PropTypes.array,
        ```

    -   **Mengecek value array dari props**

        ```jsx
        data: PropTypes.arrayOf(PropTypes.number),
        ```

    -   **Array dengan berbagai type data**

        ```jsx
        data: PropTypes.arrayOf(PropTypes.oneOfType([PropTypes.number, PropTypes.string])),
        ```

    -   **Type data object**

        ```jsx
        info: PropTypes.object,
        ```

    -   **Mengecek nilai dari object**

        ```jsx
        info: PropTypes.shape({
            hobby: PropTypes.string,
            class: PropTypes.number,
        }),
        ```

    -   **Mengecek nilai dan key dari object**
        > value dan property harus sama, tidak boleh ada tambahan
        ```jsx
        info: PropTypes.exact({
            hobby: PropTypes.string,
            class: PropTypes.number,
        }).isRequired;
        // tamabahan agar wajib
        ```

---

# Module 13 - React Router 6

> [React Router Website](https://reactrouter.com/)
>
> [React Router Website v6.3.0](https://reactrouter.com/en/v6.3.0/)

-   **Install react router**
    ```bash
    npm install react-router-dom@6
    ```
-   **Langkah-langkah:**

    1.  Import `BrowserRouter` di `main.js`

        ```jsx
        import { BrowserRouter } from "react-router-dom";

        ReactDOM.render(
            <BrowserRouter>
                <App />
            </BrowserRouter>,
            document.getElementById("root")
        );
        ```

    2.  Import `Routes`, `Route`, `Link` di `App.js`
        ```jsx
        import { Routes, Route, Link } from "react-router-dom";
        ```

-   **Penggunaan Routers**

    ```jsx
    <Routes>
        <Router></Router>
    </Routes>
    ```

-   **Penulisan Router**

    ```jsx
    <Router path="/" element={<HomePage />}></Router>
    ```

-   **Penulisan Path**

    -   Utama -> `path="/"`
    -   Halaman lain -> `path="/namaHalaman"`
    -   Halaman dengan id -> `path="/namaHalaman/:id"`
    -   Halaman not found -> `path="*"`

-   **Penulisan Link**

    ```jsx
    <Link to={"/"}>Home</Link>
    ```

-   **Membuat URL agar sesuai dengan id**

    > Menggunakan `useNavigate()`

    ```jsx
    import { useNavigate, Link } from "react-router-dom";

    const HomePage = () => {
        // panggil useNavigate agar bisa digunakan pada function handleDetail
        const navigation = useNavigate();
        let data = [
            {
                id: 1,
                name: "Mika",
            },
            {
                id: 2,
                name: "Reyhan",
            },
            {
                id: 3,
                name: "Asep",
            },
        ];

        const handleDetail = (id) => {
            // untuk pindah halaman ke page detail sekaligus membawa id params
            navigation(`/detail/${id}`);
            // variabel id harus sama dengan variabel yang ada di router App.js
            // url juga harus sama dengan router di App.js
        };

        return (
            <>
                <h1>Ini Home Page</h1>
                {data.map((el) => {
                    return (
                        <div key={el.id}>
                            <h2>Nama: {el.name}</h2>
                            <button onClick={() => handleDetail(el.id)}>Detail</button>
                        </div>
                    );
                })}
            </>
        );
    };

    export default HomePage;
    ```

-   **Menampilkan data sesuai id yang di klik**

    > Menggunakan `useParams`

    ```jsx
    import { useParams } from "react-router-dom";

    const DetailPage = () => {
        // useParams untuk menangkap id yang kita kirim dari halaman home
        const { id } = useParams();
        console.log(id);

        const detailInfo = [
            {
                id: 1,
                name: "Mika",
                address: "jakarta",
                hobby: "menari",
            },
            {
                id: 2,
                name: "Reyhan",
                address: "bandung",
                hobby: "memancing",
            },
            {
                id: 3,
                name: "Asep",
                address: "malang",
                hobby: "membaca",
            },
        ];
        // ide:
        // 1. filter data dari detailInfo dan dicocokkan dengan id yg kita kirim dari home (yg ditangkap di params)
        // 2. Mapping data untuk menampilkan hasil yang sesuai dari data filter
        return (
            <>
                {detailInfo
                    .filter((el) => el.id === +id)
                    .map((el) => {
                        return (
                            <div key={el.id}>
                                <h2>Name: {el.name}</h2>
                                <h2>Address: {el.address}</h2>
                                <h2>Hobby: {el.hobby}</h2>
                            </div>
                        );
                    })}
            </>
        );
    };

    export default DetailPage;
    ```

-   **Nested Router**

    Dibungkus oleh `<Router>`

    Penulisan path untuk childnya tidak perlu garis miring (/)

    ```jsx
    <Route path="/about" element={<AboutPage />}>
        <Route path="student" element={<AboutStudent />} />
        <Route path="teacher" element={<AboutTeacher />} />
        {/* index digunakan agar element AboutSchool langsung ditampilkan pertama kali ketika page about dibuka */}
        <Route index element={<AboutSchool />} />
    </Route>
    ```

    > Hasil path kodingan di bawah adalah :
    >
    > > `/about/student` untuk halaman Student
    > >
    > > `/about/teacher` untuk halaman Teacher
    >
    > Penambahan atribut `index` menjadikan default dari path `/about`

    Untuk halaman `AboutPage.jsx` nya

    > Gunakan `<Outlet />` untuk membawa nested route tadi

    ```jsx
    import { Outlet, Link } from "react-router-dom";

    const AboutPage = () => {
        return (
            <>
                <Outlet />
                <Link to={"student"}>About Student |</Link>
                <Link to={"teacher"}>About Teacher</Link>
            </>
        );
    };

    export default AboutPage;
    ```

-   Ingin memanggil nested router tanpa harus ke induk dulu

    > Penulisan `to` langsung full dengan nama pathnya

    ```jsx
    const HomePage = () => {
        return (
            <>
                <Link to={"about/student"}>About Student |</Link>
                <Link to={"about/teacher"}>About Teacher</Link>
            </>
        );
    };
    ```

---

# Module 14 - State Management - React Redux & React Thunk

[Redux](https://redux.js.org/)

[React Redux](https://react-redux.js.org/)

-   Install package
    ```bash
    npm install redux react-redux
    ```

## React Redux

-   Redux membantu perubahan yang terjadi di component atau halaman lain agar sama tanpa harus membuat setState di setiap halaman

-   Istilah" dari redux = action, store, reducer

-   Buatlah folder khusus untuk redux dengan berisi masing" folder kegiatan (action, reducer, store)

-   Cara membuat redux:

    1. Membuat store
    2. Membuat reducer
    3. Menambahkan provider
    4. Ambil data dari store menggunakan `useSelector`
    5. Ubah data store menggunakan `useDispatch(action)`

-   **Membuat Store**

    `redux/store/index.js`

    ```javascript
    import { createStore } from "redux";

    const store = createStore(() => {});

    export default store;
    ```

-   **Membuat Reducer**

    `redux/reducer/keranjangReducer.js`

    ```javascript
    // membuat nilai awal
    const initialState = {
        totalKeranjang = 0
    }

    function keranjangReducer(state = initialState, action){
        switch(action.type){
            case:
            // kode
            default:
                return state
        }
    }

    export default keranjangReducer
    ```

-   **Menyambungkan store dengan reducer**

    `store/index.js`

    ```javascript
    import { createStore } from "redux";
    import keranjangReducer from "../reducer/keranjangReducer";

    const store = createStore(keranjangReducer);

    export default store;
    ```

-   **Menambahkan `<Provider/>` di dalam `main.js`**

    ```jsx
    import { Provider } from "react-redux";
    import store from "./redux/store";

    ReactDOM.createRoot(document.getElementById("root")).render(
        <React.StrictMode>
            <Provider store={store}>
                <App />
            </Provider>
        </React.StrictMode>
    );
    ```

-   **Menggunakan `useSelector` pada component yang datanya mengikuti dari tombol" awalnya**

    ```jsx
    import React from "react";
    import { useSelector } from "react-redux";

    function Keranjang() {
        const state = useSelector((state) => state);

        // console.log(state)
        // Hasil nya adalah {totalKeranjang = 0}
        // Hasil dari initialState

        // Cara agar langsung ambil value dari property totalKeranjang
        const { totalKeranjang } = useSelector((state) => state);

        return (
            <div>
                <span>Keranjang</span>
                <span> {totalKeranjang}</span>
            </div>
        );
    }

    export default Keranjang;
    ```

-   **Membuat action**

    `redux/action/keranjangAction.js`

    ```javascript
    // akan di import ke reducer
    export const INCREMENT_KERANJANG = "INCREMENT_KERANJANG";
    export const DECREMENT_KERANJANG = "DECREMENT_KERANJANG";

    // akan di import ke file component
    export function incrementKeranjang() {
        console.log("action dipanggil");
        return {
            type: INCREMENT_KERANJANG,
        };
    }

    export function decrementKeranjang() {
        return {
            type: DECREMENT_KERANJANG,
        };
    }
    ```

-   **Panggil action di reducer**

    `redux/reducer/keranjangReducer.js`

    ```javascript
    // variabelnya digunakan untuk switch case
    import { INCREMENT_KERANJANG, DECREMENT_KERANJANG } from "../action/keranjangAction"

    // membuat nilai awal
    const initialState = {
        totalKeranjang = 0
    }

    function keranjangReducer(state = initialState, action){
        switch(action.type){
            case INCREMENT_KERANJANG:
                state = {
                    totalKeranjang: state.totalKeranjang + 1
                }
                return state
            case DECREMENT_KERANJANG:
                state = {
                    totalKeranjang: state.totalKeranjang - 1
                }
                return state
            default:
                return state
        }
    }

    export default keranjangReducer
    ```

-   **Membuat event untuk component tombol"nya yang melakukan perubahan menggunakan `useDispatch`**

    ```jsx
    import React, { useState } from "react";
    import { useDispatch } from "react-redux";

    import { incrementKeranjang, decrementKeranjang } from "../redux/action/keranjangAction";

    function Counter() {
        const dispatch = useDispatch();
        const [count, setCount] = useState(0);

        const increment = () => {
            // dispatch( () => {} )
            // function berada di file lain
            dispatch(incrementKeranjang());
            setCount(count + 1);
        };

        const decrement = () => {
            // function langsung di set di dalam dispatch
            dispatch({
                type: "DECREMENT_KERANJANG",
            });
            setCount(count - 1);
        };

        return (
            <>
                <button onClick={decrement}>-</button>
                <span>{count}</span>
                <button onClick={increment}>+</button>
            </>
        );
    }

    export default Counter;
    ```

-   Store hanya dibuat 1 kali dan reducernya akan di simpan ke dalam `combineReducers`

-   **Membuat reducer lebih dari 1**

    `action/index.js`

    ```javascript
    import { combineReducers, createStore } from "redux";
    import counterReducer from "../reducer/counterReducer";
    import todoReducer from "../reducer/todoReducer";

    const allReducer = combineReducers({
        counter: counterReducer,
        todo: todoReducer,
    });

    const store = createStore(allReducer);

    export default store;
    ```

    Ketika melakukan `const state = useSelector(state => state)`, maka hasil consolenya adalah

    ```
    {
        counter: {count: 0},
        todo: {data: []},
    }
    ```

-   **Menambahkan data berdasarkan inputan**

    `action/todoAction.js`

    ```javascript
    export const ADD_TODO = "ADD_TODO";

    export function addTodo(todo) {
        console.log(todo, "dari action");
        return {
            type: ADD_TODO,
            payload: todo,
        };
    }
    ```

    `reducer/todoReducer.js`

    ```javascript
    import { ADD_TODO } from "../action/todoAction";

    const initialState = {
        data: ["belajar redux", "redux itu gampng"],
    };

    function todoReducer(state = initialState, action) {
        switch (action.type) {
            case ADD_TODO:
                console.log(action.payload);

                return {
                    data: [...state.data, action.payload],
                };

            default:
                return state;
        }
    }

    export default todoReducer;
    ```

    `components/TodoList.jsx`

    ```jsx
    import React, { useState } from "react";
    import { useDispatch, useSelector } from "react-redux";
    import { addTodo } from "../redux/action/todoAction";

    function TodoList() {
        const dispatch = useDispatch();
        const [inputTodo, setInputTodo] = useState("");
        const todos = useSelector((state) => state.todo.data);

        const handleSubmit = (e) => {
            e.preventDefault();

            console.log(inputTodo, "dari event");
            dispatch(addTodo(inputTodo));
        };

        const handleChange = (e) => {
            setInputTodo(e.target.value);
        };

        return (
            <div>
                <form onSubmit={handleSubmit}>
                    <h2>Todo List</h2>
                    <input type="text" name="inputTodo" value={inputTodo} onChange={handleChange} />
                    <button>add</button>
                </form>
                // Menampilkan hasil dari masukkan / inputan
                <ul>
                    {todos.map((item, index) => (
                        <li key={index}>{item}</li>
                    ))}
                </ul>
            </div>
        );
    }

    export default TodoList;
    ```

## React Redux Thunk

[Redux Thunk](https://redux.js.org/tutorials/fundamentals/part-6-async-logic)

-   Action tidak bisa melakukan asynchronous, maka dari itu diperlukan tambahan yaitu Function middleware berupa thunk
-   Install package

    ```bash
    npm install redux-thunk
    ```

-   **tambahkan import `applyMiddleware` dan `thunk` di `action/index.js`**

    ```javascript
    import { createStore, combineReducers, applyMiddleware } from "redux";
    import thunk from "redux-thunk";
    import todoReducer from "../reducer/todoReducer";

    const allReducer = combineReducers({
        todo: todoReducer,
        // user: userReducer,
        // product: productReducer
    });

    const store = createStore(allReducer, applyMiddleware(thunk));

    export default store;
    ```

-   **Buat reducer**

    ```javascript
    import { FETCH_START, SUCCESS_GET_TODO } from "../action/todoAction";

    const initialState = {
        todos: [],
        isLoading: false,
        err: null,
    };

    const todoReducer = (state = initialState, action) => {
        switch (action.type) {
            case FETCH_START:
                return {
                    ...state,
                    isLoading: true,
                };
            case SUCCESS_GET_TODO:
                return {
                    ...state,
                    todos: action.payload,
                    isLoading: false,
                };
            default:
                return state;
        }
    };

    export default todoReducer;
    ```

-   **Buat Action**

    ```javascript
    import axios from "axios";

    export const GET_TODO = "GET_TODO";
    export const FETCH_START = "FETCH_START";
    export const SUCCESS_GET_TODO = "SUCCESS_GET_TODO";

    function fetchStart() {
        return {
            type: FETCH_START,
        };
    }

    function successGetTodo(data) {
        return {
            type: SUCCESS_GET_TODO,
            payload: data,
        };
    }

    // ====================== MENGGUNAKAN PROMISE ===============

    export const getTodo = () => {
        return async (dispatch) => {
            // ubah loading jadi true
            dispatch(fetchStart());

            // axios -> isi data todos, loading jadi false
            const result = await axios.get("https://63478a450484786c6e82998f.mockapi.io/todo");
            dispatch(successGetTodo(result.data));
        };
    };

    // =========== MENGGUNAKAN CARA ASYNC AWAIT =================
    export const addTodo = () => async (dispatch) => {
        //   // ubah loading jadi true
        dispatch(fetchStart());

        // axios -> isi data todos, loading jadi false
        const result = await axios.post("https://63478a450484786c6e82998f.mockapi.io/todo", { todo: "thunk itu mudah" });
        dispatch(successGetTodo(result.data));
    };
    ```

-   **Buat Komponen**

    ```jsx
    import React, { useEffect } from "react";
    import { useDispatch, useSelector } from "react-redux";
    import { getTodo } from "../redux/action/todoAction";

    function TodoList() {
        const dispatch = useDispatch();
        const { todos, isLoading } = useSelector((state) => state.todo);

        useEffect(() => {
            dispatch(getTodo());
        }, []);

        return (
            <div>
                <h2>Todo List</h2>

                <ul>{isLoading ? <span>Loading...</span> : todos.map((item) => <li key={item.id}>{item.todo}</li>)};</ul>
            </div>
        );
    }

    /*
    <ul>
        {isLoading ? (
            <span>Loading...</span>
        ): (
            todos.map((item) => <li key={item.id}>{item.todo}</li>)
        )};
    </ul>
    */
    export default TodoList;
    ```
