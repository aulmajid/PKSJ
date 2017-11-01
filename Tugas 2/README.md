# Tugas 2
**Anggota Kelompok**

| NRP         | Nama                        |
|-------------|-----------------------------|
| 5114100018  | Alek Nur Fatman             |
| 5114100077  | M Hanif Amrizal             |
| 5114100144  | Ilham Aulia Majid           |

## Pendahuluan
blabla


## Dasar Teori

#### OS
blabla

#### Wordpress
blbla

#### Spider Video Player
blabla

#### League Manager
blabla

#### WPScan
blabla

#### sqlmap
blabla


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
blabla

## Kesimpulan dan Saran
1. blabla
