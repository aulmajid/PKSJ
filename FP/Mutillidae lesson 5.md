#### LESSON 5

1. Membuka halaman mutillidae dengan memasukkan url `IPmetasploit/mutillidae` seperti gambar berikut : 
![](Mutillidae%20lesson%205/mutilidae%201.png)

2. Pilih login : gambar 2

3. Isi tanda petik satu ` ' ` di form login kolom nama : gambar 3

4. Akan muncul tampilan error seperti berikut : gambar 4 

5. terlihat dari error tersebut dapat diartikan program backend rentan terhadap SQL injection

6. ketik `' or 1=1-- ` di form login kolom nama (jangan lupa memberikan spasi setelah tanda `--`) gambar 5

5. Hasilnya akan muncul seperti gambar berikut (login sebagai admin): gambar 6

6. Setelah itu logout dan ketik `samurai` pada kolom nama kemudian masuk ke inspect element pada kolom password dan rubah tipe dari password menjadi bentuk teks: gambar 7 8 9

7. Isi tanda petik satu ` ' ` pada kolom password kemudian login : gambar 10

8. Masuk ke inspect element dan rubah kolom password seperti gambar berikut : gambar 12

9. Kemudian isi form login dengan nama = `samurai` dan password `' or (1=1 and username='samurai')-- ` (jangan lupa memberikan spasi setelah tanda `--`)

10. Hasilnya akan muncul seperti gambar berikut (login sebagai samurai) : gambar 14

11. kemudian masuk ke mysql pada metasploit, dan jalankan sesuai gambar berikut : gabmar 15 16 17 18

12. jalankan perintah perintah pada metasploit seperti pada gambar : gambar 19 20 21 22 23 24 25
