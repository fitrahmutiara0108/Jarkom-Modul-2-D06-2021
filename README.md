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
Dan Luffy meminta untuk web www.general.mecha.franky.yyy.com hanya bisa diakses dengan port 15000 dan port 15500
### Pada Skypie
Pertama kita konfigurasi untuk ports yang akan dilisten pada `/etc/apache2/ports.conf`
```
echo "Listen 15000
Listen 15500" >> /etc/apache2/ports.conf
```

Lakukan konfigurasi untuk membuat konfigurasi pada `/etc/apache2/sites-available/general.mecha.franky.D06.com.conf`
```
<VirtualHost *:15000 *:15500>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/general.mecha.franky.D06.com
        ServerName general.mecha.franky.D06.com
        ServerAlias www.general.mecha.franky.D06.com

        ErrorLog /error.log
        CustomLog /access.log combined
</VirtualHost>
```

lalu kita akan mendownload file untuk general.mecha.franky.D06.com dengan script berikut:
```
mkdir /var/www/general.mecha.franky.D06.com
wget https://github.com/FeinardSlim/Praktikum-Modul-2-Jarkom/raw/main/general.mecha.franky.zip -P /var/www/general.mecha.franky.D06.com
unzip /var/www/general.mecha.franky.D06.com/general.mecha.franky.zip -d /var/www/general.mecha.franky.D06.com
mv -v /var/www/general.mecha.franky.D06.com/general.mecha.franky/* /var/www/general.mecha.franky.D06.com/
rm -r /var/www/general.mecha.franky.D06.com/general.mecha.franky
rm /var/www/general.mecha.franky.D06.com/general.mecha.franky.zip
```
lalu lakukan perintah `a2ensite general.mecha.franky.D06.com.conf` dan restart service apache2 pada Skypie.

Test menggunakan node client (Loguetown/Alabasta):

![image](https://user-images.githubusercontent.com/58657135/139524991-6596ba5b-e755-4d97-8e24-e5dd13ed7791.png)

![image](https://user-images.githubusercontent.com/58657135/139525064-28519c7e-5282-43f4-9245-055d3efdd9df.png)

![image](https://user-images.githubusercontent.com/58657135/139525081-cbf6f803-cce3-4b2d-a974-7a92dffcfa91.png)

## Soal 15
dengan autentikasi username luffy dan password onepiece dan file di /var/www/general.mecha.franky.yyy
### Pada Skypie
Tambahkan konfigurasi pada `/etc/apache2/sites-available/general.mecha.franky.D06.com.conf` sehingga seperti ini:
```
<VirtualHost *:15000 *:15500>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/general.mecha.franky.D06.com
        ServerName general.mecha.franky.D06.com
        ServerAlias www.general.mecha.franky.D06.com

        <Directory /var/www/general.mecha.franky.D06.com>
                AuthType Basic
                AuthName "Restricted Content"
                AuthUserFile /var/www/general.mecha.franky.D06.com/pass
                Require valid-user
        </Directory>

        ErrorLog /error.log
        CustomLog /access.log combined
</VirtualHost>
```
![image](https://user-images.githubusercontent.com/58657135/139525108-8255b852-4f0c-426f-8acc-7fb7dc6f0a66.png)

Lalu jalankan script berikut untuk menambahkan username dan password pada file `/var/www/general.mecha.franky.D06.com/pass`:
```
htpasswd -b -c /var/www/general.mecha.franky.D06.com/pass luffy onepiece
```
Jangan lupa untuk melakukan restart pada service Apache2.

Test di client:
![image](https://user-images.githubusercontent.com/58657135/139525260-93159bf4-1676-45b4-9234-7133efaacc2b.png)

![image](https://user-images.githubusercontent.com/58657135/139525265-6df68666-eae1-4339-8395-3e5ff48e2dcb.png)

![image](https://user-images.githubusercontent.com/58657135/139525268-8456cf29-4bdf-4e32-b105-73cbe8d7daa7.png)

![image](https://user-images.githubusercontent.com/58657135/139525276-404a4585-e01c-4d79-9bbb-c6f8a0886b43.png)


## Soal 16
Dan setiap kali mengakses IP Skypie akan dialihkan secara otomatis ke www.franky.yyy.com

### Pada Skypie
Kita tinggal melakukan edit konfigurasi pada DocumentRoot di `/etc/apache2/sites-available/000-default.conf` agar mengarah ke DocumentRoot franky.D06.com seperti ini:
```conf
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/franky.D06.com

        ErrorLog /error.log
        CustomLog /access.log combined
</VirtualHost>
```

Lalu kita coba tes menggunakan client:

![image](https://user-images.githubusercontent.com/58657135/139525348-6a37e87b-7b4e-4ff6-9337-7ad1eec9cea8.png)

![image](https://user-images.githubusercontent.com/58657135/139525351-cc6554c0-8f6c-44b5-aa94-bbed6a21d80e.png)


## Soal 17
Dikarenakan Franky juga ingin mengajak temannya untuk dapat menghubunginya melalui website www.super.franky.yyy.com, dan dikarenakan pengunjung web server pasti akan bingung dengan randomnya images yang ada, maka Franky juga meminta untuk mengganti request gambar yang memiliki substring “franky” akan diarahkan menuju franky.png.

### Pada Skypie
Kita perlu menggunakan Rewrite module untuk redirect semua request access yang mengandung kata 'franky' ke file '/public/images/franky.png'. Tambahkan konfigurasi berikut ke konfigurasi `/etc/apache2/sites-available/super.franky.D06.com.conf`:
```conf
<Directory /var/www/super.franky.D06.com/public/images>
    RewriteEngine On
    RewriteBase "/"
    RewriteCond "%{REQUEST_URI}" "(?=^.*franky.*$)(?=^(?!.*(franky.png)))"
    RewriteRule "^" "http://%{HTTP_HOST}/public/images/franky.png" [R,L]
</Directory>
```

Kita gunakan regex untuk redirect semua yang mengandung kata franky dan menghindari kata franky.png agar tidak terjadi bad request:
![image](https://user-images.githubusercontent.com/58657135/139525506-23f7beb7-2339-4ba8-bf1e-7116c1788016.png)

Jangan lupa untuk melakukan restart pada service apache2.

Test pada client:
Pertama coba dengan langsung request pada franky.png:
![image](https://user-images.githubusercontent.com/58657135/139525541-1343ddcc-4985-4362-a751-99eb313a0b36.png)

![image](https://user-images.githubusercontent.com/58657135/139525549-af1217c9-10da-4816-9e70-8fa0d762b427.png)

Lalu kita coba dengan request pada file yang mengandung kata `franky`:
![image](https://user-images.githubusercontent.com/58657135/139525572-2fff1b36-f6ea-4826-99e1-ed4d53a8b12f.png)

![image](https://user-images.githubusercontent.com/58657135/139525578-21be33d3-ea77-4864-8124-141ad3dce338.png)




