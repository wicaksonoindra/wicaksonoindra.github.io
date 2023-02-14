---
title: "Membuat Bad USB dengan Digispark Attiny85"
layout: post
date: 2023-2-14 19:00
headerImage: true
hidden: true
tag:
- hacking
- badusb
- digispark
star: false
category: blog
author: wicaksonoindra
description: Langkah-langkah membuat badusb dengan Digispark Attiny85
---

<!---![terminal](/assets/images/blog/5-membuat-badusb/01-digispark.jpg) --->
<img src="/assets/images/blog/5-membuat-badusb/01-digispark.jpg" alt="Digispark Attiny85" width=70%> <br>

### Apa itu bad usb?

Bad Usb merupakan sebuah perangkat keras yang berbentuk usb biasa namun sebetulnya ia akan bertindak sebagai keyboard maupun mouse yang dapat menjalankan script yang telah diprogram. Biasanya badusb akan diprogram untuk menjalankan shortcut untuk membuka terminal dan menjalankan script yang berbahaya seperti mencuri password wifi, menjalankan reverse shell, menjalankan script exploit, dan lain-lain.

Karena badusb ini terprogram(scripted), program yang eksekusi oleh badusb ini dapat dilakukan dalam beberapa detik saja. Kita juga dapat mengatur waktu delay setiap script yang dijalankan juga pada saat proses menanamkan programnya. Untuk membuat badusb, kita dapat menggunakan Digispark Attiny85 karena harganya cukup murah dibanding dengan yang lainnya.

### Apa itu Digispark Attiny85?

Digispark Attiny85 merupakan board development yang dikembangkan oleh digistump. Digispark ini sangat sederhana dan kompatibel dengan arduino. Selain itu harganya juga cukup terjangkau.

Harga Digispark Attiny85 yang saya beli pada toko online sekitar Rp.40.000.
<img src="/assets/images/blog/5-membuat-badusb/02-pembelian-digispark.png" alt="Digispark Attiny85" width=75%> <br>
