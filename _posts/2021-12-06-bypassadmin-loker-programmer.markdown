---
title: "Bypass Admin pada subdomain Loker Progammer"
layout: post
date: 2021-12-06 16:36
headerImage: true
hidden: false
tag:
- bughunting
- writeup
- bypassadmin
star: false
category: blog
author: wicaksonoindra
description: hunting bug on loker programmer website
---

### Intro
Bypass Admin merupakan teknik hacking yang dilakukan dengan cara menginputkan perintah sql dimana system akan mengeksekusi menjadi query dari user:pass administrator untuk masuk ke halaman admin panel. Jadi tanpa mengetahui username dan passwordnya kita tetap akan bisa login menggunakan teknik tersebut.

![website](/assets/images/blog/1-bypassadmin-lokerprogrammer/bypassadmin-lokerprogrammer-1.png)

Saya tidak sengaja menemukan url web Loker Programmer yang dibagikan di story whatsapp oleh teman saya yang sedang internship di Loker Progammer. Lalu saya iseng untuk mengunjungi web tersebut untuk melihat program apa yang sedang di jalankan oleh teman saya tersebut.

### Proses Exploitasi
> Url: https://event.lokerprogrammer.com/

Pada url tersebut berisi login dan sign-up form, saya jadi iseng untuk mencoba untuk bypass login form tersebut dengan berbagai payload. Awalnya saya coba iseng memasukkan email `'=''or'` dan password `admin` namun tidak berhasil, saya lupa jika form tersebut merupakan email, bukan username hehe. Jadi saya mengubahnya menjadi seperti berikut:
> Email: '=''or'@gmail.com <br>
Password: admin

![payload](/assets/images/blog/1-bypassadmin-lokerprogrammer/bypassadmin-lokerprogrammer-2.png)

dan saya berhasil masuk sebagai admin pada website tersebut.

![admin](/assets/images/blog/1-bypassadmin-lokerprogrammer/bypassadmin-lokerprogrammer-3.png)

### Impact
- Attacker dapat membuat/menghapus event pada website loker Programmer
- Attacker dapat melihat bukti transfer pelanggan loker Progammer

### Timeline:
- [20:36, 12/3/2021] Reported.
- [20:52, 12/3/2021] Loker Programmer confirm the report.
- [21:14, 12/3/2021] Bug Fixed.
