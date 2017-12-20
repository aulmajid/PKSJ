# Instalasi

1. Kelompok kami menggunakan OS ubuntu-16.04.3 untuk mengistall Cuckoo. Langkah pertama adalah download file cucko di halaman ``` https://downloads.cuckoosandbox.org/``` Pilih yg cuckoo-current.tar.gz

![](cuckoo/cucko.png)
<br>

2. Setelah selesai mendownload cuckoo-current, maka ekstrak hasil downloadan Anda dengan mengetikkan ```tar-xvzf cuckoo-current.tar.gz```

3. Install python dan library python lainnya dengan 
``` sudo apt-get install python python-pip python-dev libffi-dev libssl-dev ```
```sudo apt-get install python-virtualenv python-setuptools```
```sudo apt-get install libjpeg-dev zlib1g-dev swig```


![](cuckoo/1.png)
![](cuckoo/2.png)
![](cuckoo/3.png)

4. Untuk menggunakan Django-based Web Interface, install MongoDB ```sudo apt-get install mongodb```
![1](cuckoo/4.png)
<br>

5. Install tcpdump untuk membuang aktivitas jaringan yang dilakukan oleh malware selama eksekusi diperlukan sniffer jaringan yang dikonfigurasi dengan benar untuk menangkap lalu lintas 
```sudo apt-get install tcpdump apparmor-utils```
```sudo aa-disable /usr/sbin/tcpdump```

![1](cuckoo/5.png)
![1](cuckoo/6.png)
<br>

6. Clone volatility dari github lalu install
![1](cuckoo/7.png)
![1](cuckoo/8.png)
<br>

7. Setelah itu download distorm, lalu install
![1](cuckoo/9.png)
![1](cuckoo/10.png)
<br>

8. Setelah itu download Yara, lalu install.
![1](cuckoo/11.png)
<br>

9. Masuk folder cuckoo yang telah diekstrak tadi. Lalu masuk folder conf. Ubah file - file yang ada di dalamnya menggunakan 
```nano cuckoo.conf```
```nano auxiliary.conf```
```nano virtualbox.conf```
```nano processing.conf```
```nano memory.conf```
```nano reporting.conf```

![1](cuckoo/12%200.png)

![1](cuckoo/12.png)
![1](cuckoo/13.png)

![1](cuckoo/14%200.png)

![1](cuckoo/14.png)

![1](cuckoo/15%200.png)

![1](cuckoo/15.png)

![1](cuckoo/16%200.png)

![1](cuckoo/16.png)

![1](cuckoo/17%200.png)

![1](cuckoo/17.png)

![1](cuckoo/18%200.png)

![1](cuckoo/18.png)
<br>

10. Masuk folder web 

```cd .. ```

```cd web```
<br>

11. Jalankan perintah berikut ```./manage.py runserver```
![1](cuckoo/cuckoo%20runserver.png)
<br>

12. Buka halaman ```127.0.0.1:8000``` pada browser.
![1](cuckoo/19.png)
<br>

13. Buka Windows XP dari virtualbox.
<br>

14. Matikan firewall dari WindowsXP agar tak ada yang menghalangi pertukaran data antara host dan WindowsXP
![1](cuckoo/20.png)
<br>

15. Setelah itu, share folder agent di dalam folder cuckoo dengan klik kanan folder agent, lalu pilih Local Network Share
![1](cuckoo/21.png)
<br>

16. Buka virtual box, klik kanan Windows XP, pilih preference, pilih shared folders, pilih folder agent.
![1](cuckoo/22.png)
<br>

17. Salin file agent.py dari folder share diatas ke folder startup Widows XP
![1](cuckoo/23.png)
<br>

18. Coba restart Windows XP untuk melihat berjalan atau tidak
![1](cuckoo/24.png)
<br>

19. Sebelum menjalankan program cuckoo di host, masukkan perintah berikut di dalam folder cuckoo untuk mendapatkan utility lain yang diperlukan dalam cuckoo
```sudo ./utils/community.py -waf```
![1](cuckoo/25.png)
<br>

20. Jalankan cuckoo dengan perintah ```./cuckoo.py ```
![1](cuckoo/26.png)
<br>
