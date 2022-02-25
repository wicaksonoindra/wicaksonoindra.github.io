---
title: "Write up: Firebase Database Exposed by Misconfiguration"
layout: post
date: 2022-02-24 09:04
headerImage: true
hidden: false
tag:
- bughunting
- writeup
- firebase
star: false
category: blog
author: wicaksonoindra
description: bug hunting on travellgo app
---

### Intro
Akhir-akhir ini, saya tertarik untuk mempelajari App Mobile Pentest. App Mobile Pentest merupakan suatu kegiatan mensimulasikan serangan yang bisa dilakukan pada suatu aplikasi tertentu untuk menemukan kelemahan pada aplikasi tersebut. Setelah mempelajari sedikit metode melakukan Mobile App Pentest, saya mulai mencari aplikasi random di play store untuk proses belajar.
Saya mencoba mencari celah pada suatu aplikasi driver online lokal pada kota tempat inggal saya, dan saya menemukan Database firebase yang ter ekspose.

### Proof of concept:
1. Download Apk file target menggunakan ekstensi tambahan dari browser, dengan memasukkan link play store aplikasi target.
![download](/assets/images/blog/4-2022-02-24-writeup-firebase-database-exposed-by-misconfiguration/download-apk.png)

2. Scanning file apk dengan menggunakan 'apkleaks'.
```powershell
┌──(ndraw㉿ndraw)-[~]
└─$ apkleaks -f /mnt/d/app/target.apk
```
![scanning](/assets/images/blog/4-2022-02-24-writeup-firebase-database-exposed-by-misconfiguration/scanning.png)

3. Saya mendapatkan end-point firebase aplikasi tersebut. Untuk melihat apakah ada kesalahan konfigurasi pada pada firebase, cukup tambahkan (.json) ke url firebase.
![vuln](/assets/images/blog/4-2022-02-24-writeup-firebase-database-exposed-by-misconfiguration/firebase-endpoint.png)

4. Firebase database terekspose karena kesalahan konfigurasi
![data](/assets/images/blog/4-2022-02-24-writeup-firebase-database-exposed-by-misconfiguration/data-exposed.png)

### Impact
Sejak firebase database salah di konfirgurasi, semua orang dapat melihat data basenya.
