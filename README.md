# Lab11Web
**Nama: Ema Rosida**

**NIM: 312010062**

**Kelas: TI.20.D1**

**Mata Kuliah: Pemrograman Web**

# Praktikum 11: PHP Framework (Codeigniter)

## Langkah-langkah Praktikum
## Buat folder baru dengan nama lab11_php_ci pada docroot webserver (htdocs)
![1](https://user-images.githubusercontent.com/101863671/172442263-0228c279-9199-456a-8ced-9a279c981114.png)

## Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache klik Config -> PHP.ini
<img width="546" alt="2(2)" src="https://user-images.githubusercontent.com/101863671/172443496-304c1dc8-a40a-4aa4-a2a4-735466644081.png">

## Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server.
![3(2)](https://user-images.githubusercontent.com/101863671/172443900-e7d3a3f7-9a9f-47bf-bbc5-311d48bdcf90.png)

## Instalasi Codeigniter 4
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara
manual.
- Unduh Codeigniter dari website https://codeigniter.com/download
- Extrak file zip Codeigniter ke direktori ```htdocs/lab11_php_ci```.
- Ubah nama direktory ```framework-4.x.xx``` menjadi ```ci4```.
- Buka browser dengan alamat http://localhost/lab11_php_ci/ci4/public/

![5](https://user-images.githubusercontent.com/101863671/172444266-4a869013-2a09-403b-ab0c-c24ce045952e.png)

## Menjalankan CLI (Command Line Interface)
Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka terminal/command prompt. Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat ```(xampp/htdocs/lab11_php_ci/ci4/)```. Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah: ```php spark```

![7](https://user-images.githubusercontent.com/101863671/172445280-207dd4de-6d3e-4fd5-b745-4468aea7c4ce.png)

## Mengaktifkan Mode Debugging
Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program.
Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan seperti berikut.
![10](https://user-images.githubusercontent.com/101863671/172446736-2c059e6f-0895-4be7-bb4f-bdc876ebd02e.png)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi
pada environment variable ```CI_ENVIRONMENT``` menjadi ```development```. Kemudian mengubah nama file ```env``` menjadi ```.env``` lalu setelah itu buka file tersebut dan ubah nilai variable ```CI_ENVORNMENT``` menjadi ```development```. Setelah itu hapus ```tanda tagar (#)``` pada awal baris ```CI_ENVIRONMENT```, ubah kode pada file ```app/Controller/Home.php``` hilangkan ```titik koma (;)``` pada akhir kode seperti berikut.

![9 (2)](https://user-images.githubusercontent.com/101863671/172447763-0a97c541-f7b1-4516-bf1c-545bd9f8cee0.png)

![12](https://user-images.githubusercontent.com/101863671/172447813-8ab4de55-5ccc-4449-be55-03a70502b7b4.png)

Maka hasilnya akan terjadi error seperti berikut.

![13](https://user-images.githubusercontent.com/101863671/172449405-1b59c13e-79ad-4ddd-8193-6c3c519d4d1e.png)

## Routing dan Controller
Router terletak pada file ```app/config/Routes.php```. Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.

Contoh: ```$routes->get('/', 'Home::index');``` Kode tersebut akan mengarahkan rute untuk halaman home. 

## Membuat Route Baru.
Tambahkan kode berikut di dalam ```Routes.php```

![14](https://user-images.githubusercontent.com/101863671/172451257-8a11fbd0-2346-4217-be8f-b5d08a7dac41.png)

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut. ```php spark routes```

![15](https://user-images.githubusercontent.com/101863671/172451950-5cebfb79-11df-4c7e-a8f7-a00777ec8c3c.png)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about

![17](https://user-images.githubusercontent.com/101863671/172452099-afd1aba7-8e90-4a16-ae56-8283e0bfbd09.png)

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

## Membuat Controller
Selanjutnya adalah membuat ```Controller Page```. Buat file baru dengan nama ```page.php``` pada direktori ```Controller``` kemudian isi kodenya seperti berikut.

![18](https://user-images.githubusercontent.com/101863671/172452782-fda315ad-de5b-4ed4-9890-109ce8cfa31a.png)

Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaitu halaman sudah dapat diakses.

![19](https://user-images.githubusercontent.com/101863671/172453503-ba86ee29-61bd-4289-8c1a-1a9967628616.png)

## Auto Routing
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai ```true``` menjadi ```false```.

Tambahkan method baru pada ```Controller Page``` seperti berikut

![20](https://user-images.githubusercontent.com/101863671/172456457-60584f21-56d6-4c69-9dc3-70351a3969a6.png)

Method ini belum ada pada ```routing```, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos

![22](https://user-images.githubusercontent.com/101863671/172458692-38665a24-72ad-4217-8db9-c6e5b4c82f92.png)

## Membuat View
Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama ```about.php``` pada direktori view ```(app/view/about.php)``` kemudian isi kodenya seperti berikut.

![23](https://user-images.githubusercontent.com/101863671/172458940-1255f5a0-8da4-433d-8fae-9f6b8582c6cb.png)

Ubah ```method about``` pada class ```Controller Page``` menjadi seperti berikut:

![24](https://user-images.githubusercontent.com/101863671/172459608-356dfb33-3aa3-43a4-8b62-a53db9775bee.png)

Kemudian lakukan refresh pada halaman tersebut.

![25(2)](https://user-images.githubusercontent.com/101863671/172461267-e78b475a-aa59-4f8a-8f1f-4839fc91e5a3.PNG)

## Membuat Layout Web dengan CSS
Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset
css dan javascript terletak pada direktori ```public```. 

Buat file css pada direktori ```public``` dengan nama ```style.css``` (copy file dari praktikum ```lab4_layout```. Kita akan gunakan layout yang pernah dibuat pada praktikum 4.

![26](https://user-images.githubusercontent.com/101863671/172465776-55b3f895-2464-4d7a-9e41-6358f54840f5.png)

Kemudian buat folder ```template``` pada direktori ```view``` kemudian buat file ```header.php``` dan ```footer.php```

File ```app/view/template/header.php```

![28](https://user-images.githubusercontent.com/101863671/172462180-79e33742-5563-419a-8d96-968014597b2f.png)

File ```app/view/template/footer.php```

![29](https://user-images.githubusercontent.com/101863671/172470521-e1072617-5df9-4645-8304-cfef06d59328.png)

Kemudian ubah file ```app/view/about.php``` seperti berikut.

![30](https://user-images.githubusercontent.com/101863671/172463254-bab3e31b-7421-4ea5-a040-d26da0e26475.png)

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![31](https://user-images.githubusercontent.com/101863671/172463301-16211f23-f8f7-4359-920b-f32841e7d0c2.png)

# Pertanyaan dan Tugas
Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

## Update Controller ```(page.php)```
![32](https://user-images.githubusercontent.com/101863671/172463496-4dcb8453-66ae-4da0-b4d1-db5ca0d3e7fb.png)

## Menu About
![33](https://user-images.githubusercontent.com/101863671/172464031-880db1cc-ea2a-447f-889e-59d8378808e8.png)

## Menu Contact
![35](https://user-images.githubusercontent.com/101863671/172464558-93f4314b-3318-4f86-b855-8e7cf8bb0c9c.png)

Maka hasilnya seperti berikut

![34](https://user-images.githubusercontent.com/101863671/172470640-9cc8cc8b-3b27-42d0-b45b-514b87021522.png)

![36](https://user-images.githubusercontent.com/101863671/172470688-107ef462-425a-485e-9473-242283cb8767.png)

![37](https://user-images.githubusercontent.com/101863671/172470710-e77bac3e-b747-4d5d-bf60-d4be12df0c46.png)
