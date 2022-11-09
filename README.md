# Jarkom-Modul-3-ITB06-2022

Repository ini dibuat sebagai laporan resmi untuk pengerjaan [Soal Shift Modul 3](https://docs.google.com/document/d/1asm7lgnTJxr17DxsE_McdUimPsRjesi6ZrHRpmXPZ4s/edit) dari praktikum Mata Kuliah Komunikasi Data dan Jaringan Komputer.


**Anggota Kelompok ITB06**
- Sarah Hanifah Pontoh	5027201006
- Sharira Saniane 	5027201016
- Naufal Dhiya Ulhaq 	5027201029


## Table of Contents

## Soal 1 & 2
Loid bersama Franky berencana membuat peta tersebut dengan kriteria WISE sebagai DNS Server, Westalis sebagai DHCP Server, Berlint sebagai Proxy Server (1), dan Ostania sebagai DHCP Relay (2). Loid dan Franky menyusun peta tersebut dengan hati-hati dan teliti.

**Langkah-langkah Pengerjaan No 1:  **
1. Pertama-tama buat topologi seperti yang diminta pada soal.
![Image 1.1](Photos/1.1.png)

2. Lakukan konfigurasi seperti berikut :

_Konfigurasi untuk ostania_

```
auto eth0
 iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.217.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.217.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.217.3.1
	netmask 255.255.255.0
```

_Konfigurasi untuk WISE_
```
auto eth0 
iface eth0 inet static 
      address 192.217.2.2
      netmask 255.255.255.0
      gateway 192.217.2.1
```

_Konfigurasi untuk berlint (proxy server)_
```
auto eth0 
iface eth0 inet static 
      address 192.217.2.3
      netmask 255.255.255.0
      gateway 192.217.2.1
```

_Konfigurasi untuk Westalis_ 
```
auto eth0 
iface eth0 inet static 
      address 192.217.2.4
      netmask 255.255.255.0
      gateway 192.217.2.1
```

_Konfigurasi untuk Eden_
```
auto eth0
iface eth0 inet dhcp
hwaddress ether 52:f1:e5:9d:68:fb
```

_Konfigurasi node yang lain_
```
auto eth0
iface eth0 inet dhcp
```
3. Pada WISE sebagai DNS Server, lakukan beberapa perintah berikut:
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
```
![Image 1.1](Photos/1.1.png)

4. Pada Berlint sebagai Proxy Server, lakukan beberapa perintah berikut:
```
echo "nameserver 192.168.122.1" > /etc/resolv.conf
apt-get update
apt-get install libapache2-mod-php7.0 -y
apt-get install squid -y
```
5. Pada Ostania sebagai DHCP Relay, lakukan bebrapa perintah berikut:
```
apt-get update
apt-get install isc-dhcp-relay -y
```


