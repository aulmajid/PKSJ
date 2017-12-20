#### LESSON 5

1. Membuka halaman mutillidae dengan memasukkan url `IPmetasploit/mutillidae` seperti gambar berikut : 
![](Mutillidae%20lesson%205/mutilidae%201.png)

2. Pilih login : 
![](Mutillidae%20lesson%205/mutilidae%202.png)

3. Isi tanda petik satu ` ' ` di form login kolom nama : 
![](Mutillidae%20lesson%205/mutilidae%203.png)

4. Akan muncul tampilan error seperti berikut :  
![](Mutillidae%20lesson%205/mutilidae%204.png)

5. terlihat dari error tersebut dapat diartikan program backend rentan terhadap SQL injection

6. ketik `' or 1=1-- ` di form login kolom nama (jangan lupa memberikan spasi setelah tanda `--`) 
![](Mutillidae%20lesson%205/mutilidae%205.png)

5. Hasilnya akan muncul seperti gambar berikut (login sebagai admin): 
![](Mutillidae%20lesson%205/mutilidae%206.png)

6. Setelah itu logout dan ketik `samurai` pada kolom nama kemudian masuk ke inspect element pada kolom password dan rubah tipe dari password menjadi bentuk teks: 
![](Mutillidae%20lesson%205/mutilidae%207.png)
![](Mutillidae%20lesson%205/mutilidae%208.png)
![](Mutillidae%20lesson%205/mutilidae%209.png)

7. Isi tanda petik satu ` ' ` pada kolom password kemudian login : gambar 10
![](Mutillidae%20lesson%205/mutilidae%2010.png)

8. Masuk ke inspect element dan rubah kolom password seperti gambar berikut : gambar 12
![](Mutillidae%20lesson%205/mutilidae%2012.png)

9. Kemudian isi form login dengan nama = `samurai` dan password `' or (1=1 and username='samurai')-- ` (jangan lupa memberikan spasi setelah tanda `--`)

10. Hasilnya akan muncul seperti gambar berikut (login sebagai samurai) : gambar 14
![](Mutillidae%20lesson%205/mutilidae%2014.png)

11. kemudian masuk ke mysql pada metasploit, dan jalankan sesuai gambar berikut : gabmar 15 16 17 18
![](Mutillidae%20lesson%205/mutilidae%2015.png)
![](Mutillidae%20lesson%205/mutilidae%2016.png)
![](Mutillidae%20lesson%205/mutilidae%2017.png)
![](Mutillidae%20lesson%205/mutilidae%2018.png)

12. jalankan perintah perintah pada metasploit seperti pada gambar : gambar 19 20 21 22 23 24 25
![](Mutillidae%20lesson%205/mutilidae%2019.png)
![](Mutillidae%20lesson%205/mutilidae%2020.png)
![](Mutillidae%20lesson%205/mutilidae%2021.png)
![](Mutillidae%20lesson%205/mutilidae%2022.png)
![](Mutillidae%20lesson%205/mutilidae%2023.png)
![](Mutillidae%20lesson%205/mutilidae%2024.png)
![](Mutillidae%20lesson%205/mutilidae%2025.png)
