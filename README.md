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

Bridge pattern digunakan untuk memisahkan abstraksi dari implementasinya, sehingga keduanya dapat berubah secara independen. Bridge sangat berguna ketika Anda memiliki hierarki kelas yang kompleks dan ingin menghindari ketergantungan yang kuat antara abstraksi dan implementasi. Pisahkan antarmuka (*interface*) dan implementasi suatu komponen ke dalam hierarki kelas yang ortogonal. Kelas antarmuka berisi sebuah *pointer* ke kelas implementasi abstrak. *Pointer* ini diinisialisasi dengan sebuah instance dari kelas implementasi konkret, tetapi semua interaksi selanjutnya dari kelas antarmuka ke kelas implementasi dibatasi pada abstraksi yang dipertahankan dalam kelas implementasi dasar. Klien berinteraksi dengan kelas antarmuka, yang kemudian "mendelegasikan" semua permintaan ke kelas implementasi.  

Objek antarmuka berfungsi sebagai *"handle"* yang dikenal dan digunakan oleh klien, sedangkan objek implementasi, atau *"body"*, dienkapsulasi dengan aman untuk memastikan bahwa ia dapat terus berkembang, diganti sepenuhnya, atau bahkan dibagikan saat *run-time*.  

Gunakan pola *Bridge* ketika:  
- Anda ingin melakukan *run-time binding* terhadap implementasi.  
- Anda memiliki banyak kelas yang berkembang karena antarmuka yang terhubung erat dengan berbagai implementasi.  
- Anda ingin berbagi implementasi di antara beberapa objek.  
- Anda perlu memetakan hierarki kelas yang ortogonal.  

Konsekuensi dari penggunaan pola ini meliputi:  
- Pemisahan (*decoupling*) antara antarmuka dan implementasi objek.  
- Peningkatan ekstensibilitas (Anda dapat memperluas (*subclass*) hierarki abstraksi dan implementasi secara independen).  
- Penyembunyian detail implementasi dari klien.  

*Bridge* adalah sinonim dari idiom *"handle/body"*. Ini adalah mekanisme desain yang mengenkapsulasi kelas implementasi dalam kelas antarmuka. Kelas implementasi bertindak sebagai *body*, sedangkan kelas antarmuka bertindak sebagai *handle*. Klien melihat *handle* sebagai kelas utama, tetapi pekerjaan utama dilakukan di *body*.  

*"Handle/body class idiom"* dapat digunakan untuk memecah abstraksi yang kompleks menjadi kelas yang lebih kecil dan mudah dikelola. Selain itu, idiom ini dapat digunakan untuk mencerminkan penggunaan sumber daya tunggal yang dibagikan oleh beberapa kelas yang mengontrol akses ke sumber daya tersebut (misalnya, melalui *reference counting*).

## **ILUSTRASI**

![image](https://github.com/user-attachments/assets/47f62f6f-ad12-4465-8aa8-f88e12d077c4)

Pola *Bridge* memisahkan (*decouples*) abstraksi dari implementasinya, sehingga keduanya dapat berkembang secara independen. Sebuah sakelar rumah tangga yang mengontrol lampu, kipas langit-langit, dan perangkat lainnya adalah contoh dari pola *Bridge*. Tujuan dari sakelar adalah untuk menyalakan atau mematikan perangkat. Implementasi sakelar yang sebenarnya dapat berupa rantai tarik, sakelar dua posisi sederhana, atau berbagai jenis sakelar peredup (*dimmer switch*).

### **Stuktur Creational Building Pattern**

![image](https://github.com/user-attachments/assets/98345e74-4136-4501-a27c-abe8ecebf0d4)

Klien tidak ingin berurusan dengan detail yang bergantung pada platform. Pola *Bridge* mengenkapsulasi kompleksitas ini di balik sebuah abstraksi sebagai *"wrapper"*. *Bridge* menekankan pada identifikasi dan pemisahan (*decoupling*) antara abstraksi antarmuka (*interface abstraction*) dan abstraksi implementasi (*implementation abstraction*). Dari struktur ini maka nantinya kita akan mendapatkan gambaran bagaimana class diagram dan sourcode akan di buat:

![image](https://github.com/user-attachments/assets/c4628a3d-10a0-43b0-a0f0-d516828d96de)

Dalam class diagram dan juga Source code ini keduanya adalah class induk atau parent

![image](https://github.com/user-attachments/assets/68d5be64-23e9-4fec-938a-87094979c9f4)

Dalam class diagram dan juga Sourcode ini keduanya adalah class child yang di turunkan dari kelas induknya

![image](https://github.com/user-attachments/assets/ab9a5b33-809b-42b7-bd3f-a941d7c02557)

Dalam class diagram dan juga Sourcode ini keduanya adalah Interface, interface ini nantinya yang akan menjadi jembatan atau bridge

![image](https://github.com/user-attachments/assets/26e609a7-3a4a-49e0-89fd-40f8956b4a83)
\
Dalam class diagram dan juga Sourcode ini keduanya adalah implementasi dan turunan dari interfacce yang nantinya berfungsi untuk menyimpan suatu implementasi yang nantinya akan di gunakan interface




### **Class Diagram**

![Structural bridge](https://github.com/user-attachments/assets/f1ce54c6-010c-4ed1-bb06-c65d5fa16b5e)

## **Penjelasan Class Diagram**
Class diagram yang telah dibuat mencerminkan implementasi dari **Bridge Pattern**, yang bertujuan untuk memisahkan abstraksi (`HewanTernak`) dengan implementasi spesifik untuk setiap jenis hewan (`ImplementasiHewanTernak`).  

### **1. Struktur dan Hubungan Antar Kelas**
### **a. Abstraksi Utama (`HewanTernak`)**  
Kelas **`HewanTernak`** adalah kelas utama yang merepresentasikan hewan ternak secara umum. Kelas ini memiliki atribut dan metode sebagai berikut:  
- **Atribut:**  
  - `jenis`: Menyimpan jenis hewan, seperti "Sapi", "Kambing", "Ayam", atau "Unta".  
  - `gender`: Menyimpan jenis kelamin hewan, misalnya "Jantan" atau "Betina".  
  - `tanggal_lahir`: Menyimpan tanggal lahir hewan dalam format `Date`.  
  - `umur_bulan`: Menghitung umur hewan berdasarkan tanggal lahir.  
  - `berat_kg`: Menyimpan berat hewan dalam kilogram.  
  - `implementasi`: Objek dari kelas `ImplementasiHewanTernak` yang menangani logika spesifik tiap jenis hewan.  

- **Metode:**  
  - `cek_potong()`: Mengecek apakah hewan sudah memenuhi syarat untuk dipotong berdasarkan `umur_bulan`.  
  - `cek_kembangbiak()`: Mengecek apakah hewan sudah memenuhi syarat untuk berkembang biak berdasarkan `umur_bulan` dan `gender`.  
  - `tampilkan_info()`: Menampilkan informasi tentang hewan.  
  - `sapa_hewan()`: Memberikan pesan sapaan berdasarkan jenis hewan.  

### **b. Interface (`ImplementasiHewanTernak`)**
Kelas **`ImplementasiHewanTernak`** adalah **interface** yang menjadi jembatan antara kelas abstraksi (`HewanTernak`) dan implementasi spesifik tiap jenis hewan.  
Interface ini memiliki metode:  
- `cek_potong(umur_bulan: int)`: Mengecek apakah hewan boleh dipotong.  
- `cek_kembangbiak(umur_bulan: int, gender: String)`: Mengecek apakah hewan bisa berkembang biak.  
- `tampilkan_info(hewan: HewanTernak)`: Menampilkan informasi hewan tertentu.  
- `sapa_hewan(hewan: HewanTernak)`: Memberikan sapaan khusus berdasarkan jenis hewan.  

Interface ini memastikan bahwa setiap jenis hewan memiliki aturan yang bisa diimplementasikan dengan cara berbeda tanpa mengubah struktur **HewanTernak**.

### **c. Implementasi Spesifik (`ImplementasiSapi`, `ImplementasiKambing`, `ImplementasiAyam`, `ImplementasiUnta`)**
Kelas-kelas ini adalah implementasi konkret dari `ImplementasiHewanTernak`.  
Masing-masing kelas menentukan logika spesifik terkait pemotongan dan perkembangbiakan hewan berdasarkan jenisnya:  
- **`ImplementasiSapi`**: Misalnya, sapi bisa disembelih pada umur tertentu dan berkembang biak jika berusia minimal beberapa bulan.  
- **`ImplementasiKambing`**: Memiliki aturan pemotongan dan perkembangbiakan yang berbeda dari sapi.  
- **`ImplementasiAyam`**: Umumnya lebih cepat dalam siklus hidupnya dibandingkan sapi atau kambing.  
- **`ImplementasiUnta`**: Mungkin memiliki aturan yang berbeda lagi karena karakteristik biologis unta yang khas.  

Setiap **subclass** ini mengimplementasikan metode dari **interface** `ImplementasiHewanTernak`.

### **d. Kelas Turunan (`Sapi`, `Kambing`, `Ayam`, `Unta`)**
Setiap jenis hewan memiliki kelas spesifik, seperti:  
- **`Sapi`** → Menyediakan implementasi sapi dengan `ImplementasiSapi`.  
- **`Kambing`** → Menyediakan implementasi kambing dengan `ImplementasiKambing`.  
- **`Ayam`** → Menyediakan implementasi ayam dengan `ImplementasiAyam`.  
- **`Unta`** → Menyediakan implementasi unta dengan `ImplementasiUnta`.  

Kelas-kelas ini adalah **turunan dari `HewanTernak`** yang menggunakan implementasi spesifik untuk setiap jenis hewan.

## **Dampak Jika Class Bridge Dihapus**
Jika **class Bridge (`ImplementasiHewanTernak`) dihapus**, maka pola **Bridge** tidak lagi digunakan, dan beberapa masalah akan muncul:  

1. **Kelas `HewanTernak` Harus Menangani Semua Logika Sendiri**  
   - Tanpa interface `ImplementasiHewanTernak`, maka seluruh logika pemotongan dan perkembangbiakan harus ditangani langsung di kelas `HewanTernak`.  
   - Ini menyebabkan kode menjadi **monolitik** dan sulit diperluas.  

2. **Kurangnya Fleksibilitas**  
   - Jika ingin menambahkan jenis hewan baru, maka kita harus **mengubah langsung** kelas `HewanTernak`, bukan hanya menambahkan subclass baru.  
   - Hal ini melanggar **Open-Closed Principle (OCP)** dalam SOLID, yang menyarankan bahwa kode harus terbuka untuk ekstensi tetapi tertutup untuk modifikasi.  

3. **Duplikasi Kode**  
   - Jika setiap kelas seperti `Sapi`, `Kambing`, `Ayam`, dan `Unta` menangani sendiri aturan pemotongan dan perkembangbiakan, maka akan banyak **pengulangan kode**.  
   - Dengan **Bridge Pattern**, kita cukup mendefinisikan aturan sekali dalam `ImplementasiHewanTernak` dan menggunakannya dalam berbagai subclass.  

4. **Sulit untuk Mengubah atau Mengganti Implementasi**  
   - Misalkan kita ingin mengganti aturan pemotongan sapi, maka kita harus mencari setiap referensi sapi dalam kode dan mengubahnya secara manual.  
   - Dengan **Bridge Pattern**, kita cukup mengubah `ImplementasiSapi`, dan semua objek sapi akan langsung mengikuti aturan baru.  

5. **Keterkaitan Erat antara Abstraksi dan Implementasi**  
   - Tanpa Bridge, `HewanTernak` akan terlalu erat terkait dengan implementasi spesifik tiap hewan.  
   - Dengan Bridge, kita bisa mengganti implementasi tanpa mengubah struktur utama `HewanTernak`.  

### **Sequence Diagram**
![image](https://github.com/user-attachments/assets/4fb29e08-68cf-46c8-97da-eb63124ca0d3)

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
![image](https://github.com/user-attachments/assets/85353682-8274-4a6d-85c9-575d59d85086)

### **Kode CLI**
![image](https://github.com/user-attachments/assets/b8f69d44-91e9-468b-a18f-bcb33c38771b)


## **Design Pattern Behavioral: Observer**

### **Penjelasan**

Observer pattern digunakan ketika ada hubungan satu-ke-banyak antara objek, di mana satu objek (subjek) memiliki banyak objek dependen (observer) yang perlu diberi tahu ketika subjek mengalami perubahan state. Observer memungkinkan objek-objek ini untuk "mengamati" subjek dan bereaksi terhadap perubahan tersebut. Tentukan sebuah objek yang berperan sebagai *"keeper"* dari model data dan/atau logika bisnis (*Subject*). Delegasikan seluruh fungsi *"view"* kepada objek *Observer* yang terpisah dan tidak terhubung langsung (*decoupled*). Setiap *Observer* mendaftarkan dirinya ke *Subject* saat dibuat. Ketika *Subject* mengalami perubahan, ia akan menyiarkan notifikasi ke semua *Observer* yang telah terdaftar, dan masing-masing *Observer* akan mengambil (*query*) bagian dari *state* *Subject* yang menjadi tanggung jawabnya untuk dipantau.  

Pendekatan ini memungkinkan jumlah dan jenis objek *view* dikonfigurasi secara dinamis, bukan ditentukan secara statis saat *compile-time*.  

Protokol di atas menggunakan model interaksi *"pull"*. Alih-alih *Subject* langsung *"mendorong"* perubahan ke semua *Observer*, setiap *Observer* bertanggung jawab untuk *"menarik"* bagian informasi yang dibutuhkannya dari *Subject*. Model *"push"* mengurangi kemungkinan penggunaan ulang (*reuse*), sedangkan model *"pull"* kurang efisien.  

Beberapa masalah yang dibahas tetapi diserahkan kepada keputusan desainer meliputi:  
- Implementasi kompresi event (mengirim satu notifikasi perubahan setelah serangkaian perubahan berturut-turut terjadi).  
- Seorang *Observer* yang memantau beberapa *Subject*.  
- Memastikan bahwa *Subject* memberi tahu *Observer* saat akan dihapus.  

Pola *Observer* menangkap sebagian besar konsep arsitektur *Model-View-Controller* (*MVC*), yang telah lama menjadi bagian dari komunitas Smalltalk.

## **ILUSTRASI**
![image](https://github.com/user-attachments/assets/349cd3f5-2ea0-4431-aecc-182cbdb87bac)


### **Stuktur Creational Building Pattern**
![image](https://github.com/user-attachments/assets/ef3461dd-190d-4ce9-8d18-43574a831825)
*Subject* merepresentasikan inti (*core*), atau abstraksi yang independen, umum, atau berperan sebagai *engine*. Sementara itu, *Observer* merepresentasikan abstraksi yang bersifat variabel, bergantung, opsional, atau bagian dari antarmuka pengguna (*user interface*). *Subject* memberi sinyal kepada objek *Observer* untuk menjalankan fungsinya. Setiap *Observer* dapat memanggil kembali (*callback*) ke *Subject* sesuai kebutuhan. Structure ini nantinya akan mempermudah kita membangun dan mengusun class diagram dan code yang di buat. pada gambar di bawah ini terlihat bahwa struktur dan code yang di buat memiliki struktuk yang sama

![image](https://github.com/user-attachments/assets/09736b21-1071-491c-b000-83d8f6bf6fa6)
![image](https://github.com/user-attachments/assets/3f14e28d-c6ed-4273-ae4f-ac54998039e2)
![image](https://github.com/user-attachments/assets/da99c4c0-3874-4ba4-81f5-38ec16cdb43d)


### **Class Diagram**

![behavioral observer](https://github.com/user-attachments/assets/f72cae34-b3d0-48d0-89f2-c7a9716f6856)

## Penjelasan  
Kode ini menggunakan **Observer Pattern**, yang memungkinkan objek **HewanTernak** memberi notifikasi ke objek **Observer** ketika terjadi perubahan status (misalnya, apakah hewan sudah bisa disembelih atau berkembang biak).  
- **Subject (HewanTernak)** mengelola daftar **Observer**, menambahkan atau menghapusnya, serta memberi notifikasi ketika ada perubahan.  
- **Observer** adalah antarmuka yang memiliki metode `update(hewan)`, yang kemudian diimplementasikan oleh dua observer:  
  - **PotongObserver** → mengecek apakah hewan siap disembelih.  
  - **KembangBiakObserver** → mengecek apakah hewan siap berkembang biak.  
- Kelas turunan **HewanTernak** (Sapi, Kambing, Ayam, Unta) menyimpan informasi batas umur minimal dan maksimal untuk penyembelihan dan perkembangbiakan.  

## Dampak Jika Class Observer Dihapus  
Jika **Observer Pattern** dihapus (termasuk `Observer`, `PotongObserver`, `KembangBiakObserver`, dan mekanisme observer pada `HewanTernak`), maka:  
1. **Tidak ada notifikasi otomatis** → Hewan tidak dapat memberi tahu apakah sudah siap disembelih atau berkembang biak.  
2. **Harus mengecek manual** → Setiap kali pengguna ingin tahu status hewan, mereka harus memanggil `cek_potong()` atau `cek_kembangbiak()` secara manual.  
3. **Kurang fleksibel** → Jika ingin menambahkan tipe pengecekan lain (misalnya, observer untuk kesehatan hewan), harus mengubah logika utama HewanTernak daripada cukup menambah observer baru.  

### **Sequence Diagram**
![image](https://github.com/user-attachments/assets/d37542fb-30bd-41b2-bdb4-7980db542079)
## **Penjelasan Sequence Diagram**  


### **1. Proses Input Data Hewan**  
Pada tahap ini, **User** memasukkan data hewan, seperti jenis, gender, tanggal lahir, dan berat, melalui **Boundary (UI/Input Handler)**. Boundary kemudian mengirim data tersebut ke **Entity (HewanTernak)** untuk diproses.  

Setelah menerima data, **Entity** akan menghitung umur berdasarkan tanggal lahir dan menetapkan informasi batas usia penyembelihan serta batas usia berkembang biak. Setelah pemrosesan selesai, **Entity** mengembalikan objek HewanTernak yang sudah terinisialisasi ke **Boundary**, yang kemudian menampilkan konfirmasi kepada **User** bahwa data telah berhasil disimpan.  

---

### **2. Proses Menambahkan Observer**  
Setelah data hewan berhasil dimasukkan, **Boundary** menambahkan dua observer ke objek **HewanTernak**, yaitu:  
1. **PotongObserver**, yang akan mengevaluasi apakah hewan sudah siap untuk disembelih.  
2. **KembangBiakObserver**, yang akan mengevaluasi apakah hewan sudah siap untuk berkembang biak.  

Boundary mengirim perintah ini ke **Control (Observer Logic)**, yang bertugas menyimpan kedua observer tersebut dalam daftar pengamat. Setelah observer berhasil ditambahkan, **Control** mengembalikan konfirmasi ke **Boundary**.  

---

### **3. Proses Menampilkan Informasi Hewan**  
Ketika **User** ingin melihat informasi mengenai hewan yang telah dimasukkan, **Boundary** mengirim permintaan ke **Entity (HewanTernak)** untuk mengambil data yang diperlukan.  

**Entity** kemudian memproses data yang mencakup jenis, gender, umur, dan berat hewan, lalu mengembalikannya ke **Boundary**. Setelah itu, **Boundary** akan menampilkan informasi tersebut kepada **User**.  

---

### **4. Proses Sapa Hewan**  
User juga dapat meminta sistem untuk menampilkan sapaan hewan. Dalam proses ini, **User** mengirimkan permintaan melalui **Boundary**, yang kemudian meneruskan perintah tersebut ke **Entity (HewanTernak)**.  

**Entity** akan memproses teks sapaan yang sesuai dengan jenis hewan dan mengembalikannya ke **Boundary**, yang kemudian menampilkan sapaan tersebut kepada **User**.  

---

### **5. Proses Mengecek Status Hewan (Notifikasi dari Observer)**  
Pada tahap ini, **User** ingin mengecek kesiapan hewan dengan memanggil fungsi `beri_notifikasi()`. **Boundary** meneruskan permintaan ini ke **Control (Observer Logic)**, yang kemudian akan menjalankan evaluasi terhadap status hewan berdasarkan observer yang telah ditambahkan sebelumnya.  

**Control** melakukan iterasi (loop) pada semua observer yang terdaftar dan menjalankan dua pemeriksaan utama:  
1. **Pemeriksaan kesiapan penyembelihan**, di mana **Entity (HewanTernak)** mengecek apakah umur hewan telah mencapai batas minimal/maksimal untuk disembelih. Hasil evaluasi ini dikembalikan ke **Control**.  
2. **Pemeriksaan kesiapan berkembang biak**, di mana **Entity** mengecek apakah umur dan gender hewan memenuhi syarat untuk berkembang biak. Hasil evaluasi ini juga dikembalikan ke **Control**.  

Setelah kedua observer selesai mengevaluasi status hewan, **Control** mengirimkan hasil evaluasi ke **Boundary**, yang kemudian menampilkannya kepada **User**.  

### **Use Cse Diagram**
![image](https://github.com/user-attachments/assets/263414c2-7355-4c59-829a-01160d27a1e5)


### **Kode CLI**
![image](https://github.com/user-attachments/assets/c76429af-3e43-4940-bdd5-40748e327045)






