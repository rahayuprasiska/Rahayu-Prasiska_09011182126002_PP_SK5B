# MELAKUKAN INSTALASI WORDPRESS DI UBUNTU SERVER MENGGUNAKAN MYSQL DAN APACHE 2

## Langkah 1: Update Repository Ubuntu
  **1.	Jalankan perintah di bawah ini pada jendela Terminal di ubuntu server: sudo apt update**
    ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/787baaca-6dff-4156-adea-565ea1565eb1)

  **2.	Jalankan perintah di bawah ini pada jendela Terminal sudo apt upgrade**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/4e3d43a4-0b7d-494b-80d6-3facb8d1b154)

## Langkah 2: Install Apache2

  **1.	Jalankan perintah sudo apt install apache2 untuk memulai penginstalan Apache 2**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/b727a0ac-8300-4544-9b55-49394c737ecd)

  **2.	Selanjutnya, aktifkan Apache2 dengan dua perintah di bawah:**
  sudo systemctl start apache2
  
  sudo systemctl enable apache2
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/54a6caa9-3ac4-4578-a011-6541cfddf05a)

  **3.	Untuk memastikan bahwa Apache2 telah benar-benar aktif, bisa menuliskan command yang satu ini:**
  
  sudo systemctl status apache2
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/292c08c4-dee7-470c-ae34-52f4f5b9a04c)

## Langkah 3: Install PHP dan Modul yang berjalan di Apache2
  **1. Install modul php**

  sudo apt install php libapache2-mod-php php-mysql
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/de4aa024-c5f2-46be-b65a-14110ff60022)

  **2.	Setelah instalasi, pastikan PHP bekerja dengan Apache dengan baik:**

  sudo systemctl restart apache2
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/aa629bee-3132-400d-af13-7bb39bd28062)

## Langkah 4 : Instal Database Server (MySQL):

  **1.	Melakukan Installasi MySQL**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/1f6d4481-3822-45a2-955a-e04f06634a38)

  **2.	Setelah instalasi selesai, amankan instalasi mysql:**
  sudo mysql_secure_installation
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/463d60b3-a3ce-4ba8-b973-5ee6ee7239d9)

  **3.	Buat Database dan Pengguna Database Log masuk ke mysql sebagai root:** 
  
  sudo mysql
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/d700634b-d266-4201-87f4-b86f958dbbbb)

  **4.	Buat database baru dan pengguna database untuk WordPress. Gantilah `nama_database`, `nama_pengguna`, dan `password_pengguna`**

  CREATE DATABASE nama_database;
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/e69445d5-76ff-4ce7-acdf-6832ce2dfd2f)

  **5.	CREATE USER 'nama_pengguna'@'localhost' IDENTIFIED BY 'password_pengguna';**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/95932929-b5ee-4354-a0b2-6e39a057bccd)

  ### 6.	GRANT ALL PRIVILEGES ON rahayu_database.* TO 'rahayuprasiska'@'localhost';
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/be53f5fb-6a8d-45c8-8859-530c4d5c41c7)

  **7.	FLUSH PRIVILEGES;**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/7740ac9e-1c4b-4bec-9191-9935866bfbe8)

  **8.	EXIT;**
  
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/6d913833-8eab-4eee-ab7f-45f79e3ce5e0)

## Langkah 5: Install WordPress dengan Apache2

  **1.	Untuk memulai, masuk ke direktori /var/www/html dengan perintah:**
  cd /var/www/html
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/7612e828-4867-4f5f-865c-6cd99123354f)

  **2.	Selanjutnya, download file paket WordPress menggunakan command berikut:**
  sudo wget https://wordpress.org/latest.tar.gz
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/a25e788b-7dd4-408b-8302-baf611d1ea5f)

  **3.	Setelah file paket WordPress terunduh, ekstrak file tersebut lewat perintah yang satu ini:**
  sudo tar -xzvf latest.tar.gz
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/2d85b58d-7ec9-4bb1-8f1c-f09c3244c7ff)

  **4.	sudo mv wordpress nama_folder**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/bada16ef-3b5c-44fe-9dcf-257eb9d5b2ad)

## Langkah 6: Konfigurasi WordPress:

  **1.	Buat salinan file konfigurasi WordPress:**
  sudo cp /var/www/html/nama_folder/wp-config-sample.php /var/www/html/nama_folder/wp-config.php
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/e1659a31-4de2-4bb9-998a-92e45495c9c4)

  **2.	Selanjutnya, edit file wp-config.php:**
  sudo nano /var/www/html/nama_folder/wp-config.php
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/1144935c-6dc0-4943-883c-cf1cf14fae1b)

  **3.	Ganti konfigurasi database dengan informasi yang sesuai yang telah Anda buat sebelumnya:**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/3e603d69-3d88-4812-b360-1aa41d51ea46)

  **4.	Setel Hak Akses
  Pastikan Apache memiliki hak akses yang tepat ke folder WordPress:**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/e657b572-354a-437c-a1ea-cde98267c413)

  **5.	Konfigurasi Web Server
  Buat konfigurasi server web Apache untuk mengarahkan permintaan ke WordPress. Buat file konfigurasi baru:**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/65aa2dbf-f304-4663-bb08-08401dbbe2f4)

  **6.	Isi Konfigurasi:**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/8f1bdc9d-b7f4-48fb-9945-219666ea0565)

## Langkah 7: Aktifkan Konfigurasi dan restart Apache

  **1.	Aktifkan konfigurasi situs dan restart Apache:**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c005ba5a-4630-45bd-8b0a-ef71e7c1ddb3)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/304d4a98-643f-4323-9386-9d5e5244a532)

  **2.	Cek status keaktifan apache2:**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c31da212-689d-4282-bf19-d191d2872c2a)

## Langkah 8: Akses WordPress di Ubuntu Server

  **1.	Buka web browser Anda dan ketikkan alamat domain atau alamat IP milik server Ubuntu.
  Pilih bahasa yang akan digunakan di WordPress**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/d1110cb8-63c1-4f6e-ac87-91bd3d9c73cb)

  **2.	Masukkan informasi untuk login ke WordPressnya**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/7708a2de-25f6-4114-9662-530d53fa083a)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/fc5bc3ba-d18f-4ff4-9137-6f8da7f7f4a6)

  **3.	Masukkan Nama pengguna dan sandi yang telah saya buat sebelumnya**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/5e2118a0-ea37-4537-9bf1-9e29ca488808)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/8d11080e-cd22-4800-a21e-2a21887bf698)

  **4.	Ini adalah tampilan pertama ketika kita berhasil login di akuun WordPress**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/c7a01ca7-2c90-4774-8672-4d729febd76c)

  **5.	Berikut adalah tampilan WordPress yang telah saya buat**
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/f4d87a65-82c5-4fd0-a547-e7ea56db65c2)
  ![image](https://github.com/rahayuprasiska/Rahayu-Prasiska_09011182126002_PP_SK5B/assets/119491151/66683787-9cac-471f-90e9-46d30a3ca669)
