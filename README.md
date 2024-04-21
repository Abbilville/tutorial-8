# Tutorial-8
---
#### Nama: Abbilhaidar Farras Zulfikar
#### NPM: 2206026012
#### Kelas: Adpro A
---
### Refleksi
1. **What is *amqp***? <br>
AMQP atau Advanced Message Queuing Protocol. Merupakan open standard application layer protocol untuk message-oriented middleware, biasa digunakan untuk membangun message system. AMQP memungkinkan berbagai aplikasi untuk berkomunikasi satu sama lain dengan bertukar messages secara efisien.<br>

2. **what guest:guest@localhost:5672 means? what is the first quest, and what is the second guest, and what is localhost:5672 is for?** <br>
- String <code>guest:guest@localhost:5672</code> merupakan string koneksi untuk sebuah server AMQP
- <code>guest:guest</code> merupakan nama pengguna dan kata sandi untuk autentikasi pada server. Dalam kasus ini, baik nama pengguna maupun kata sandi keduanya adalah "guest". Dalam banyak konfigurasi default broker pesan seperti RabbitMQ, nama pengguna dan sandi default keduanya adalah "guest". Namun, dalam lingkungan produksi, sangat disarankan untuk mengubah kredensial default ini karena alasan keamanan.
- <code>@localhost:5672</code> menentukan host dan port. "localhost" mengacu pada mesin lokal, yang berarti bahwa message brocker (RabbitMQ) berjalan di mesin yang sama di mana kode ini dieksekusi. Port 5672 adalah port default yang digunakan oleh RabbitMQ untuk komunikasi AMQP.