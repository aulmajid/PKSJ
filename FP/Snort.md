# Instalasi Snort


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
- Update library
```
ldconfig
ln -s /usr/local/bin/snort /usr/sbin/snort
snort -V
```

### Instalasi Snort
mkdir /etc/snort 
mkdir /etc/snort/preproc_rules 
mkdir /etc/snort/rules 
mkdir /var/log/snort 
mkdir /usr/local/lib/snort_dynamicrules 
touch /etc/snort/rules/white_list.rules 
touch /etc/snort/rules/black_list.rules 
touch /etc/snort/rules/local.rules

chmod -R 5775 /etc/snort/ 
chmod -R 5775 /var/log/snort/ 
chmod -R 5775 /usr/local/lib/snort
chmod -R 5775 /usr/local/lib/snort_dynamicrules/