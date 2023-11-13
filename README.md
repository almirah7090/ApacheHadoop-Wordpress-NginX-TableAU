# ApacheHadoop
1. Login sebagai user dengan menggunakan nama dan kata sandi Anda. ![1](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/f0d907e5-db98-4c70-92a1-da862ce5e60d)
2. Gunakan perintah `sudo apt update` untuk memperbarui daftar paket yang tersedia di repositori Ubuntu. ![3](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/99af6b3a-11a7-4354-a047-c6bec274d06a)


3. Menginstall apache dengan perintah `sudo apt install apache2`. Anda akan diminta untuk memasukkan kata sandi Anda dan mengetik Y untuk melanjutkan instalasi. ![4](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/2ff0d402-9389-4b6d-8fd9-2c63b19fe77c)

4. Mengecek aplikasi yang diinstal dengan perintah `sudo ufw app list`. Anda akan melihat daftar aplikasi yang terdaftar di firewall Ubuntu, termasuk Apache Full, Apache Secure, dan OpenSSH. ![5](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/5e2066d8-8309-4727-b997-0db13d560ff7)

5. Gunakan perintah `sudo systemctl status apache2` untuk mengecek status layanan apache. Anda akan melihat informasi seperti versi apache, status aktif atau tidak, dan proses yang berjalan. ![5](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/1adeb20f-a215-4657-b260-d199d55d8b8a)

6. Mengecek apakah status apache telah aktif dengan perintah `sudo ufw status`. Apabila statusnya inactive, maka Anda perlu mengaktifkan firewall dengan mengetik `sudo ufw enable`. Anda juga perlu mengizinkan akses ke apache dengan mengetik `sudo ufw allow 'Apache Full'`. ![6](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/57bc796d-dc7c-4441-8c5f-1b71a55ae9c5)

7. Gunakan perintah `hostname -I` untuk melihat alamat IP Anda. Anda akan melihat satu atau lebih angka yang dipisahkan oleh spasi, seperti 10.1.41.66. ![6](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/9008094f-3e9e-4748-8ab2-ded197e7c19b)

8. Mengecek apache2 pada alamat IP Anda dengan membuka browser web Anda dan mengetikkan alamat IP Anda di bilah alamat. Anda akan melihat halaman web default apache yang menampilkan pesan "It works!". ![7](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/75501c51-1566-457f-894e-cc53a6578917)

9. Masuk ke direktori `/var/www/html` dengan mengetik `cd /var/www/html`. Direktori ini adalah tempat di mana file-file web apache disimpan. ![8](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/87f1c490-2278-4382-b815-8a8a957e8adc)

10. Mengedit file `index.html` dengan menggunakan editor teks yang Anda sukai, seperti nano, vim, atau gedit. Anda dapat menambahkan atau mengubah konten HTML sesuai dengan keinginan Anda. ![9](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/628e9cfd-a0ad-4f6c-b3f5-8d056511eef5)

11. Tampilan di website akan berubah sesuai dengan perubahan yang Anda lakukan pada file `index.html`. Anda dapat merefresh browser Anda untuk melihat hasilnya. ![11](https://github.com/almirah7090/ApacheHadoop-Wordpress-NginX-TableAU/assets/150506744/5f9ff4bb-8739-4891-9982-fe896a3c5030)

# Wordpress
# NginX
# TableAU
