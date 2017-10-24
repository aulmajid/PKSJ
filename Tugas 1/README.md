# Tugas 1

## Pendahuluan
blala

## Dasar Teori

#### Oracle VM VirtualBox
blabla

#### Ubuntu Server
blabla

#### Xubuntu
Xubuntu adalah varian dari Ubuntu yang menggunakan desktop environment Xfce. Xubuntu dipilih karena lebih ringan dan ukurannya lebih kecil dari Ubuntu, sehingga spesifikasi hardware yang dibutuhkan lebih rendah dari Ubuntu. Xubuntu dapat diunduh dari halaman resminya yaitu https://xubuntu.org .

#### 500-worst-passwords.txt
File txt perisi 500 buah password yang digunakan dalam uji coba ini. File ini dapat diunduh di https://wiki.skullsecurity.org/images/c/ca/500-worst-passwords.txt .

#### THC-Hydra
blabla

#### Ncrack
blabla

#### fail2ban
blabla

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

#### Uji penetrasi menggunakan Ncrack
Pada OS yang digunakan untuk penetrasi, lakukan langkah berikut :
1. Buka terminal.
1. Ketikkan perintah `ncrack -p 22 --user [user] -P [passlist.txt] [remote_ip]`, contoh: `ncrack -p 22 --user pksj -P 500-worst-passwords.txt 10.0.2.4`

## Uji Penetrasi 2

