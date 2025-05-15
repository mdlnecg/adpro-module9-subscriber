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
