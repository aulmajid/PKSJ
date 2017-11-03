# Tugas 2
**Anggota Kelompok**

| NRP         | Nama                        |
|-------------|-----------------------------|
| 5114100018  | Alek Nur Fatman             |
| 5114100077  | M Hanif Amrizal             |
| 5114100144  | Ilham Aulia Majid           |

## Pendahuluan
Sql Injection : SQL injection adalah sebuah teknik hacking yang menyalahgunakan celah keamanan pada database dari aplikasi. cara kerjanya adalah dengan menyisipkan perintah-perintah SQL melalu URL untuk di eksekusi oleh database.


## Dasar Teori

#### OS Ubuntu 16.04
Ubuntu 16.04 adalah sistem operasi distribusi linux yang berbasis debian dan bersifat Open Source.

#### Wordpress
Wordpress adalah aplikasi open source yang digunakan sebagai blog engine. Wordpress menggunakan bahasa pemrograman PHP dan basis data MySQL. Wordpress juga digunakan sebagai CMS (Content Management System) karena memiliki kemampuan untuk dimodifikasi dan disesuaikan dengan kebutuhan penggunanya.

#### Spider Video Player
Spider Video Player adalah salah satu plugin Wordpress yang menyediakan fitur untuk memasukkan video ke website Wordpress. 

#### League Manager
League Manager adalah plugin yang digunakan untuk menampilkan hasil dari sebuah pertandingan pada website wordpress.

#### WPScan
WPScan adalah tools vulnerability scanner untuk CMS Wordpress yang memeriksa keamanan WordPress menggunakan metode “black box”. WPScan ini ditulis dengan bahasa ruby.

#### sqlmap
Sqlmap adalah tools opensource yang mendeteksi dan melakukan exploit pada bug SQL injection secara otomatis. dengan melakukan serangan SQL injection seorang attacker dapat mengambil alih serta memanipulasi sebuah database di dalam sebuah server.


## Instalasi Wordpress, Vulnerable Plugins, dan Tools untuk Penetrasi

#### Instalasi LAMP
1. Buka terminal.
2. Masukkan perintah :
```
sudo apt-get install apache2 mysql-server php7.0 php7.0-mysql libapache2-mod-php7.0 php7.0-cli php7.0-cgi php7.0-gd
sudo systemctl enable apache2
sudo systemctl start apache2
```

#### Instalasi Wordpress
1. Unduh wordpress tarball di http://wordpress.org/latest.tar.gz
2. Ekstrak ke direktori /var/www/html dengan perintah `tar -xvzf wordpress-4.8.3.tar.gz -C /var/www/html `.
3. Buka `http://localhost/wordpress/wp-admin/install.php` dan ikuti prosedur yang ada.

#### Instalasi Plugin Video Player
1. Unduh plugin di https://wordpress.org/plugins/player/
2. Ekstrak plugin ke /var/www/html/wordpress/wp-content/plugins dengan perintah `unzip player.1.5.20.zip -d /var/www/html/wordpress/wp-content/plugins`.

#### Instalasi Plugin League Manager
1. Unduh plugin di https://wordpress.org/plugins/leaguemanager/
2. Ekstrak plugin ke /var/www/html/wordpress/wp-content/plugins dengan perintah `unzip leaguemanager.4.2-RC1.3.zip -d /var/www/html/wordpress/wp-content/plugins`.

#### Aktivasi Plugin
1. Buka halaman `http://localhost/wordpress/wp-admin/plugins.php`.
2. Centang LeagueManager dan Spider Video Player.
3. Pilih aksi `Activate` lalu klik `Apply`.

#### Instalasi WPScan
1. Instal prerequisites dengan perintah `sudo apt-get install git libcurl4-openssl-dev libxml2 libxml2-dev libxslt1-dev ruby-dev build-essential libgmp-dev zlib1g-dev`.
2. Clone repository WPScan `git clone https://github.com/wpscanteam/wpscan.git`.
3. Pindah ke direktori WPScan `cd wpscan`.
4. Masukkan perintah `sudo gem install bundler && bundle install --without test development`.
5. Untuk menjalankan WPScan gunakan ruby `ruby wpscan.rb [options]`.

#### Instalasi sqlmap
1. Clone repository sqlmap `https://github.com/sqlmapproject/sqlmap.git`.
2. Pindah ke direktori WPScan `cd sqlmap`.
5. Untuk menjalankan WPScan gunakan python `python sqlmap.py [options]`.

## Uji Penetrasi SQL Injection

#### Uji WPScan
1. Update terlebih dahulu database WPScan dengan perintah `ruby wpscan.rb --update`.
2. Jalankan perintah `wpscan -u [alamat_wordpress] --enumerate vp`, contoh: `ruby wpscan.rb --u http://localhost/wordpress --enumerate vp`.
3. Output :
![WPScan](Hasil%20WPScan/WPScan%201.png)
![WPScan](Hasil%20WPScan/WPScan%202.png)
![WPScan](Hasil%20WPScan/WPScan%203.png)


#### Uji sqlmap
1. Jalankan perintah 

## Kesimpulan dan Saran
1. blabla
