# Apache 
## Cara Menampilkan Apache pada Ubuntu dan Remote ke CMD, PuTTY, dan Ubuntu Desktop
Apache adalah web server yang populer dan dapat digunakan untuk melayani berbagai jenis konten web, seperti HTML, PHP, Python, dan lainnya. 

## Prasyarat
- Sebuah server Ubuntu yang sudah terhubung dengan internet
- Seorang user yang memiliki hak sudo
- Sebuah domain atau alamat IP yang sudah diarahkan ke server Ubuntu
- Sebuah komputer atau laptop yang dapat mengakses server Ubuntu melalui SSH
- Sebuah aplikasi SSH client, seperti CMD, PuTTY, atau Ubuntu Desktop

## Langkah-langkah
### Menampilkan Apache pada Ubuntu
1. Login sebagai user dengan menggunakan nama dan kata sandi Anda. 
2. Gunakan perintah `sudo apt update` untuk memperbarui daftar paket yang tersedia di repositori Ubuntu.
3. Menginstal apache dengan perintah `sudo apt install apache2`. Anda akan diminta untuk memasukkan kata sandi Anda dan mengetik Y untuk melanjutkan instalasi.
4. Mengecek aplikasi yang diinstal dengan perintah `sudo ufw app list`. Anda akan melihat daftar aplikasi yang terdaftar di firewall Ubuntu, termasuk Apache Full, Apache Secure, dan OpenSSH. 
5. Gunakan perintah `sudo systemctl status apache2` untuk mengecek status layanan apache. Anda akan melihat informasi seperti versi apache, status aktif atau tidak, dan proses yang berjalan.
6. Mengecek apakah status apache telah aktif dengan perintah `sudo ufw status`. Apabila statusnya inactive, maka Anda perlu mengaktifkan firewall dengan mengetik `sudo ufw enable`. Anda juga perlu mengizinkan akses ke apache dengan mengetik `sudo ufw allow 'Apache Full'`.
7. Gunakan perintah `hostname -I` untuk melihat alamat IP Anda. Anda akan melihat satu atau lebih angka yang dipisahkan oleh spasi, seperti 10.1.41.66.
8. Mengecek apache2 pada alamat IP Anda dengan membuka browser web Anda dan mengetikkan alamat IP Anda di bilah alamat. Anda akan melihat halaman web default apache yang menampilkan pesan "It works!".
![7](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/826783ef-a7e4-4512-b308-6a7f03660a38)
9. Masuk ke direktori `/var/www/html` dengan mengetik `cd /var/www/html`. Direktori ini adalah tempat di mana file-file web apache disimpan.
10. Mengedit file `index.html` dengan menggunakan editor teks yang Anda sukai, seperti nano, vim, atau gedit. Anda dapat menambahkan atau mengubah konten HTML sesuai dengan keinginan Anda. 
11. Tampilan di website akan berubah sesuai dengan perubahan yang Anda lakukan pada file `index.html`. Anda dapat merefresh browser Anda untuk melihat hasilnya.
![11](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/2428cbdd-9d96-42fe-a282-13ee318c820e)

### Remote ke CMD
1. Login ke dalam CMD dengan perintah `ssh user@ip address`. Ganti `user` dengan nama user Anda dan `ip address` dengan alamat IP server Anda. Anda akan diminta untuk memasukkan kata sandi Anda dan mengetik yes untuk menerima kunci host.
2. Setelah login, Anda dapat melakukan perintah-perintah dasar pada command prompt, seperti `ls`, `cd`, `pwd`, `cat`, `nano`, dan lainnya. Anda juga dapat mengakses file-file web apache yang terletak di direktori `/var/www/html`.

### Remote ke PuTTY
1. Buka aplikasi PuTTY dan masukkan hostname atau alamat IP server Anda di kolom yang tersedia. Pastikan port yang digunakan adalah 22 dan connection type adalah SSH. Klik Open untuk memulai koneksi.
2. Login ke PuTTY dengan menggunakan nama dan kata sandi user Anda. Anda akan diminta untuk mengetik yes untuk menerima kunci host.
3. Setelah login, Anda dapat melakukan perintah-perintah dasar pada terminal PuTTY, sama seperti pada CMD. Anda juga dapat mengakses file-file web apache yang terletak di direktori `/var/www/html`.

### Remote ke Ubuntu Desktop
1. Buka terminal Ubuntu Desktop dan login ke server Ubuntu dengan perintah `ssh user@ip.address`. Ganti `user` dengan nama user Anda dan `ip address` dengan alamat IP server Anda. Anda akan diminta untuk memasukkan kata sandi Anda dan mengetik yes untuk menerima kunci host.
2. Setelah login, Anda dapat melakukan perintah-perintah dasar pada terminal Ubuntu Desktop, sama seperti pada CMD atau PuTTY. Anda juga dapat mengakses file-file web apache yang terletak di direktori `/var/www/html`.


# Wordpress
## Cara Menginstal dan Menjalankan WordPress di Ubuntu Server
WordPress adalah sistem manajemen konten (CMS) yang populer dan mudah digunakan untuk membuat dan mengelola situs web. WordPress dapat digunakan untuk membuat berbagai jenis situs web, seperti blog, toko online, portofolio, dan lainnya.

## Prasyarat
- Sebuah server Ubuntu yang sudah terhubung dengan internet
- Seorang user yang memiliki hak sudo
- Sebuah domain atau alamat IP yang sudah diarahkan ke server Ubuntu
- Sebuah web server Apache yang sudah terinstal dan dikonfigurasi
- Sebuah server basis data MariaDB yang sudah terinstal dan dikonfigurasi
- Sebuah bahasa pemrograman PHP yang sudah terinstal dan dikonfigurasi

## Langkah-langkah
1. Login sebagai user dengan menggunakan nama dan kata sandi Anda. 
2. Gunakan perintah `apt update && apt upgrade` untuk memperbarui dan meng-upgrade paket di sistem Anda.
3. Gunakan perintah `apt install apache2` untuk menginstal server web Apache jika belum terinstal.
4. Gunakan perintah `systemctl status apache2` untuk memeriksa status layanan Apache. Anda akan melihat output seperti ini:
```
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2021-11-10 10:41:08 UTC; 2min 17s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 2370 ExecStartPre=/usr/sbin/apache2ctl graceful-stop (code=exited, status=0/SUCCESS)
    Process: 2384 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
   Main PID: 2385 (apache2)
      Tasks: 55 (limit: 1137)
     Memory: 6.7M
     CGroup: /system.slice/apache2.service
             ├─2385 /usr/sbin/apache2 -k start
             ├─2386 /usr/sbin/apache2 -k start
             └─2387 /usr/sbin/apache2 -k start
```
5. Gunakan perintah `apt install mariadb-server mariadb-client` untuk menginstal server basis data MariaDB jika belum terinstal.
6. Gunakan perintah `$ mysql_secure_installation` untuk menjalankan skrip keamanan untuk mengamankan instalasi MariaDB. Anda akan diminta untuk memasukkan kata sandi root, membuat kata sandi baru, menghapus basis data anonim, menonaktifkan login root dari jarak jauh, menghapus hak akses tes, dan memuat ulang tabel hak akses.
7. Gunakan perintah `apt install php php-mysql` untuk menginstal PHP dan ekstensi MySQL jika belum terinstal.
8. Gunakan perintah `nano /var/www/html/info.php` untuk membuat berkas info.php untuk memeriksa konfigurasi PHP. Anda dapat menulis kode PHP berikut di berkas tersebut:
```
<?php
phpinfo();
?>
```
9. Simpan dan keluar dari editor nano dengan menekan Ctrl+X, kemudian Y, kemudian Enter.
10. Buka browser web Anda dan ketikkan alamat IP server Anda diikuti dengan /info.php, misalnya http://203.0.113.111/info.php. Anda akan melihat halaman informasi PHP yang menampilkan versi, ekstensi, variabel, dan lainnya.
11. Hapus berkas info.php dengan perintah `rm /var/www/html/info.php` untuk menghindari risiko keamanan.
12. Gunakan perintah `mysql -u root -p` untuk mengakses shell MySQL sebagai pengguna root. Anda akan diminta untuk memasukkan kata sandi root yang telah Anda buat sebelumnya.
13. Buat basis data untuk WordPress dengan perintah `CREATE DATABASE wordpress;`. Anda akan melihat output seperti ini:
```
Query OK, 1 row affected (0.00 sec)
```
14. Buat pengguna untuk WordPress dengan perintah `CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'password';`. Ganti `password` dengan kata sandi yang kuat dan unik. Anda akan melihat output seperti ini:

```
Query OK, 0 rows affected (0.00 sec)
```
15. Berikan hak akses penuh ke pengguna WordPress untuk basis data WordPress dengan perintah `GRANT ALL ON wordpress.* TO 'wordpressuser'@'localhost';`. Anda akan melihat output seperti ini:
```
Query OK, 0 rows affected (0.00 sec)
```
16. Muat ulang tabel hak akses dengan perintah `FLUSH PRIVILEGES;`. Anda akan melihat output seperti ini:
```
Query OK, 0 rows affected (0.00 sec)
```
17. Keluar dari shell MySQL dengan perintah `exit;`. Anda akan melihat output seperti ini:
```
Bye
```
18. Masuk ke direktori `/tmp` dengan perintah `cd /tmp` dan unduh paket terbaru WordPress dengan perintah `wget https://wordpress.org/latest.tar.gz`.
19. Ekstrak paket WordPress yang telah diunduh dengan perintah `tar -xvf latest.tar.gz`. Anda akan melihat output seperti ini:
```
wordpress/
wordpress/wp-settings.php
wordpress/wp-cron.php
wordpress/wp-comments-post.php
wordpress/wp-activate.php
wordpress/wp-admin/
wordpress/wp-admin/install.php
wordpress/wp-admin/admin-footer.php
wordpress/wp-admin/options-writing.php
...
```
20. Salin isi direktori WordPress ke direktori root Apache dengan perintah `cp -R wordpress /var/www/html/`.
21. Ubah kepemilikan direktori WordPress ke pengguna web server dengan perintah `chown -R www-data:www-data /var/www/html/wordpress/`.
22. Atur izin direktori WordPress sesuai standar keamanan dengan perintah `chmod -R 755 /var/www/html/wordpress/`.
23. Buat direktori untuk unggahan di WordPress dengan perintah `$ mkdir /var/www/html/wordpress/wp-content/uploads`.
24. Ubah kepemilikan direktori unggahan ke pengguna web server dengan perintah `chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads/`.
25. Kunjungi situs web WordPress yang baru diinstal melalui alamat IP server Anda diikuti dengan /wordpress, misalnya http://196.142.1.96/wordpress. Anda akan melihat halaman instalasi WordPress yang menampilkan pilihan bahasa. Pilih bahasa yang Anda inginkan dan klik Continue.
26. Anda akan diminta untuk memasukkan informasi situs web Anda, seperti judul, nama pengguna, kata sandi, alamat email, dan pilihan mesin pencari. Isi informasi tersebut dan klik Install WordPress.
27. Anda akan melihat halaman yang menampilkan pesan "Success! WordPress has been installed.". Klik Log In untuk masuk ke dashboard WordPress dengan menggunakan nama pengguna dan kata sandi yang telah Anda buat sebelumnya.
28. Anda akan melihat halaman dashboard WordPress yang menampilkan berbagai menu, widget, dan fitur. Anda dapat mengelola situs web Anda dari sini, seperti membuat dan mengedit postingan, halaman, tema, plugin, pengguna, dan lainnya.
![28](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/bf21cb40-932f-41e5-b84c-8b06378a7659)


# NginX
## Cara Menginstal dan Menjalankan Nginx di Ubuntu Server
Nginx adalah web server yang populer dan ringan yang dapat digunakan untuk melayani konten statis maupun dinamis. Nginx juga dapat berfungsi sebagai reverse proxy, load balancer, atau HTTP cache.

## Prasyarat
- Sebuah server Ubuntu yang sudah terhubung dengan internet
- Seorang user yang memiliki hak sudo
- Sebuah domain yang sudah diarahkan ke alamat IP server

## Langkah-langkah
1. Login sebagai user di ubuntu server dengan menggunakan SSH atau terminal
2. Gunakan perintah `sudo apt update` untuk memperbarui daftar paket yang tersedia
3. Menginstal Nginx dengan perintah `sudo apt install nginx`
4. Mengecek aplikasi yang diinstal dengan perintah `sudo ufw app list`. Anda akan melihat output seperti ini:
```
Available applications:
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
```
5. Mengizinkan lalu lintas ke server web Nginx dengan perintah `sudo ufw allow 'Nginx HTTP'`. Anda juga dapat mengizinkan HTTPS jika Anda menggunakan SSL/TLS. Gunakan perintah `sudo ufw status` untuk memeriksa status firewall. Apabila status yang ditampilkan `inactive`, maka harus diaktifkan terlebih dahulu dengan perintah `sudo ufw enable`
6. Memeriksa status layanan Nginx dengan perintah `systemctl status nginx`. Anda akan melihat output seperti ini:
```
● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2021-11-10 10:41:08 UTC; 2min 17s ago
       Docs: man:nginx(8)
    Process: 2370 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
    Process: 2384 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Main PID: 2385 (nginx)
      Tasks: 3 (limit: 1137)
     Memory: 3.5M
     CGroup: /system.slice/nginx.service
             ├─2385 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
             ├─2386 nginx: worker process
             └─2387 nginx: worker process
```
7. Mencari alamat IP server dengan perintah `curl -4 icanhazip.com`. Anda akan melihat output seperti ini:
```
10.1.42.123
```
8. Membuka browser dan mengakses alamat IP server. Anda akan melihat halaman default Nginx seperti ini:
![8](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/bab5e6af-5f09-47b0-a63e-f5eb4622a6fb)

## Perintah yang digunakan untuk mengelola layanan Nginx
- Menghentikan layanan Nginx dengan perintah `sudo systemctl stop nginx`
- Menjalankan ulang layanan Nginx dengan perintah `sudo systemctl start nginx`
- Merestart layanan Nginx dengan perintah `sudo systemctl restart nginx`
- Memuat ulang konfigurasi Nginx dengan perintah `sudo systemctl reload nginx`
- Menonaktifkan layanan Nginx saat startup dengan perintah `sudo systemctl disable nginx`
- Mengaktifkan layanan Nginx saat startup dengan perintah `sudo systemctl enable nginx`

## Cara membuat direktori dan berkas untuk domain
- Membuat direktori untuk domain dengan perintah `sudo mkdir -p /var/www/your_domain/html`. Ganti `your_domain` dengan nama domain Anda.
- Mengubah kepemilikan direktori dengan perintah `sudo chown -R $USER:$USER /var/www/your_domain/html`. Ini akan memungkinkan user Anda untuk menulis ke direktori tersebut.
- Mengatur izin untuk direktori dengan perintah `sudo chmod -R 755 /var/www/your_domain`. Ini akan memungkinkan user lain untuk membaca dan mengeksekusi berkas di direktori tersebut, tetapi hanya user Anda yang dapat menulis.
- Mengedit berkas index.html dengan perintah `sudo nano /var/www/ your_domain /html/index.html`. Ini akan membuka editor nano di terminal. Anda dapat menulis konten HTML yang Anda inginkan di sini. Misalnya:
```
<html>
    <head>
        <title>Welcome to Your Domain</title>
    </head>
    <body>
        <h1>Hello, world!</h1>
        <p>This is the index.html file for your domain.</p>
    </body>
</html>
```
- Menyimpan dan keluar dari editor nano dengan menekan Ctrl+X, kemudian Y, kemudian Enter.

## Cara mengedit konfigurasi Nginx untuk domain
- Mengedit konfigurasi Nginx untuk domain dengan perintah `sudo nano /etc/nginx/sites-available/ your_domain`. Ini akan membuka editor nano di terminal. Anda dapat menulis konfigurasi Nginx yang Anda inginkan di sini. Misalnya:
```
server {
        listen 80;
        listen [::]:80;

        root /var/www/your_domain/html;
        index index.html index.htm index.nginx-debian.html;

        server_name your_domain www.your_domain;

        location / {
                try_files $uri $uri/ =404;
        }
}
```
- Menyimpan dan keluar dari editor nano dengan menekan Ctrl+X, kemudian Y, kemudian Enter.
- Membuat tautan simbolik dari konfigurasi ke direktori konfigurasi aktif dengan perintah `sudo ln -s /etc/nginx/sites-available/ your_domain /etc/nginx/sites-enabled/`. Ini akan memungkinkan Nginx untuk membaca konfigurasi Anda saat dijalankan.
- Mengedit berkas konfigurasi utama Nginx dengan perintah `sudo nano /etc/nginx/nginx.conf`. Ini akan membuka editor nano di terminal. Anda perlu mencari baris berikut:
```
# server_names_hash_bucket_size 64;
```
- Menghapus tanda `#` di awal baris tersebut untuk mengaktifkan opsi tersebut. Ini akan memungkinkan Nginx untuk membaca nama server yang panjang.
- Menyimpan dan keluar dari editor nano dengan menekan Ctrl+X, kemudian Y, kemudian Enter.
- Memeriksa keabsahan konfigurasi Nginx dengan perintah `sudo nginx -t`. Anda akan melihat output seperti ini:
```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
- Merestart layanan Nginx dengan perintah `sudo systemctl restart nginx` untuk menerapkan perubahan konfigurasi.
- Membuka browser dan mengakses nama domain Anda. Anda akan melihat halaman yang Anda buat sebelumnya seperti ini:
![19](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/e9092da0-b340-479b-8e4c-f99e8b708ed2)


# TableAU
## Cara Instalasi, Aktivasi, Registrasi, dan Visualisasi Data dengan Tableau Desktop Public
Tableau Desktop Public adalah aplikasi yang dapat digunakan untuk membuat dan membagikan visualisasi data secara interaktif. Tableau Desktop Public dapat diunduh secara gratis dan mendukung berbagai jenis sumber data, seperti file Excel, CSV, JSON, dan lainnya. Dalam tutorial ini, Anda akan belajar cara instalasi, aktivasi, registrasi, dan visualisasi data dengan Tableau Desktop Public.

## Prasyarat
- Sebuah komputer atau laptop yang menggunakan sistem operasi Windows
- Sebuah koneksi internet yang stabil
- Sebuah akun email yang valid
- Sebuah file data yang ingin divisualisasikan, misalnya daftar nilai UAS Pengantar Teknik Komputer SKREG tahun 2022

## Langkah-langkah
### Instalasi Tableau Desktop Public
1. Buka browser web Anda dan kunjungi situs web Tableau Public di [https://public.tableau.com/en-us/s/download].
2. Klik tombol Download the App yang berwarna biru. Anda akan diarahkan ke halaman unduhan Tableau Desktop Public.
3. Klik tombol Download Tableau Public for Windows yang berwarna biru. Anda akan diminta untuk menyimpan file instalasi TableauPublicDesktop-64bit-2021-3-1.exe di komputer Anda.
4. Setelah file instalasi selesai diunduh, buka file tersebut dan ikuti petunjuk yang muncul di layar untuk menginstal Tableau Desktop Public. Anda akan diminta untuk menyetujui persyaratan lisensi, memilih lokasi instalasi, dan menunggu proses instalasi selesai.
5. Setelah instalasi selesai, klik tombol Finish untuk keluar dari wizard instalasi. Anda akan melihat ikon Tableau Desktop Public di desktop Anda.

### Aktivasi dan Registrasi Tableau Desktop Public
1. Buka aplikasi Tableau Desktop Public dengan mengklik dua kali ikonnya di desktop Anda. Anda akan melihat halaman selamat datang Tableau Desktop Public yang menampilkan pilihan untuk membuat koneksi data, membuka workbook, dan mempelajari lebih lanjut tentang Tableau.
2. Klik tombol Sign In yang berada di pojok kanan atas halaman. Anda akan diminta untuk memasukkan alamat email dan kata sandi Tableau Public Anda. Jika Anda belum memiliki akun Tableau Public, klik tombol Create one now untuk membuat akun baru.
3. Isi formulir pendaftaran dengan memasukkan nama, alamat email, kata sandi, dan negara Anda. Centang kotak I agree to the Tableau Terms of Service and Privacy Policy untuk menyetujui persyaratan layanan dan kebijakan privasi Tableau. Klik tombol Sign Up untuk menyelesaikan pendaftaran.
4. Anda akan menerima email konfirmasi dari Tableau Public yang berisi tautan untuk mengaktifkan akun Anda. Buka email tersebut dan klik tautan yang disediakan. Anda akan diarahkan ke halaman Tableau Public yang menampilkan pesan "Your account is now active".
5. Kembali ke aplikasi Tableau Desktop Public dan masukkan alamat email dan kata sandi Tableau Public Anda. Klik tombol Sign In untuk masuk ke akun Anda. Anda akan melihat halaman selamat datang Tableau Desktop Public yang menampilkan nama dan foto profil Anda di pojok kanan atas.

### Visualisasi Data dengan Tableau Desktop Public
1. Pilih sumber data yang ingin Anda visualisasikan dengan mengklik salah satu ikon yang tersedia di halaman selamat datang Tableau Desktop Public, misalnya Excel, Text File, JSON File, dan lainnya. Dalam contoh ini, kita akan menggunakan file Excel yang berisi daftar nilai UAS Pengantar Teknik Komputer SKREG tahun 2022.
2. Cari dan pilih file Excel yang ingin Anda gunakan dengan mengklik tombol Open. Anda akan melihat halaman Data Source yang menampilkan nama file, lembar kerja, dan kolom data Anda. Anda dapat memeriksa dan mengedit sumber data Anda di sini, seperti mengganti nama, mengubah tipe data, menghapus kolom, dan lainnya.
3. Klik tombol Sheet 1 yang berada di bagian bawah halaman untuk beralih ke halaman Worksheet. Anda akan melihat halaman Worksheet yang menampilkan Data Pane, Cards, Shelves, Marks, dan Canvas. Anda dapat membuat visualisasi data Anda di sini dengan menggunakan fitur-fitur yang tersedia di Tableau Desktop Public.
4. Untuk membuat visualisasi data yang menampilkan kelas dan nilai UAS, Anda dapat melakukan langkah-langkah berikut:
    - Seret kolom Kelas dari Data Pane ke Columns Shelf. Anda akan melihat label kelas muncul di sumbu horizontal Canvas.
    - Seret kolom Score dari Data Pane ke Rows Shelf. Anda akan melihat skala nilai muncul di sumbu vertikal Canvas.
    - Seret kolom Score dari Data Pane ke Marks Card. Anda akan melihat pilihan untuk mengubah tipe mark, agregasi, dan warna nilai.
    - Ubah tipe mark menjadi Bar dengan mengklik ikon drop-down di Marks Card dan memilih Bar. Anda akan melihat batang-batang yang merepresentasikan nilai UAS muncul di Canvas.
    - Ubah agregasi nilai menjadi Average dengan mengklik ikon drop-down di Marks Card dan memilih Average. Anda akan melihat batang-batang yang merepresentasikan rata-rata nilai UAS muncul di Canvas.
    - Ubah warna nilai dengan mengklik ikon drop-down di Marks Card dan memilih Color. Anda akan melihat pilihan untuk mengubah skema warna, rentang warna, dan transparansi nilai.
    - Pilih skema warna yang Anda inginkan, misalnya Orange-Blue Diverging. Anda akan melihat warna batang-batang berubah sesuai dengan skema warna yang dipilih. Warna yang paling terang menunjukkan nilai yang paling tinggi, dan warna yang paling gelap menunjukkan nilai yang paling rendah.
5. Anda dapat menambahkan judul, keterangan, dan elemen lainnya ke visualisasi data Anda dengan menggunakan fitur-fitur yang tersedia di menu Worksheet, Format, dan Dashboard. Anda juga dapat membuat visualisasi data lainnya dengan menggunakan data yang sama atau berbeda dengan mengklik tombol New Worksheet atau New Dashboard yang berada di bagian bawah halaman.
6. Untuk menyimpan data yang telah divisualisasikan, Anda perlu untuk meng-upload data tersebut ke web Tableau Public. Anda dapat melakukannya dengan mengklik menu File dan memilih Save to Tableau Public As. Anda akan diminta untuk memberi nama workbook Anda dan memilih apakah Anda ingin menyertakan data eksternal atau tidak. Klik tombol Save untuk meng-upload workbook Anda ke web Tableau Public. Anda akan melihat halaman web Tableau Public yang menampilkan workbook Anda. Anda dapat membagikan workbook Anda dengan orang lain dengan menggunakan tautan atau kode semat yang disediakan.
![10](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/d1b50926-07a9-4350-8102-b6302fe4bec1)

