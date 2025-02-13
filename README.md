## **Laporan Design Pattern**

## **Penjelasan Design Pattern**

Design pattern adalah solusi umum yang dapat digunakan kembali untuk masalah desain yang umum terjadi dalam pengembangan perangkat lunak. Pola-pola ini merupakan praktik terbaik yang telah teruji dan terbukti efektif dalam memecahkan masalah desain tertentu.

### **Penjelasan**

## **Design Pattern Creational: Builder**
Builder pattern digunakan untuk memisahkan konstruksi objek yang kompleks dari representasinya, sehingga proses pembuatan objek dapat dikontrol dan lebih fleksibel. Builder sangat berguna ketika sebuah objek memiliki banyak parameter opsional atau ketika proses pembuatannya melibatkan langkah-langkah yang rumit.

### **ILUSTRASI**

![image](https://github.com/user-attachments/assets/74c47703-4dc6-44ae-b6a1-b351ae6de324)

Pola Builder memisahkan konstruksi suatu objek kompleks dari representasinya sehingga proses konstruksi yang sama dapat menghasilkan representasi yang berbeda. Pola ini digunakan oleh restoran cepat saji untuk menyusun paket makanan anak-anak. Paket makanan anak-anak biasanya terdiri dari satu item utama, satu makanan pendamping, satu minuman, dan satu mainan (misalnya, hamburger, kentang goreng, Coke, dan mainan dinosaurus). Perlu diperhatikan bahwa isi dari paket makanan anak-anak dapat bervariasi, tetapi proses konstruksinya tetap sama. Baik pelanggan memesan hamburger, cheeseburger, atau ayam, prosesnya tetap sama. Karyawan di kasir mengarahkan tim untuk merakit satu item utama, satu makanan pendamping, dan satu mainan. Item-item ini kemudian dimasukkan ke dalam tas. Minuman ditempatkan dalam gelas dan tetap berada di luar tas. Proses yang sama digunakan di restoran pesaing.

### **Stuktur Creational Building Pattern**

![image](https://github.com/user-attachments/assets/66697140-68d6-4ab7-a003-68dfeb63a05f)

Contoh struktur ini adalah sebuah contoh pengimplementasian Building pattern yang dimana contoh struktur ini dapat menjadi acuan untuh pembuatan pattern building yang dimana pada gambar ini Reader mengenkapsulasi proses parsing dari input yang umum. Hierarki Builder memungkinkan pembuatan polimorfik dari berbagai representasi atau target yang spesifik. Berikut adalah pengimplementasian dari struktur ke dalam code yang di buat:

![image](https://github.com/user-attachments/assets/16cc90fa-4495-41d5-8121-45e20528bb7a)

Kesamaan antara class **`Reader`** dengan sourcode **`HewanTernakBuilder`** yaitu keduanya adalah wadah yang nantinya akan membaca pesanan atau order dari user, maka wadah tersebut akan menyesuaikan sesuai dengan request dari user

![image](https://github.com/user-attachments/assets/776bee69-736f-411c-b5ec-f0439144ba0b)

Kesamaan antara class **`Converter`** dengan sourcode **`HewanTernakB`** yaitu keduanya akan membuat pesanan dari apa yang sudah di pesan oleh user, sourcode ini atau class diagram ini akan membuat sebuah object dari bahan-bahan yang ada, dalam arti bahan-bahan ini akan di dapatkan dari class child.

![image](https://github.com/user-attachments/assets/c86339eb-f4f8-4a39-9299-abe8c8ecd842)

Kesamaan antara class **`PostScriptConverter`**, **`ASCIIConverter`**, dan **`PDFConverter`**, dengan sourcode **`Sapi`**, **`Kambing`**, **`Unta`**, dan **`Ayam`** yaitu keduanya adalah kelas turunan (class child) yang dimana keduanya memiliki bahan-bahan yang di perlukan untuk membangun sebuah object yang akan di gunakan oleh **`HewanTernakBuilder`**.

### **Class Diagram**

![cretive building](https://github.com/user-attachments/assets/fa6b3c2f-74cc-4f36-a2ad-d1bcd07918e3)

### Penjelasan Class Diagram Secara Menyeluruh

1. **HewanTernak**  
   - **Atribut:**  
     - `jenis`, `gender`, `tanggal_lahir`, `umur_bulan`, `berat_kg`, `info_potong`, dan `info_kembangbiak` bersifat *public*.  
     - Semua atribut ini mewakili informasi dasar tentang hewan ternak dan dapat diakses secara langsung karena Python tidak menggunakan modifier akses secara eksplisit.  
   - **Metode:**  
     - `cek_potong()`, `cek_kembangbiak()`, `tampilkan_info()`, dan `sapa_hewan()` juga bersifat *public* untuk memungkinkan pemanggilan dari luar kelas guna mengevaluasi kondisi atau menampilkan informasi hewan.

2. **HewanTernakBuilder**
   - **Peran:**  
     - Menerapkan pola desain *Builder* untuk membuat objek `HewanTernak` secara bertahap.  
     - Memisahkan logika konstruksi dari logika operasional objek utama.
   - **Atribut:**  
     - `hewan` bersifat *private* (ditandai dengan tanda minus `-`) karena hanya digunakan secara internal oleh builder untuk menyusun objek `HewanTernak`.
   - **Metode:**  
     - Metode seperti `dengan_gender()`, `dengan_tanggal_lahir()`, `dengan_berat()`, `dengan_info_potong()`, dan `dengan_info_kembangbiak()` mengembalikan instance builder untuk mendukung *method chaining*.  
     - `bangun()` akan mengembalikan objek `HewanTernak` yang telah dikonfigurasi.

3. **Subclass: Sapi, Kambing, Ayam, Unta**  
   - **Hubungan Inheritance:**  
     - Kelas-kelas ini merupakan spesialisasi dari `HewanTernak` dan mewarisi seluruh atribut serta metode dasar.  
   - **Konstruktor:**  
     - Masing-masing subclass menggunakan `HewanTernakBuilder` untuk menyusun objek dengan konfigurasi spesifik (misalnya, batas umur untuk potong dan kembangbiak) sesuai dengan karakteristik masing-masing hewan.  
   - **Keuntungan Inheritance:**  
     - **Reuse:** Menghindari pengulangan kode karena logika dasar didefinisikan hanya di `HewanTernak`.  
     - **Pemeliharaan:** Perubahan pada metode atau atribut dasar di `HewanTernak` akan otomatis mempengaruhi semua subclass.

---

## Hubungan Antar Kelas

1. **Hubungan antara HewanTernakBuilder dan HewanTernak**  
   - **Tipe Hubungan:**  
     - **Association/Dependency**  
   - **Penjelasan:**  
     - **HewanTernakBuilder** berperan sebagai pembuat (creator) objek `HewanTernak`.  
     - Di dalam builder terdapat atribut private `hewan` yang merupakan instance dari `HewanTernak`.  
     - Builder *bergantung* pada struktur `HewanTernak` karena ia harus mengetahui atribut dan metode yang ada untuk dapat menyusunnya secara bertahap.  
     - Hubungan ini menunjukkan bahwa tanpa `HewanTernak`, builder tidak memiliki objek untuk dikonfigurasikan, sehingga builder memiliki dependency yang jelas terhadap `HewanTernak`.

2. **Hubungan antara Subclass (Sapi, Kambing, Ayam, Unta) dengan HewanTernak**  
   - **Tipe Hubungan:**  
     - **Inheritance/Generalization**  
   - **Penjelasan:**  
     - Setiap kelas seperti **Sapi**, **Kambing**, **Ayam**, dan **Unta** merupakan turunan (subclass) dari `HewanTernak`.  
     - Inheritance memungkinkan masing-masing subclass mewarisi semua atribut dan metode dari `HewanTernak`, sehingga menghindari duplikasi kode dan memastikan konsistensi.  
     - **Manfaat Inheritance:**  
       - **Reuse:** Kode dasar didefinisikan sekali di `HewanTernak` dan dapat digunakan oleh semua subclass.  
       - **Pemeliharaan:** Perubahan di kelas induk secara otomatis akan diterapkan ke subclass, sehingga mengurangi kompleksitas dalam pemeliharaan kode.  
       - **Generalization:** Menyediakan kerangka umum bagi semua jenis hewan ternak, sedangkan masing-masing subclass hanya perlu menambahkan atau mengubah properti yang spesifik.

3. **Dampak Umum dari Hubungan Ini:**
   - **Pemisahan Tanggung Jawab:**  
     - **HewanTernakBuilder** bertugas pada proses konstruksi objek, sedangkan `HewanTernak` dan subclass-nya menangani logika operasional serta perilaku hewan.  
   - **Modularitas dan Fleksibilitas:**  
     - Pola Builder membuat sistem menjadi modular, memungkinkan perubahan pada proses pembuatan objek tanpa harus mengubah logika bisnis dari objek itu sendiri.  
   - **Dependency Management:**  
     - Builder memiliki dependency terhadap `HewanTernak` yang memastikan bahwa setiap perubahan pada struktur dasar harus disinkronkan dengan builder agar pembuatan objek tetap benar.  
   - **Simplisitas dan Keterbacaan:**  
     - Hubungan yang jelas antara builder dan kelas dasar serta inheritance antar subclass menjaga agar diagram tetap simpel dan mudah dipahami, dengan setiap kelas hanya menunjuk langsung pada satu kelas terkait (misalnya, subclass menunjuk ke induk).

---

## Dampak Jika Kelas Builder Dihilangkan

Tanpa adanya `HewanTernakBuilder`:
- **Duplikasi Kode:**  
  - Setiap subclass harus mengimplementasikan logika konstruksi sendiri (misalnya, perhitungan `umur_bulan` dan pengaturan `info_potong`/`info_kembangbiak`), yang berpotensi menghasilkan banyak kode yang serupa.
- **Kesulitan Pemeliharaan:**  
  - Perubahan pada cara pembuatan objek (misalnya, logika perhitungan umur) harus dilakukan di setiap subclass, meningkatkan risiko inkonsistensi.
- **Keterbacaan Menurun:**  
  - Penggabungan logika konstruksi dengan logika objek utama membuat kode menjadi kurang modular dan lebih sulit dipahami serta diperbaiki.

Penggunaan pola Builder melalui `HewanTernakBuilder` memastikan bahwa logika pembuatan objek terpusat, sehingga meningkatkan modularitas, keterbacaan, dan pemeliharaan kode secara keseluruhan.

### **Sequence Diagram**

![image](https://github.com/user-attachments/assets/7ce5aac3-17fe-47d0-8b03-3749b8b6e6ce)

Diagram sekuens ini menggambarkan alur interaksi antara objek-objek dalam proses pembuatan objek `HewanTernak` menggunakan builder.

1.  Pengguna memasukkan data hewan.
2.  Program membuat objek `HewanTernak` melalui kelas anak (misalnya, `Sapi`).
3.  Kelas anak membuat instance dari `HewanTernakBuilder`.
4.  Kelas anak memanggil method-method pada `HewanTernakBuilder` untuk mengatur atribut-atribut `HewanTernak`.
5.  Kelas anak memanggil method `bangun()` pada `HewanTernakBuilder` untuk menghasilkan objek `HewanTernak`.
6.  Program menggunakan objek `HewanTernak` untuk menampilkan informasi hewan.
7.  
### **Use Cse Diagram**
![image](https://github.com/user-attachments/assets/85353682-8274-4a6d-85c9-575d59d85086)

### **Kode CLI**

![image](https://github.com/user-attachments/assets/b8f69d44-91e9-468b-a18f-bcb33c38771b)

## **Design Pattern Structural: Bridge**

### **Penjelasan**

Bridge pattern digunakan untuk memisahkan abstraksi dari implementasinya, sehingga keduanya dapat berubah secara independen. Bridge sangat berguna ketika Anda memiliki hierarki kelas yang kompleks dan ingin menghindari ketergantungan yang kuat antara abstraksi dan implementasi.

## **ILUSTRASI**


### **Stuktur Creational Building Pattern**


### **Class Diagram**



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



Diagram sekuens ini menggambarkan bagaimana objek `HewanTernak` mendelegasikan operasi ke objek implementasi yang sesuai melalui jembatan (bridge).

1.  Pengguna memasukkan data hewan.
2.  Program membuat objek `HewanTernak` melalui kelas anak (misalnya, `Sapi`).
3.  Kelas anak membuat instance dari kelas implementasi yang sesuai (misalnya, `ImplementasiSapi`).
4.  Kelas anak meneruskan instance kelas implementasi ke konstruktor kelas `HewanTernak`.
5.  Ketika method pada `HewanTernak` dipanggil, ia mendelegasikan panggilan tersebut ke instance kelas implementasi.
6.  Kelas implementasi menjalankan operasi yang sesuai dan mengembalikan hasilnya ke `HewanTernak`.
7.  `HewanTernak` mengembalikan hasil ke program.
8.  Program menampilkan informasi hewan kepada pengguna.
   
### **Use Cse Diagram**


### **Kode CLI**



## **Design Pattern Behavioral: Observer**

### **Penjelasan**

Observer pattern digunakan ketika ada hubungan satu-ke-banyak antara objek, di mana satu objek (subjek) memiliki banyak objek dependen (observer) yang perlu diberi tahu ketika subjek mengalami perubahan state. Observer memungkinkan objek-objek ini untuk "mengamati" subjek dan bereaksi terhadap perubahan tersebut.

## **ILUSTRASI**


### **Stuktur Creational Building Pattern**


### **Class Diagram**


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



Diagram sekuens ini menggambarkan bagaimana subjek memberi tahu observer ketika ada perubahan state, dan bagaimana observer bereaksi terhadap pemberitahuan tersebut.

1.  Pengguna memasukkan data hewan.
2.  Program membuat objek `HewanTernak`.
3.  Program membuat objek observer (misalnya, `Peternak`, `Penjual`).
4.  Objek `HewanTernak` mendaftarkan observer menggunakan method `attach()`.
5.  Ketika state `HewanTernak` berubah (misalnya, berat hewan berubah), `HewanTernak` memanggil method `notify_observers()`.
6.  `HewanTernak` memberi tahu semua observer dengan memanggil method `update()` pada masing-masing observer.
7.  Observer menerima pemberitahuan dan bereaksi sesuai dengan logikanya.

### **Use Cse Diagram**


### **Kode CLI**






