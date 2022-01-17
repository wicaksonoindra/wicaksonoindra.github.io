---
title: "Kontrol Akses File Linux"
layout: post
date: 2021-12-06 16:36
headerImage: true
hidden: false
tag:
- administration
- controll access
- linux
star: false
category: blog
author: wicaksonoindra
description: Markdown summary with different options
---

### Basic Linux Permission

![terminal](/assets/images/blog/3-kontrol-akses-linux/list-detail.png)

Linux permission terdapat pada dua jenis, yaitu Permission pada File dan Permission pada Directory. Permissionnya terbagi menjadi tiga yaitu read, write dan execute.

|        |File    |Directory|
|----    |----    |----|
|Read    |Open    |List|
|Write   |Modify  |Create/Delete|
|Execute |Run     |CD  |

1. Read(r), pada sebuah file artinya yaitu membuka file atau membaca isinya. Namun pada sebuah directory ini berarti dapat melihat list file maupun folder yang terdapat pada directory tersebut.
2. Write(w), pada sebuah file berarti memiliki izin untuk memodifikasi isi file tersebut. Lalu pada sebuah directory(folder) ini berarti dapat menghapus atau membuat suatu folder/file pada directory tersebut.
3. Execute(x), pada sebuah file ini berarti file tersebut dapat di eksekusi atau dijalankan. Namun pada sebuah directory ini berarti kita dapat masuk ke dalam folder tersebut.

![illustration](/assets/images/blog/3-kontrol-akses-linux/symbol-mode.png)

Huruf pertama menunjukan bahwa item tersebut bertipe directory(folder). Jika baris pertama menunjukan huruf `-` maka item tersebut merupakan sebuah file. Permission pada linux terbagi menjadi tiga bagian yang di tunjukan pada bagian merah, hijau dan biru.
Permission pada bagian pertama merupakan hak akses milik user, lalu pada permission bagian kedua merupakan hak akses milik group dan permission bagian ketiga merupakan hak akses milik other.

### Change Ownership

Pada setiap file maupun directory pada System Linux di asosiasikan dengan kelompok kepemilikan(ownership) dan pemilik(owner). Berikut contoh ownership pada suatu directory.

![terminal](/assets/images/blog/3-kontrol-akses-linux/ownership.png)

Titik yang ditunjukan oleh panah kuning merupakan user pemilik dari directory tersebut. Sedangkan titik yang ditunjukan oleh panah merah merupakan grup pemiliknya.
Kita dapat mengganti kepemilikan dari file maupun directory dengan command

```powershell
chown user_baru:grup_baru nama_file
```

Pastikan saat mengubah kepemilikan file maupun directory kita harus masuk sebagai user root terlebih dahulu. Contohnya kita akan mengubah kepemilikan ownership directory dir-a di atas dari milik user indraw dan milik group indraw menjadi milik user kali dan milik group grup-1.

![terminal](/assets/images/blog/3-kontrol-akses-linux/chown-1.png)

Sekarang kepemilikan dir-a sudah berubah yaitu menjadi milik user kali yang sebelumnya milik user indraw dan pemilik group sudah berubah menjadi grup-1 yang sebelumnya milik dari group indraw.
Perlu diketahui bahwa jika kita mengubah kepemilikan suatu directory(folder), semua isi dalam suatu folder tersebut secara default tidak ikut terubah kepemilikannya. Kita dapat menggunakan opsi -R untuk ikut mengubah kepemilikan dari seluruh isi folder yang ingin kita ubah. Contoh:

![terminal](/assets/images/blog/3-kontrol-akses-linux/chown-2.png)

### Change Permission

Kita dapat mengubah permission dari suatu file maupun directory dengan command
```powershell
chmod ugo+rwx nama_file
```
Artinya, u untuk user, g untuk group, o untuk other. Lalu tanda + artinya menambahkan, dan dilanjutkan dengan r yaitu read, w yaitu write dan x artinya execute. Kita juga dapat menghapus persmission dengan tanda -  yang merupakan kebalikan dari tanda +.
Contoh:
Jika kita ingin menghapus permission read user, maka kita dapat mengubahnya seperti ini.

![terminal](/assets/images/blog/3-kontrol-akses-linux/chmod-1.png)

Permission read pada user sudah berhasil di hapus. Lalu jika kita ingin menambahkan permission write pada other, kita dapat mengubahnya seperti berikut.

![terminal](/assets/images/blog/3-kontrol-akses-linux/chmod-2.png)

Jika ingin mengubah permission pada seluruh isi directorynya juga, kita dapat menggunakan opsi `-R`.

### Change Permission with Number

Kita juga dapat mengubah permission file dengan metode angka. Setiap permission memiliki nilai angka masing masing, yaitu:
- read = 4
- write = 2
- execute = 1
- `-` = 0

Pada directory dir-a tadi memiliki permission seperti berikut:

|d |-wx|r-x|rwx|
|--|--|--|--|
|  |0+2+1|4+0+1|4+2+1|

Maka total angka untuk user adalah 3, untuk group adalah 5 dan untuk other adalah 7. Angka permissionnya adalah 357. Contoh:

Jika kita ingin mengubah permissionnya menjadi user dapat semua akses, group hanya membaca dan other hanya membaca, kita dapat mengubahnya menjadi seperti berikut.

![terminal](/assets/images/blog/3-kontrol-akses-linux/chmod-3.png)

Permissionnya telah berubah menjadi:

|d |rwx|r--|r--|
|--|--|--|--|
|  |4+2+1|4+0+0|4+0+0|

Dengan total user 7, group 4 dan other 4.

Berikut merupakan setting yang biasa digunakan:
- rw------- (600) -- Hanya user yang dapat akses read dan write.
- rw-r--r-- (644) -- User yang mendapat akses read dan write; group dan other hanya mendapat akses read.
- rwx------ (700) -- Hanya user yang mendapat akses read, write dan execute.
- rwx------ (700) -- Hanya user yang mendapat akses read, write dan execute.
- rwx--x--x (711) -- User mendapat akses read, write and execute permissions; the group and others can only execute.
- rw-rw-rw- (666) -- Semua dapat akses read dan write.
- rwxrwxrwx (777) -- Semua dapat akses read, write dan execute.
