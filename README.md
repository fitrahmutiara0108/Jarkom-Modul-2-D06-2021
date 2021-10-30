# Jarkom-Modul-2-D06-2021

Anggota :
- Fitrah Mutiara 05111940000126
- Ahdan Amanullah Irfan Muzhaffar 05111940000197
- Dewi Mardani 05111940000225

## Soal 1
## Soal 2
## Soal 3
## Soal 4
## Soal 5
## Soal 6
## Soal 7
## Soal 8
Setelah melakukan konfigurasi server, maka dilakukan konfigurasi Webserver. Pertama dengan webserver `www.franky.yyy.com`. Pertama, luffy membutuhkan webserver dengan DocumentRoot pada `/var/www/franky.yyy.com`.
### Pada Skypie
- Lakukan penginstallan apache dan start
- install juga php
```
apt-get install apache2 
service apache2 start
apt-get install php 
apt-get install libapache2-mod-php7.0 
service apache2 
apt-get install ca-certificates openssl 
```
- Lalu konfigurasi file /etc/apache2/sites-available/franky.D06.com.conf seperti berikut
![image](https://user-images.githubusercontent.com/81247727/139520840-a6b7aaf2-4d12-45a7-9c6d-4e80d2ee892c.png)
- Kemudian membuat direktori root dan unzip file dari link github yang sudah disediakan di soal shift
![image](https://user-images.githubusercontent.com/81247727/139520871-5efb3adb-1a03-4c18-b2ce-5a1a7eef1d6d.png)
### Pada Loguetown
- Install lynx `apt-get install lynx`
- `lynx franky.D06.com` untuk Testing
- Hasilnya akan sebagai berikut:
![image](https://user-images.githubusercontent.com/81247727/139520905-b9903206-bed3-4dca-be83-ffe0998909d2.png)

## Soal 9
Setelah itu, Luffy juga membutuhkan agar url `www.franky.yyy.com/index.php/home` dapat menjadi menjadi `www.franky.yyy.com/home`.
### Pada Skypie
- Buat file `htaccesno9` yang berisi
```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule (.*) /index.php/\$1 [L]
```
- Kemudian buka file `/etc/apache2/sites-available/franky.D06.com.conf` dan tambahkan `cp htaccessno9 /var/www/franky.D06.com/.htaccess`
- Lakukan `service apache2 restart`
### Pada Loguetown
- jalankan `lynx www.franky.D06.com/home` untuk Testing
- Hasilnya akan sebagai berikut:
![image](https://user-images.githubusercontent.com/81247727/139521069-570e2a84-2e34-451d-b4fa-fe7e8ca6a71e.png)

## Soal 10
Setelah itu, pada subdomain `www.super.franky.yyy.com`, Luffy membutuhkan penyimpanan aset yang memiliki DocumentRoot pada `/var/www/super.franky.yyy.com`
### Pada Skypie
- Lakukan konfigurasi file pada `/etc/apache2/sites-available/franky.D06.com.conf`
![image](https://user-images.githubusercontent.com/81247727/139521144-a1e98540-1c34-4e34-98c5-8419d8ccb756.png)

## Soal 11
Akan tetapi, pada folder `/public`, Luffy ingin hanya dapat melakukan directory listing saja.
### Pada Skypie
- Lakukan konfigurasi file pada `/etc/apache2/sites-available/franky.D06.com.conf`
![image](https://user-images.githubusercontent.com/81247727/139521196-c88c727e-5006-4ecc-818a-8e9f7169ff8b.png)
### Pada Loguetown
- jalankan `lynx 'www.super.franky.D06.com/public`
- Hasilnya akan sebagai berikut:
![image](https://user-images.githubusercontent.com/81247727/139521386-93c42129-0b36-4426-bc94-b074dc94f30f.png)

## Soal 12
Tidak hanya itu, Luffy juga menyiapkan error file `404.html` pada folder `/error` untuk mengganti error kode pada apache 
### Pada Skypie
- Lakukan wget dan unzip file error dari link github yang sudah disediakan di soal shift
- Lakukan konfigurasi file pada `/etc/apache2/sites-available/franky.D06.com.conf`
![image](https://user-images.githubusercontent.com/81247727/139521348-b3411092-2ed9-44f8-a175-a2a78d28238e.png)
### Pada Loguetown
- jalankan misal `lynx www.super.franky.D06.com/yuhu`
- Hasilnya akan sebagai berikut:
![image](https://user-images.githubusercontent.com/81247727/139521415-2a4786a9-9002-4da0-a8ba-f9c5ac471c01.png)

## Soal 13
Luffy juga meminta Nami untuk dibuatkan konfigurasi virtual host. Virtual host ini bertujuan untuk dapat mengakses file asset `www.super.franky.yyy.com/public/js` menjadi `www.super.franky.yyy.com/js`. 
### Pada Skypie
- Lakukan konfigurasi file pada `/etc/apache2/sites-available/franky.D06.com.conf`
![image](https://user-images.githubusercontent.com/81247727/139521361-c523bb21-4b8f-4c86-8dfe-a8b0b3a78b50.png)
### Pada Loguetown
- jalankan `lynx 'www.super.franky.D06.com/js`
- Hasilnya akan sebagai berikut:
![image](https://user-images.githubusercontent.com/81247727/139521436-75dbe3a1-e4c4-41a2-851c-62f60500ede4.png)

## Soal 14
## Soal 15
## Soal 16
## Soal 17
