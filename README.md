# Jarkom-Modul-2-D06-2021

Anggota :
- Fitrah Mutiara 05111940000126
- Ahdan Amanullah Irfan Muzhaffar 05111940000197
- Dewi Mardani 05111940000225

## Soal 1
Luffy adalah seorang yang akan jadi Raja Bajak Laut. Demi membuat Luffy menjadi Raja Bajak Laut, Nami ingin membuat sebuah peta, bantu Nami untuk membuat peta berikut:

![image](https://user-images.githubusercontent.com/73428220/139525173-b7b972ed-c2cd-4f89-b9c4-d4ec2f723de0.png)

EniesLobby akan dijadikan sebagai DNS Master, Water7 akan dijadikan DNS Slave, dan Skypie akan digunakan sebagai Web Server. Terdapat 2 Client yaitu Loguetown, dan Alabasta. Semua node terhubung pada router Foosha, sehingga dapat mengakses internet.
### Jawaban Soal 1
1. Membuat topologi sesuai dengan gambar yang ada diatas dan berikut merupakan hasilnya
    ![image](https://user-images.githubusercontent.com/73428220/139525688-707cb8af-06f4-42f1-bc55-af3549e682ed.png)
2. Melakukan setting network pada masing-masing node
   - Pada Foosha sebagai router:
   ![image](https://user-images.githubusercontent.com/73428220/139525428-f8fd4b04-2bc4-47c8-93a9-ab61cb92fa67.png)
   - Pada Loguetown sebagai client:
   ![image](https://user-images.githubusercontent.com/73428220/139525480-ccae2ff7-7c3e-4432-b5db-65f7bda7e24e.png)
   - Pada Alabasta sebagai client:
   ![image](https://user-images.githubusercontent.com/73428220/139525530-09d62a34-4b2d-4f4f-9063-3f38334eaadf.png)
   - Pada EniesLobby sebagai DNS Master:
   ![image](https://user-images.githubusercontent.com/73428220/139525551-c9d361f2-d3f2-4416-8e23-212e35c1b022.png)
   - Pada Water7 sebagai DNS Slave:
   ![image](https://user-images.githubusercontent.com/73428220/139525610-c5e72938-e577-48ba-b60a-0c07f6015de6.png)
   - Pada Skypie sebagai Web Server:
   ![image](https://user-images.githubusercontent.com/73428220/139525638-e8d337b1-ed92-4083-9425-515741e07100.png)
3. Restart semua node
4. Cek semua node ubuntu apakah sudah memiliki ip yang sesuai dengan settingan dengan command ```ip a```
5. Kemudian agar dapat terkoneksi dengan internet jalankan ```iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.24.0.0/16``` pada router ```Foosha```. Dimana **iptables** merupakan suatu tools dalam sistem operasi Linux yang berfungsi sebagai filter terhadap lalu lintas data. Dengan iptables inilah kita akan mengatur semua lalu lintas dalam komputer, baik yang masuk, keluar, maupun yang sekadar melewati komputer kita, **NAT (Network Address Translation)** merupakan sebuah metode penafsiran alamat jaringan yang digunakan untuk menghubungkan lebih dari satu komputer ke jaringan internet dengan menggunakan satu alamat IP, **Masquerade** yang digunakan untuk menyamarkan paket, misal mengganti alamat pengirim dengan alamat router dan **s (Source Address)** merupakan Spesifikasi pada source.
## Soal 2
Luffy ingin menghubungi Franky yang berada di EniesLobby dengan denden mushi. Kalian diminta Luffy untuk membuat website utama dengan mengakses **franky.yyy.com** dengan alias **www.franky.yyy.com** pada folder kaizoku.
### Jawaban Soal 2
Pada EniesLobby lakukan konfigurasi terhadap file ```/etc/bind/named.conf.local```
  1. ```nano /etc/bind/named.conf.local```
  2. Buatlah folder etx/bind/kaizoku
  3. Isikan konfigurasi domain ```franky.D06.com```
  4. Edit script dengan IP Enies lobby 10.24.2.2
  BERIKUT INI MERUPAKAN SCRIPT dari keempat langkah diatas
      ![image](https://user-images.githubusercontent.com/73428220/139527280-09d61d9b-aab9-4e70-a33f-739001e1e1e6.png)
  5. Lakukan restart dengan ```service bind9 restart```
  6. Untuk mengecek domain masuk ke server LogueTown dan masukkan perintah berikut:
  
      ```ping franky.D06.com```
      berikut merupakan hasilnya :
      ![image](https://user-images.githubusercontent.com/73428220/139527579-9e0e1809-a5a9-4582-a450-b167f2884884.png)
     ```ping www.franky.D06.com```
     ![image](https://user-images.githubusercontent.com/73428220/139527653-8e301503-8170-401c-87f7-8d1c8fffe9b9.png)
     ```host -t CNAME www.franky.D06.com```
     ![image](https://user-images.githubusercontent.com/73428220/139527684-64cf9d23-97a1-415b-a6d7-4fdce0ea0720.png)

## Soal 3
Setelah itu buat subdomain super.franky.yyy.com dengan alias www.super.franky.yyy.com yang diatur DNS nya di EniesLobby dan mengarah ke Skypie
### Jawaban Soal 3
1. Edit script menjadi seperti gambar dibawah untuk mengarahkan subdomain super.franky.yyy.com ke Skypie
![image](https://user-images.githubusercontent.com/73428220/139528990-209efc7e-feb6-4095-a611-e41199d46ab2.png)
2. Untuk mengeceknya restart bind9 pada Enieslobby kemudian masuk ke LogueTown dan mjalankan perintah berikut :
 ```ping super.franky.D06.com```
 ![image](https://user-images.githubusercontent.com/73428220/139529041-3d6c67bd-7c8d-4656-ae3f-62bce16c8981.png)
```ping www.super.franky.D06.com```
![image](https://user-images.githubusercontent.com/73428220/139529067-53bf1c67-bdfe-4710-81b5-319613c35632.png)
```host -t A super.franky.D06.com```
![image](https://user-images.githubusercontent.com/73428220/139529107-7385cd16-bc7e-49e3-a8f6-c8673deaf242.png)
```host -t CNAME www.super.franky.D06.com```
![image](https://user-images.githubusercontent.com/73428220/139529137-465367e0-7eb2-4d35-bae7-d3a4b037a79e.png)

## Soal 4
Buat juga reverse domain untuk domain utama
### Jawaban Soal 4
1. nano ```/etc/bind/named.conf.local```
2. Tambahkan konfigurasi ke dalam file named.conf.local. 
3. Tambahkan reverse dari 3 byte awal sehingga menjadi 2.24.10.
4. Sehingga akan menghasilkan script seperti gambar yang ada dibawah ini
![image](https://user-images.githubusercontent.com/73428220/139529292-c6906c29-a184-4d6c-a6f0-51cdb3bf6339.png)
 
## Soal 5
Supaya tetap bisa menghubungi Franky jika server EniesLobby rusak, maka buat Water7 sebagai DNS Slave untuk domain utama
1. Edit file /etc/bind/named.conf.local pada EniesLobby sebagai berikut
![image](https://user-images.githubusercontent.com/73428220/139529804-32dcf6ed-8799-46bd-a64e-0141508b03cf.png)
2. Lakukan restart bind9
3. Buka Water7 dan update package lists dengan menjalankan command ```apt-get update```
4. install aplikasi bind9 pada Water7 dengan perintah ```apt-get install bind9 -y```
5. Edit file /etc/bind/named.conf.local pada Water7 dan tambahkan syntax berikut
![image](https://user-images.githubusercontent.com/73428220/139529900-18b4f266-34a2-4ae2-a0d7-d25dbc3d6877.png)
6. Untuk melakukan testing, kembali ke EniesLobby dan lakukan stop pada serivice bind9
7. Pada LogueTown jalankan perintah sebagai berikut :
![image](https://user-images.githubusercontent.com/73428220/139529994-b0d379c1-bc2f-432b-b983-aaeec84e587a.png)

## Soal 6
Setelah itu terdapat subdomain mecha.franky.yyy.com dengan alias www.mecha.franky.yyy.com yang didelegasikan dari EniesLobby ke Water7 dengan IP menuju ke Skypie dalam folder sunnygo
1. Pada server EniesLobby lakukan konfigurasi pada file 
![image](https://user-images.githubusercontent.com/73428220/139530133-cd82a175-e745-4638-9411-f9aac5a8c5ec.png)
2. Restart service bind9
3. Pada server water7 edit tambahkan script berikut ini agar subdomain dapat menuju ke skypie dalam folder sunnygo
![image](https://user-images.githubusercontent.com/73428220/139530256-c254a62e-6167-480d-b199-f27444e8f908.png)

![image](https://user-images.githubusercontent.com/73428220/139530359-dac5d1e6-76b1-44a6-bd36-81ff99b3576e.png)

![image](https://user-images.githubusercontent.com/73428220/139530380-59952dba-1515-4c4b-8cec-aa0a6d8910c0.png)

4.Restart service bind9

5. Untuk melakukan testing jalankan perintah ```ping mecha.franky.D06.com```
![image](https://user-images.githubusercontent.com/73428220/139530502-fe181729-d9f0-459b-8390-45ba250d2c37.png)
6. Untuk melakukan testing jalankan perintah ```ping www.mecha.franky.D06.com```
![image](https://user-images.githubusercontent.com/73428220/139530531-a45cc5e7-d180-448c-aeff-a1499a11ab4d.png)


## Soal 7
Untuk memperlancar komunikasi Luffy dan rekannya, dibuatkan subdomain melalui Water7 dengan nama general.mecha.franky.yyy.com dengan alias www.general.mecha.franky.yyy.com yang mengarah ke Skypie.

1. Pada server Water7 tambahkan script berikut untuk membuat subdomain dengan nama general.mecha.franky.D06.com dengan alias www.general.mecha.franky.D06.com yang mengarah ke Skypie
![image](https://user-images.githubusercontent.com/73428220/139530417-182a744b-3033-494c-98c2-a0742aa5ae3e.png)
2. Untuk melakukan testing jalankan perintah sebagai berikut 
![image](https://user-images.githubusercontent.com/73428220/139530698-262eb42f-4671-4f6b-9ac5-263c2a12c7ff.png)
![image](https://user-images.githubusercontent.com/73428220/139530707-8fa75012-ad2e-4627-a341-742730c63db6.png)

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
