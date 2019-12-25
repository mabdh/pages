---
layout: post
date: 2013-04-23 17:35:59
title: Install OpenCV Android di Eclipse
description: 
summary: 
tags: 
- android
- opencv
- install
categories:
- Writings
---

Setelah nyoba di Mac OS, akhirnya saya juga nyoba buat Android. Pertama-tama siapkan Eclipse Java atau Android Development Toolkit juga boleh. Pertama-tama saya nyoba pake Eclipse Java karena jaman dulu sekitar dua tahun lalu belum ada Android Development Toolkit yang welcome screen-nya lebih keren. Tapi akhirnya setelah dikasih tahu nanu, saya download ADT, sekitar 300MB, hampir sampe kuota AI3.
Setelah itu download juga CDT Plugin buat Eclipse. Di Eclipse pilih Help -> Install New Software -> Add -> Masukin alamatnya http://download.eclipse.org/tools/cdt/releases/juno (khusus Eclipse Juno). Kasih nama CDT aja , sebenernya bebas sih.
Kemudian download juga OpenCV buat Android di opencv.org.
Terakhir download OpenCV Manager dari Google Play buat di-install di Android-nya.
Oh iya sebelumnya, setahu saya, Android yang bisa pake ini cuma yang API Level 8 ke atas, karena HP Android saya Level 7 jadi tidak bisa langsung debugging pake HP. Nanti kalo udah rusak baru beli lagi.

Sebenarnya dapet referensi dari sini : http://docs.opencv.org/doc/tutorials/introduction/android_binary_package/O4A_SDK.html

Setelah semua bahan sudah siap, ekstrak file OpenCV Android, lalu buka Eclipse atau ADT, kemudian klik kanan di project explorer dan pilih import. Pilih yang import existing project -> pilih folder OpenCV Android yang sudah diekstrak (akan ada banyak project yang akan di import) -> kemudian finish. Terus ikutin aja settingannya mulai dari setting C/C++ Build sampe setting Build command-nya kaya link di atas.

Setelah itu build project yang namanya OpenCV, setelah berhasil di build, project tersebut akan menghasilkan file .jar yang terletak di folder bin di dalam projectnya.

Tips kalo ada error :

Setiap example atau project yang mau dibuat, harus dimasukin file hasil build project OpenCV yang .jar itu. Caranya, klik kanan project yang dibuat (misal : project sampel), kemudian klik Properties -> Java Build Path -> Pilih tab library -> terus Add Jar -> pilih file .jar hasil dari build project yang namanya OpenCV tadi. Setelah itu baru error-nya akan hilang dan bisa di build. Setelah dibuild baru bisa di-run, tapi build automatically juga bisa. Kalo mau langsung debugging lewat HP Android. Setting dulu debuggable-nya di AndroidManifest.xml pilih Application (jangan langsung ubah file text di xml nya – istilahnya hard coding), terus ubah Debuggable-nya jadi true. Selesai.
