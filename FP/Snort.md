# Snort


### Instalasi Snort

- Download daq dan snort
```
wget https://www.snort.org/downloads/snort/daq-2.0.6.tar.gz
wget https://www.snort.org/downloads/snort/snort-2.9.11.tar.gz
```
- Install daq
```
tar xvfz daq-2.0.6.tar.gz
cd daq-2.0.6
./configure && make && sudo make install
```
- Install snort
```
cd ..
tar xvfz snort-2.9.11.tar.gz
cd snort-2.9.11
./configure --enable-sourcefire && make && sudo make install
```
- Keterangan : jika terdapat error membutuhkan paket lain yang belum terinstall, langsung install saja seperti biasa
```
apt-get install [nama_paket_yang_dibutuhkan]
```
- Update library
```
ldconfig
ln -s /usr/local/bin/snort /usr/sbin/snort
snort -V
```
1

### Konfigurasi Snort
- Buat struktur folder dan file rules
mkdir /etc/snort 
mkdir /etc/snort/preproc_rules 
mkdir /etc/snort/rules 
mkdir /var/log/snort 
mkdir /usr/local/lib/snort_dynamicrules 
touch /etc/snort/rules/white_list.rules 
touch /etc/snort/rules/black_list.rules 
touch /etc/snort/rules/local.rules
- Atur perijinan
chmod -R 5775 /etc/snort/ 
chmod -R 5775 /var/log/snort/ 
chmod -R 5775 /usr/local/lib/snort
chmod -R 5775 /usr/local/lib/snort_dynamicrules/
2
- Salin file konfigurasi
```
cd etc/
cp -avr *.conf *.map *.dtd /etc/snort/
cd ..
cp -avr src/dynamic-preprocessors/build/usr/local/lib/snort_dynamicpreprocessor/* /usr/local/lib/snort_dynamicpreprocessor/
```
3
4
- Edit file konfigurasi
```
sed -i "s/include \$RULE\_PATH/#include \$RULE\_PATH/" /etc/snort/snort.conf
nano /etc/snort/snort.conf
```
- Isi sesuai konfigurasi di bawah
```
ipvar HOME_NET 192.168.15.0/24
ipvar EXTERNAL_NET any 
var RULE_PATH /etc/snort/rules 
var SO_RULE_PATH /etc/snort/so_rules 
var PREPROC_RULE_PATH /etc/snort/preproc_rules 
var WHITE_LIST_PATH /etc/snort/rules 
var BLACK_LIST_PATH /etc/snort/rules 
include $RULE_PATH/local.rules
```
6
7
- Lalu jalankan konfigurasi tadi dengan perintah berikut
```
snort -T -i eth0 -c /etc/snort/snort.conf
snort -T -i enp0s3 -c /etc/snort/snort.conf
```
- Hasilnya error
8