---
layout: post
date: 2013-04-23 17:35:59
title: Install OpenCV di Mac OS
description: 
summary: 
tags: 
- mac
- opencv
- install
categories:
- Writings
---

![Install OpenCV](/images/install-opencv.png)

Sekitar dua hari yang lalu saya install OpenCV, sebuah library untuk image processing. Berikut ceritanya.

Ada beberapa link yang jadi referensi buat install OpenCV di Mac OS, gatau kalo di linux bisa apa engga. Tapi kemungkinan besar caranya mirip. Kemarin liat-liat di website-website ini :
```
OpenCV on Mac OSX: A step-by-step guide

http://opencv.willowgarage.com/wiki/Mac_OS_X_OpenCV_Port

http://opencv.willowgarage.com/wiki/UsingOpenCVUnderOSX

```
Jadi ada banyak cara untuk menginstall OpenCV di Mac OS. Yang pertama download langsung librarynya di `http://opencv.org/`, yang kedua download OpenCV pake package manager lewat terminal. Saya lebih suka yang kedua karena lebih praktis dan librarynya langsung ke file system kita. Karena saya pake cara yang kedua, maka saya tidak membahas cara yang pertama.

Untuk download OpenCV lewat package manager, ada beberapa package manager yang bisa digunakan untuk download dan install OpenCV. Pertama pake MacPorts dan yang kedua make Homebrew. Kali ini saya make MacPorts, kenapa ? Karena berhasil download, kalo ga berhasil mungkin udah nyoba pake homebrew.

Perbedaan keduanya hanya pada direktori target tempat package diinstall saja. MacPorts akan menginstall package di direktori `/opt/local/` , sedangkan Homebrew menginstall package di direktori `/usr/local/`.

Cara download dengan MacPorts. Pertama buka terminal, terus ketik

sudo port selfupdate

(‘sudo’ agar kita punya akses superuser, setelah instruksi sudo akan selalu diminta password komputer, selfupdate untuk mengupdate package-package apa saja yang dapat diinstall)

```
sudo port install opencv
```

Selesai, file-file OpenCV sudah langsung ada di direktori `/opt/local/`

Setelah itu buka XCode, masukkan library-library dan setting segala dependencies-nya. Klik kanan di project, kemudian klik ‘Add files to “(namaproject)”‘. Di browse window ketik ‘/’ (slash) agar bisa memasukkan alamat secara manual, kemudian ketikkan `/opt/local/lib`.

Pilih dan masukkan semua file yang berbau libopencv agar project terhindar dari error. Setelah itu setting dependencies-nya. Klik projectnya (atau klik kanan project), kemudian pilih Build Settings -> Search paths , masukkan Header paths sebagai `/opt/local/include` dan Library paths `opt/local/libs`.

Setelah itu coba program example, jangan lupa cek headernya apakah sesuai dengan foldernya. Build dan selesai.
