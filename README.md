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

![14(2)](https://user-images.githubusercontent.com/101863671/172589873-03621699-647e-4761-9db1-75c9f68ffca2.png)

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

# Praktikum 12: Framework Lanjutan (CRUD)
## Langkah-langkah Praktikum
Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah database server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui XAMPP.
![1 (2)](https://user-images.githubusercontent.com/101863671/173547092-843ab28e-c61d-446c-bf80-02310a9b7f8f.png)

## Konfigurasi Koneksi Database
Selanjutnya membuat konfigurasi untuk menghubungkan dengan database server. Konfigurasi dapat dilakukan dengan dua cara, yaitu pada file app/config/database.php
atau menggunakan file .env. Pada praktikum ini kita gunakan konfigurasi pada file ```.env```. Konfigurasi dapat dilakukan dengan cara mengubah beberapa kode pada file ```htdocs\lab11_php_ci\ci4\.env```. Dan hilangkan tanda pagar ```#``` didepan.

![3 (3)](https://user-images.githubusercontent.com/101863671/173550312-6f321837-dcd9-4059-9f92-4c47c1e2124b.png)

## Membuat Model
Selanjutnya adalah membuat Model untuk memproses data Artikel. Buat file baru pada direktori ```app/Models``` dengan nama ```ArtikelModel.php```

![4](https://user-images.githubusercontent.com/101863671/173551166-fa1a8210-b46a-403b-a8ce-cb6e111a5093.png)

## Membuat Controller
Buat Controller baru dengan nama ```Artikel.php``` pada direktori ```app/Controllers```.

![5](https://user-images.githubusercontent.com/101863671/173551453-d763fe3f-92e5-4bee-85ef-1901140c7f7c.png)

## Membuat View
Buat direktori baru dengan nama ```artikel``` pada direktori ```app/views```, kemudian buat file baru dengan nama ```index.php```.

![6 (2)](https://user-images.githubusercontent.com/101863671/173551695-0be44c01-a015-4b15-a1d6-2afb90fa3e54.png)

Selanjutnya buka browser kembali, dengan mengakses url http://localhost:8080/artikel

![7](https://user-images.githubusercontent.com/101863671/173551982-0abc6487-72cf-418f-9d88-6827606df5a1.png)

Belum ada data yang diampilkan. Kemudian coba tambahkan beberapa data pada database agar dapat ditampilkan datanya.

![8](https://user-images.githubusercontent.com/101863671/173552513-35f8d434-2c15-4623-8f57-0a92dca1d7d8.png)

Refresh kembali browser, sehingga akan ditampilkan hasilnya.

![9](https://user-images.githubusercontent.com/101863671/173552593-0eac72da-69c2-4a75-8682-589afd035bab.png)

## Membuat Tampilan Detail Artikel
Tampilan pada saat judul berita di klik maka akan diarahkan ke halaman yang berbeda. Tambahkan fungsi baru pada ```Controller Artikel``` dengan nama ```view()```.

![10](https://user-images.githubusercontent.com/101863671/173552964-deb807f1-2eee-42b6-9bfb-7e4785978cb0.png)

## Membuat View Detail
Buat view baru untuk halaman detail dengan nama ```app/views/artikel/detail.php```.

![11](https://user-images.githubusercontent.com/101863671/173786268-f35f78e1-46e1-4462-9f43-127be6a5ac85.png)

## Membuat Routing untuk artikel detail
Buka Kembali file ```app/config/Routes.php```, kemudian tambahkan routing untuk artikel detail.

![12 (2)](https://user-images.githubusercontent.com/101863671/173786526-3dfd8fa4-07a0-4ee2-998f-bc4b3a098558.png)

Kemudian Refresh kembali

![14](https://user-images.githubusercontent.com/101863671/173787507-64ac6af8-4d1d-4540-ac7f-348e59439c16.png)

## Membuat Menu Admin
Menu admin adalah untuk proses CRUD data artikel. Buat method baru pada ```Controller Artikel``` dengan nama ```admin_index()```.

![15 (2)](https://user-images.githubusercontent.com/101863671/173787691-587cd6e1-d9ab-44ac-aa94-dacbc95eed1c.png)

Selanjutnya buat view untuk tampilan admin dengan nama ```admin_index.php```

![16 (2)](https://user-images.githubusercontent.com/101863671/173787907-a6a35122-5ae8-44ec-a901-f614790adbc0.png)

![17 (2)](https://user-images.githubusercontent.com/101863671/173787947-db2694f1-90cb-4065-abdb-7951438e7eaf.png)

Tambahkan routing untuk menu admin seperti berikut:

![18 (2)](https://user-images.githubusercontent.com/101863671/173788031-6f47bd8d-0247-4475-8568-875f2e616dce.png)

Akses menu admin dengan url http://localhost:8080/admin/artikel

![26](https://user-images.githubusercontent.com/101863671/174576643-af1c19d8-501b-4ea7-8b01-3de795192864.png)

## Menambah Data Artikel
Tambahkan fungsi/method baru pada ```Controller Artikel``` dengan nama ```add()```.

![27 (2)](https://user-images.githubusercontent.com/101863671/173789043-60c7bef2-4b30-49d1-8973-ad5cbfee8b4e.png)

Kemudian buat view untuk form tambah dengan nama ```form_add.php```

![28 (2)](https://user-images.githubusercontent.com/101863671/173789401-9aec1fb8-7e8e-493e-abb5-9a3cb04adf85.png)

Setelah itu klik tambah artikel maka tampilan nya seperti berikut.

![29](https://user-images.githubusercontent.com/101863671/174576387-e929675b-6d2a-4775-a9bf-4db1f8bbfbae.png)

## Mengubah Data
Tambahkan fungsi/method baru pada ```Controller Artikel``` dengan nama ```edit()```.

![30 (2)](https://user-images.githubusercontent.com/101863671/173795478-99fb7103-8160-457d-a945-9bd4e9046267.png)

Kemudian buat view untuk form tambah dengan nama ```form_edit.php```

![31 (2)](https://user-images.githubusercontent.com/101863671/173795793-0d363e3f-a42f-4d8e-824b-a1ae7cf2b10c.png)

maka tampilan nya seperti ini

![32](https://user-images.githubusercontent.com/101863671/174576080-36612cef-1cca-49ed-82ba-ed7766075ad6.png)

## Menghapus Data
Tambahkan fungsi/method baru pada ```Controller Artikel``` dengan nama ```delete()```.

![33 (2)](https://user-images.githubusercontent.com/101863671/173797554-6166a038-5183-4417-bcf5-8fa8b9cda04f.png)

maka tampilan nya seperti ini

![34](https://user-images.githubusercontent.com/101863671/174575838-28d77c10-1b8c-4ea4-9f49-2b87e976ec53.png)

# Pertanyaan dan Tugas
## Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan improvisasi.

Saya melengkapi file admin_header.php dan admin_footer.php serta CSSnya agar programnya bisa di run.

- Admin_header.php

![19](https://user-images.githubusercontent.com/101863671/173820554-355f0bc8-5e62-4cf0-96e6-bb9099190f3b.png)

- Admin_footer.php

![20 (2)](https://user-images.githubusercontent.com/101863671/173820717-103210ab-0e83-4993-bfe1-59b2bd67de19.png)

- admin.css

![21](https://user-images.githubusercontent.com/101863671/174575587-fcc5cb67-aff7-44ce-91f5-2d34a1dcc1d4.png)

![22](https://user-images.githubusercontent.com/101863671/174575623-4131047d-ba1c-4cf3-8bbf-7a9d7f63a9b9.png)

![23](https://user-images.githubusercontent.com/101863671/174575648-19d0227a-3d7a-4406-b85c-bb09b551b6d1.png)

![24](https://user-images.githubusercontent.com/101863671/174575681-5d662f73-effa-47d4-af5a-bd1156cca257.png)

![25](https://user-images.githubusercontent.com/101863671/174575717-554e4099-ac78-402b-9a11-8371154ac6a9.png)

![26](https://user-images.githubusercontent.com/101863671/174575757-053ff7c5-42ee-467b-a722-38954b3e78a6.png)

# Praktikum 13: Framework Lanjutan (Modul Login)

## Langkah-langkah Praktikum
Untuk memulai membuat modul Login, yang perlu disiapkan adalah database server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui XAMPP.

## Membuat Tabel User

![1](https://user-images.githubusercontent.com/101863671/174578273-25996d58-0ff8-4e7f-aa33-16dd64713d5f.png)

## Membuat Model User
Selanjutnya adalah membuat Model untuk memproses data Login. Buat file baru pada direktori ```app/Models``` dengan nama ```UserModel.php```

![2](https://user-images.githubusercontent.com/101863671/174578620-3330b744-9d84-4e74-bc8e-5a0d4ed7a375.png)

## Membuat Controller User
Buat Controller baru dengan nama ```User.php``` pada direktori ```app/Controllers```. Kemudian tambahkan method ```index()``` untuk menampilkan daftar user, dan method ```login()``` untuk proses login.

![3](https://user-images.githubusercontent.com/101863671/174579179-2f1c28b4-dcc5-4d6b-a0fa-4970f689829e.png)

![4](https://user-images.githubusercontent.com/101863671/174579202-c4be2277-5ab9-4b41-a66c-80d97d6f3890.png)

## Membuat View Login
Buat direktori baru dengan nama ```user``` pada direktori ```app/views```, kemudian buat file baru dengan nama ```login.php```.

![5](https://user-images.githubusercontent.com/101863671/174579395-5e093143-c78a-4b72-acc4-9c6e773f4663.png)

## Membuat Database Seeder
Database seeder digunakan untuk membuat data dummy. Untuk keperluan ujicoba modul login, kita perlu memasukkan data user dan password kedaalam database. Untuk itu buat database seeder untuk tabel user. Buka CLI, kemudian tulis perintah berikut:

![6](https://user-images.githubusercontent.com/101863671/174579497-089b6566-c14c-4045-9fce-c598129ddcd6.png)

Selanjutnya, buka file ```UserSeeder.php``` yang berada di lokasi direktori ```/app/Database/Seeds/UserSeeder.php``` kemudian isi dengan kode berikut:

![7](https://user-images.githubusercontent.com/101863671/174579732-43bed28a-9d3b-4b92-bc44-22000cb9ef9c.png)

Selanjutnya buka kembali CLI dan ketik perintah berikut:

![8](https://user-images.githubusercontent.com/101863671/174579992-ba34bc79-416a-4967-b1c3-0274c9ec28b2.png)

## Uji Coba Login

Selanjutnya buka url http://localhost:8080/user/login seperti berikut:

![11](https://user-images.githubusercontent.com/101863671/174580108-e490af6b-dfdb-441b-9c49-a89a323ce5e7.png)

## Menambahkan Auth Filter
Selanjutnya membuat filer untuk halaman admin. Buat file baru dengan nama ```Auth.php``` pada direktori ```app/Filters```.

![12 (2)](https://user-images.githubusercontent.com/101863671/174580388-bac8975e-5ec4-4764-9c64-d4e87c73c572.png)

Selanjutnya buka file ```app/Config/Filters.php``` tambahkan kode berikut:

![13 (2)](https://user-images.githubusercontent.com/101863671/174581668-c949a020-4509-4efc-b454-6439f2804bc6.png)

Selanjutnya buka file ```app/Config/Routes.php``` dan sesuaikan kodenya.

![14(3)](https://user-images.githubusercontent.com/101863671/174581984-d6647eb2-5ff7-4029-af62-08cf0c6eec15.png)

## Percobaan Akses Menu Admin
Buka url dengan alamat http://localhost:8080/admin/artikel ketika alamat tersebut diakses maka, akan dimunculkan halaman login.

![18](https://user-images.githubusercontent.com/101863671/174696950-3232a4ab-caa5-4a28-acb2-522660e5d28a.png)

- Hasil setelah log in

![21 (2)](https://user-images.githubusercontent.com/101863671/174696850-563258e7-7199-4f42-8b95-cb31112db27b.png)

## Fungsi Logout
- Tambahkan method ```logout``` pada Controller User seperti berikut:

![15](https://user-images.githubusercontent.com/101863671/174582648-bb23e03b-7b5f-4bad-b463-6163c001ea82.png)

- Buka file ```admin_header.php``` di direktori ```app\view\template``` untuk menambahkan menu ```logout``` di header admin.

![16 (2)](https://user-images.githubusercontent.com/101863671/174699034-4fe53c2c-ca76-4c45-9b07-b51bc82aed60.png)

![21](https://user-images.githubusercontent.com/101863671/174698364-2709778f-c38e-4e10-afdf-6ebd2eadff03.png)

- Hasil setelah menekan tombol ```log out```

![20](https://user-images.githubusercontent.com/101863671/174584570-2263d660-da2e-4a4b-b0bb-5efbdd0a7579.png)

# Pertanyaan dan Tugas
## Selesaikan programnya sesuai langkah-langkah yang ada. Anda boleh melakukan improvisasi.
Saya telah menyelesaikan dari awal login hingga logout halaman admin, disini saya menambahkan Route logout dan css nya.

- Route Logout

![17 (2)](https://user-images.githubusercontent.com/101863671/174585440-1429cfa6-00b6-41e0-ad92-593f87970d49.png)

- Userstyle CSS

![9](https://user-images.githubusercontent.com/101863671/174585738-ca417a19-296f-46b9-86dd-31ce98802823.png)

![10](https://user-images.githubusercontent.com/101863671/174585754-2f9ad567-0339-4bee-9ef4-3a16ef17af8b.png)









