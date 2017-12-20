#### LESSON 6

1. Membuka halaman mutillidae dengan memasukkan url `IPmetasploit/mutillidae` seperti gambar berikut : gambar 1
![](Mutillidae%20lesson%206/mutillidae%201.png)

2. Setting networks pada mozilla di kali linuk seperti pada gambar : 
![](Mutillidae%20lesson%206/mutillidae%202.png)

3. Kemudian buka burpsuite, setelah itu cek proxy dan klik `intercept is on` seperti pada gambar : 
![](Mutillidae%20lesson%206/mutillidae%203.png)

![](Mutillidae%20lesson%206/mutillidae%204.png)

4. Login mutilidae dengan name `' or 1=1-- ` (jangan lupa memberikan spasi setelah tanda `--`) 
![](Mutillidae%20lesson%206/mutillidae%205.png)

![](Mutillidae%20lesson%206/mutillidae%206.png)

5. Buka aplikasi burpsuite pilih tab proxy, lalu http history, cari host `IPmetasploit` dan method `post` : 
![](Mutillidae%20lesson%206/mutillidae%207.png)

6. Kemudian Buka terminal dan ketik commend `curl -b crack_cookies.txt -c crack_cookies.txt -A "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "username=%27+or+1%3D1--+&password=&login-php-submit-button=Login" -L "http://10.0.1.100/mutillidae/index.php?page=login.php" > loginlesson5.txt` juga ketik perintah `grep "Logged In" loginlesson5.txt` dan `cat crack_cookies.txt` seperti pada gambar : 
![](Mutillidae%20lesson%206/mutillidae%208.png)

7. Lalu lakukan hal yang sama dari langkah 4. login dengan nama `samurai` password `' or (1=1 and username='samurai')-- `  (jangan lupa memberikan spasi setelah tanda `--`) seperti pada gambar dibawah :
![](Mutillidae%20lesson%206/mutillidae%209.png)

![](Mutillidae%20lesson%206/mutillidae%2010.png)

8. Buka http history pada burpsuite dan blok semua isi dari request tab -> raw tab kemudian `save to file`  dan berikan nama `loginlesson.txt` 
![](Mutillidae%20lesson%206/mutillidae%2011.png)

9. Lalukan seperti langkah  dengan merubah command seperti gambar berikut berikut. : gambar 12
![](Mutillidae%20lesson%206/mutillidae%2012.png)

10. Setelah itu matikan proxy. 
![](Mutillidae%20lesson%206/mutillidae%2013.png)

12. Buka cookies manager+ dan add cookies isikan sesuai dengan hasil yang ada pada perintah `cat crack_cookies.txt`(jika belum punya cookies manager+, install addons cookies manager+ terlebuh dahulu). 
![](Mutillidae%20lesson%206/mutillidae%2014.png)

![](Mutillidae%20lesson%206/mutillidae%2015.png)

![](Mutillidae%20lesson%206/mutillidae%2016.png)

13. Setelah itu buka mutillidae pada browser dan hasilnya akan secara otomatis login sebagai samurai tanpa mengisi form login terleih dahulu 
![](Mutillidae%20lesson%206/mutillidae%2017.png)
