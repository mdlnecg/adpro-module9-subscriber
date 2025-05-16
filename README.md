# Tutorial 9 Pemrograman Lanjut: Subscriber
### Madeline Clairine Gultom - 2306207846 - ADPRO A

> What is amqp?

AMQP (Advanced Message Queuing Protocol) adalah protokol komunikasi antrian pesan yang dirancang untuk memungkinkan sistem perangkat lunak saling bertukar pesan atau berkomunikasi secara asinkronus melalui message queue, bahkan ketika dijalankan pada mesin atau bahasa pemrograman yang berbeda. Contoh pengimplementasian AMQP, yaitu pada `main.rs`, terdapat protokol komunikasi untuk menerima pesan bertipe `UserCreatedEventMessage` dari antrian bernama `user_created` menggunakan library `crosstown_bus` yang berfungsi sebagai abstraksi untuk message broker dan akan ditangani menggunakan handler `UserCreatedHandler`.

> What does it mean? guest:guest@localhost:5672, what is the first guest, and what is the second guest, and what is localhost:5672 is for?

Hal tersebut adalah format umum untuk terhubung ke Server AMQP (RabbitMQ)
- guest (pertama): username yang digunakan untuk login ke RabbitMQ
- guest (kedua): password untuk username tersebut
- localhost: alamat server RabbitMQ yang ingin dihubungi, di mana program ini mencoba terhubung ke komputer lokal
- 5672: port default untuk protokol AMQP

## Simulation slow subscriber
![image](https://github.com/user-attachments/assets/c2ed5e65-7814-42fa-bd2a-0a2d798469ef)
Kali ini, saya mencoba untuk memperlambat proses pada Subscriber dan dapat dilihat ketika kita menjalani run, maka queued messages akan bertambah sesuai dengan delay yang diberikan. Pada kasus ini, saya menjalani tiga `cargo run` pada Publisher dan kemudian terdapat queued messages sekitar 11 buah pesan.

## Reflection and Running at least three subscribers
![image](https://github.com/user-attachments/assets/4b2b07f5-a1dc-4042-ba1c-4d6c5a02a416)
![image](https://github.com/user-attachments/assets/c3e43c93-6109-4b01-af2f-7669408e4ddf)
Dengan membuka lebih dari satu console subscriber, kita dapat melihat bahwa tiap console memproses pesan-pesan yang dikirim. Pada grafik di RabbitMQ juga kita dapat melihat bahwa queued messages yang terdaftar hanya tiga untuk tiga `cargo run` yang saya jalani, hal ini menandakan jika kita membuka banyak Subscriber, maka akan lebih sedikit queued messages yang terdaftar karena masing-masing Subscriber langsung memproses berbagai pesan. Oleh karena itu, tanpa mengubah bagian di kode, kita dapat memperoleh hasil yang lebih maksimal hanya dengan menambah jumlah Subscriber.
