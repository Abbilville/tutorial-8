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

Screenshot interface RabbitMQ ketika saya menjalankan <code>cargo run</code> berkali kali pada publiser ketika sudah menggunakan thread, disini terlihat bahwa queue-nya mencapai 25 karena saya menjalankan <code>cargo run</code> sebanyak 6 kali yang mana terjadi queue sebanyak 5 <code>cargo run</code>, kita tahu bahwa 1 <code>cargo run</code> itu mengirimkan sebanyak 5 data sehingga terdapat queue sebanyak 25 data. <br>
![alt text](assets/images/image1.png) <br><br>

Screenshot ketika saya menjalankan <code>cargo run</code> sebanyak 4 kali pada publisher dan <code>cargo run</code> sebanyak 3 kali di console yang berbeda pada subscriber. Dapat terlihat bahwa spike dari message queue berkurang yang menandakan lebih cepat daripada sebelumnya karena request yang diterima queue akan dibagi tugaskan kepada 3 subscriber. <br>
![alt text](assets/images/image6.png) <br>
![alt text](assets/images/image5.png) <br>
![alt text](assets/images/image2.png) <br>
![alt text](assets/images/image3.png) <br>
![alt text](assets/images/image4.png) <br>

Ada beberapa perbaikan yang dapat dilakukan pada kode ini: <br>
1. Hindari menggunakan <code>unwrap()</code> sebab menggunakan <code>unwrap()</code> pada kode produksi tidak disarankan karena dapat menyebabkan program panic jika Result adalah Err. Sebagai gantinya, kita dapat menangani kesalahan secara elegan menggunakan <code>match</code> atau <code>if let</code>. <br>
2. Gunakan konstanta untuk string yang diulang sebab jika kita memiliki string yang digunakan beberapa kali (seperti <code>amqp://guest:guest@localhost:5672</code>), lebih baik mendefinisikannya sebagai konstanta di bagian atas file.