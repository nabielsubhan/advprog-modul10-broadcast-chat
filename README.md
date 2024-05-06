## Nama   : Muhammad Nabiel Subhan
## NPM    : 2206081553
## Kelas  : AdPro B

###  2.1. Original code of broadcast chat.

<p align="center">
  <img src="images\test.png" />
</p>

Untuk mencoba menjalankan program ini, kita bisa menjalankan `cargo run --bin server` untuk menjalankan server, lalu membuka terminal lain sebanyak 3 terminal dan menjalankan `cargo run --bin client` pada masing-masing terminal untuk menjalankan total 3 buah client. Cara kerja dari program ini adalah ketika kita mencoba mengetik suatu pesan dari salah satu client, maka server akan menybarkan pesan tersebut ke semua client yang ada sehingga tiap client bisa mengetahui pesan apa yang dibuat oleh client lainnya.

###  2.2. Modifying the websocket port

<p align="center">
  <img src="images\test2.png" />
</p>

Untuk mengubah port menjadi 8080, kita perlu mengubah sedikit pada file `server.rs` dan `client.rs`. Pada `client.rs`, kita perlu mengubah bagian `ClientBuilder::from_uri(Uri::from_static("ws://127.0.0.1:2000"))` menjadi `ClientBuilder::from_uri(Uri::from_static("ws://127.0.0.1:8080"))`. Untuk `server.rs` kita juga perlu mengubah bagian ketika server ingin melakukan bind ke port yang akan di-listen, yaitu pada bagian `let listener = TcpListener::bind("127.0.0.1:2000").await?;` kita ubah menjadi `let listener = TcpListener::bind("127.0.0.1:8080").await?;`. Server juga menggunakan websocket protocol yang sama dengan client, hal ini dapat dilihat dari penggunaan `WebSocketStream` dari library `tokio_websockets`.