---
title: "Manajemen User & Group Linux"
layout: post
date: 2021-12-31 10:20
headerImage: true
hidden: false
tag:
- administration
- management
- linux
star: false
category: blog
author: wicaksonoindra
description: Markdown summary with different options
---

![terminal](/assets/images/blog/2-manajemen-user-dan-group/etc-passwd.png)

Sistem operasi Linux tidak pernah lepas dari manajemen proses maupun kepemilikan dan hak akses file dimana ketiga fungsi tersebut memerlukan sebuah account user dan group. Seperti yang kita ketahui, dalam sistem operasi LInux pada umumnya, hak akses user dibagi ke dalam dua jenis yaitu user biasa ditandai dengan prompt $ dan super user (root) ditandai dengan prompt #.
Pembagian hak akses ini tentunya dilakukan untuk keamanan sistem itu sendiri, artinya hanya super user (root) yang punya kendali untuk melakukan konfigurasi terhadap sistem sedangkan user biasa hanya sebatas bisa melihat file yang berada pada direktori /home.

## Membuat User($)
Untuk membuat user baru kita dapat menggunakan command “useradd” dan “adduser”. Sebelum membuat user kita harus masuk ke super user dulu dengan command `su -`.
1. Menggunakan useradd<br>
Untuk membuat user baru dengan useradd kita dapat menuliskan command “useradd [namauser]”, secara default user akan terbuat tanpa home directory dan shellnya menggunakan /bin/sh. Untuk membuat user yang memiliki home directory dan menggunakan shell bash kita dapat menggunakan command sebagai berikut:
```powershell
useradd -m -s /bin/bash [namauser]
```
User baru akan terbuat dan mendapatkan home directory karena flag -m dan shell yang user baru gunakan adalah bash karena flag -s /bin/shell. Selain -m dan -s, banyak lagi opsi lain untuk memberikan custom pada user yang kita buat. Misalnya -u untuk memberikan nomor UID tertentu, -e untuk menentukan limit waktu user, -c untuk memberikan komentar dan lainnya. Opsi ini dapat kita lihat di Manual useradd atau “man useradd”.
Selanjutnya kita akan memerlukan password untuk login ke akun tersebut. Berikut adalah cara memasang password pada user baru tersebut:
```powershell
passwd [namauser]
```
Lalu inputkan password yang di inginkan.

2. Menggunakan adduser<br>
Dengan membuat user baru dengan command adduser, home user akan automatis terbuat dan shell yang digunakan adalah bash. Selain itu, password akan langsung automatis dibuat serta beberapa user information lainnya seperti Fullname, room number, work phone, dan lain-lain. Command ini terasa lebih mudah dibanding useradd.
Berikut cara membuat user dengan command adduser:
```powershell
adduser [namauser]
```
lalu, kita akan diminta untuk memasukkan password untuk user baru tersebut dan diminta untuk mengisi beberapa indormasi tambahan.

## Membuat Group
Group digunakan untuk mengelompokkan beberapa user. Contoh jika kita memiliki 5 user pada suatu sistem operasi dan kita ingin memberikan akses tertentu untuk 3 user tersebut. Tanpa Group ini, kita harus konfigurasi 3 kali. Namun jika kita menggunakan group, kita hanya perlu memberikan akses ke group saja. Maka automatis user yang termasuk didalam group tersebut diberikan akses juga.
Sebelum membuat group, kita dapat melihat group apa saja yang telah terbuat pada sistem operasi dengan command “cat /etc/group”. Secara default saat kita membuat user baru, group baru juga akan terbuat sesuai dengan nama user baru tersebut.
Berikut cara membuat group baru:
```powershell
groupadd [namagroup]
```
Pastikan sebelum membuat group, kita harus menggunakan super user(root) terlebih dahulu.

## Menambahkan User ke Group
Sebelum menambahkan user tertentu ke suatu group, kita dapat melihat suatu user sudah bergabung kegroup mana saja dengan command “id [username]”.
Command yang digunakan untuk menambahkan user ke group adalah “usermod”. Kita dapat melihat beberapa opsi yang dapat digunakan pada usermod dengan command “man usermod”. Flag yang digunakan untuk memasukkan suatu user ke suatu group adalah -G.
Berikut command untuk memasukkan suatu user ke suatu group:
```powershell
usermod -G [namagroup] [namauser]
```
Cek kembali apakah user tersebut telah termasuk ke dalam group yang kita inginkan dengan command “id [namauser]”.
Lalu jika kita ingin menambahkan user yang telah termasuk ke suatu group ke group lain juga. Misalnya user1 telah tergabung di group1 dan kita ingin user1 tergabung ke group2 juga, maka kita tidak dapat menambahkan user1 dengan command dengan option yang sama. Jika kita menggunakan command yang sama, maka group1 akan di replace/timpa menjadi group2.
Jadi, kita memerlukan option tambahan untuk menambahkan user1 ke group2 dengan option -a atau append. Sehingga command yang dapat digunakan adalah:
```powershell
usermod -aG [namagroup] [namauser]
```

## Menghapus User dan Group
- Menghapus User<br>
Untuk menghapus suatu user kita dapat menggunakan command “userdel” seperti berikut:
```powershell
userdel -r [namauser]
```
Option -r digunakan agar home directory suatu user juga ikut terhapus.

- Menghapus Group<br>
Untuk menghapus suatu group kita dapat menggunakan command “groupdel” seperti berikut:
```powershell
groupdel [namagroup]
```
