## **Laporan Design Pattern**

## **Penjelasan Design Pattern**

Design pattern adalah solusi umum yang dapat digunakan kembali untuk masalah desain yang umum terjadi dalam pengembangan perangkat lunak. Pola-pola ini merupakan praktik terbaik yang telah teruji dan terbukti efektif dalam memecahkan masalah desain tertentu.

## **Design Pattern Creational: Builder**

### **Penjelasan**

Builder pattern digunakan untuk memisahkan konstruksi objek yang kompleks dari representasinya, sehingga proses pembuatan objek dapat dikontrol dan lebih fleksibel. Builder sangat berguna ketika sebuah objek memiliki banyak parameter opsional atau ketika proses pembuatannya melibatkan langkah-langkah yang rumit.

### **Class Diagram**

![image](https://github.com/user-attachments/assets/51798ca2-d7c5-4c96-a9ee-dad2610a792f)

Diagram kelas ini menunjukkan hubungan antara kelas `HewanTernak`, `HewanTernakBuilder`, dan kelas-kelas anak seperti `Sapi`, `Kambing`, `Ayam`, dan `Unta`. `HewanTernakBuilder` bertanggung jawab untuk membangun objek `HewanTernak` dengan konfigurasi yang berbeda-beda.

*   **`HewanTernak`**: Kelas utama yang merepresentasikan hewan ternak. Memiliki atribut seperti jenis, gender, tanggal lahir, dll.
*   **`HewanTernakBuilder`**: Kelas yang bertanggung jawab untuk membangun objek `HewanTernak`. Memiliki method-method untuk mengatur atribut dan method `bangun()` untuk menghasilkan objek `HewanTernak`.
*   **Kelas Anak (Sapi, Kambing, Ayam, Unta)**: Kelas-kelas yang наследуется dari `HewanTernak`. Bertanggung jawab untuk mengatur konfigurasi spesifik untuk setiap jenis hewan.

### **Alur Class Diagram Builder**

1.  Kelas anak (misalnya, `Sapi`) membuat instance dari `HewanTernakBuilder`.
2.  Kelas anak memanggil method-method pada `HewanTernakBuilder` untuk mengatur atribut-atribut `HewanTernak`.
3.  Kelas anak memanggil method `bangun()` pada `HewanTernakBuilder` untuk menghasilkan objek `HewanTernak`.

### **Sequence Diagram**

![image](https://github.com/user-attachments/assets/914bc7a3-82bf-48e8-8ec8-be27863a966a)
Diagram sekuens ini menggambarkan alur interaksi antara objek-objek dalam proses pembuatan objek `HewanTernak` menggunakan builder.

1.  Pengguna memasukkan data hewan.
2.  Program membuat objek `HewanTernak` melalui kelas anak (misalnya, `Sapi`).
3.  Kelas anak membuat instance dari `HewanTernakBuilder`.
4.  Kelas anak memanggil method-method pada `HewanTernakBuilder` untuk mengatur atribut-atribut `HewanTernak`.
5.  Kelas anak memanggil method `bangun()` pada `HewanTernakBuilder` untuk menghasilkan objek `HewanTernak`.
6.  Program menggunakan objek `HewanTernak` untuk menampilkan informasi hewan.

### **Kode CLI**

![image](https://github.com/user-attachments/assets/b8f69d44-91e9-468b-a18f-bcb33c38771b)

## **Design Pattern Structural: Bridge**

### **Penjelasan**

Bridge pattern digunakan untuk memisahkan abstraksi dari implementasinya, sehingga keduanya dapat berubah secara independen. Bridge sangat berguna ketika Anda memiliki hierarki kelas yang kompleks dan ingin menghindari ketergantungan yang kuat antara abstraksi dan implementasi.

### **Class Diagram**

![image](https://github.com/user-attachments/assets/3cc4fa1b-14b7-4dac-b6d7-5e337c1d8c20)


Diagram kelas ini menunjukkan bagaimana Bridge pattern memisahkan abstraksi `HewanTernak` dari implementasi spesifik untuk setiap jenis hewan (misalnya, `ImplementasiSapi`, `ImplementasiKambing`, dll.).

*   **`HewanTernak`**: Kelas utama yang merepresentasikan hewan ternak. Memiliki atribut seperti jenis, gender, tanggal lahir, dll. dan method-method umum untuk semua hewan ternak.
*   **`ImplementasiHewanTernak`**: Interface yang mendefinisikan method-method yang harus diimplementasikan oleh kelas-kelas implementasi.
*   **Kelas Implementasi (ImplementasiSapi, ImplementasiKambing, dll.)**: Kelas-kelas yang mengimplementasikan interface `ImplementasiHewanTernak`. Menyediakan implementasi spesifik untuk setiap jenis hewan.

### **Alur Class Diagram Bridge**

1.  Kelas anak (misalnya, `Sapi`) membuat instance dari kelas implementasi yang sesuai (misalnya, `ImplementasiSapi`).
2.  Kelas anak meneruskan instance kelas implementasi ke konstruktor kelas `HewanTernak`.
3.  Kelas `HewanTernak` menyimpan instance kelas implementasi sebagai atributnya.
4.  Ketika method pada `HewanTernak` dipanggil, ia mendelegasikan panggilan tersebut ke instance kelas implementasi.

### **Sequence Diagram**

![image](https://github.com/user-attachments/assets/25f9e65b-8106-450b-9817-143013d8582c)
Diagram sekuens ini menggambarkan bagaimana objek `HewanTernak` mendelegasikan operasi ke objek implementasi yang sesuai melalui jembatan (bridge).

1.  Pengguna memasukkan data hewan.
2.  Program membuat objek `HewanTernak` melalui kelas anak (misalnya, `Sapi`).
3.  Kelas anak membuat instance dari kelas implementasi yang sesuai (misalnya, `ImplementasiSapi`).
4.  Kelas anak meneruskan instance kelas implementasi ke konstruktor kelas `HewanTernak`.
5.  Ketika method pada `HewanTernak` dipanggil, ia mendelegasikan panggilan tersebut ke instance kelas implementasi.
6.  Kelas implementasi menjalankan operasi yang sesuai dan mengembalikan hasilnya ke `HewanTernak`.
7.  `HewanTernak` mengembalikan hasil ke program.
8.  Program menampilkan informasi hewan kepada pengguna.

### **Kode CLI**

![image](https://github.com/user-attachments/assets/59e74da3-23e3-4743-9e24-4fe83db04190)

## **Design Pattern Behavioral: Observer**

### **Penjelasan**

Observer pattern digunakan ketika ada hubungan satu-ke-banyak antara objek, di mana satu objek (subjek) memiliki banyak objek dependen (observer) yang perlu diberi tahu ketika subjek mengalami perubahan state. Observer memungkinkan objek-objek ini untuk "mengamati" subjek dan bereaksi terhadap perubahan tersebut.

### **Class Diagram**

![image](https://github.com/user-attachments/assets/6a955736-7179-48da-9c18-82dd91e7dfd8)

Diagram kelas ini menunjukkan bagaimana observer (misalnya, `Peternak`, `Penjual`) mendaftarkan diri ke subjek (`HewanTernak`) dan menerima pemberitahuan ketika ada perubahan state.

*   **`HewanTernak`**: Kelas utama yang merepresentasikan hewan ternak. Memiliki atribut seperti jenis, gender, tanggal lahir, dll. dan method-method untuk menambah dan menghapus observer, serta method untuk memberi tahu observer ketika ada perubahan state.
*   **`Observer`**: Interface yang mendefinisikan method `update()` yang harus diimplementasikan oleh kelas-kelas observer.
*   **Kelas Observer (Peternak, Penjual, dll.)**: Kelas-kelas yang mengimplementasikan interface `Observer`. Bertanggung jawab untuk bereaksi terhadap perubahan state pada subjek.

### **Alur Class Diagram Observer**

1.  Observer (misalnya, `Peternak`) membuat instance dari dirinya sendiri.
2.  Observer mendaftarkan diri ke subjek (`HewanTernak`) menggunakan method `attach()`.
3.  Ketika state subjek berubah, subjek memanggil method `notify_observers()`.
4.  Subjek memberi tahu semua observer yang terdaftar dengan memanggil method `update()` pada masing-masing observer.
5.  Observer menerima pemberitahuan dan bereaksi sesuai dengan logikanya.

### **Sequence Diagram**

![image](https://github.com/user-attachments/assets/a6ad90e7-8a6a-419d-8b2c-200b4514fd8f)

Diagram sekuens ini menggambarkan bagaimana subjek memberi tahu observer ketika ada perubahan state, dan bagaimana observer bereaksi terhadap pemberitahuan tersebut.

1.  Pengguna memasukkan data hewan.
2.  Program membuat objek `HewanTernak`.
3.  Program membuat objek observer (misalnya, `Peternak`, `Penjual`).
4.  Objek `HewanTernak` mendaftarkan observer menggunakan method `attach()`.
5.  Ketika state `HewanTernak` berubah (misalnya, berat hewan berubah), `HewanTernak` memanggil method `notify_observers()`.
6.  `HewanTernak` memberi tahu semua observer dengan memanggil method `update()` pada masing-masing observer.
7.  Observer menerima pemberitahuan dan bereaksi sesuai dengan logikanya.

### **Kode CLI**

![image](https://github.com/user-attachments/assets/3850e7e3-39ef-447e-b07a-e5dec2a46553)



##
