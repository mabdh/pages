---
layout: post
date: 2013-05-26 17:35:59
title: Android App - MIPS Calculator
description: 
summary: 
tags: 
- android
- mips
- processor
categories:
- Writings
---

Di post sebelumnya, saya punya tugas untuk membuat prosessor MIPS R3000 32-bit. Tugas tersebut adalah tugas dari mata kuliah Struktur Prosessor Digital. Jadi, ada 30 instruksi yang dimiliki oleh prosessor MIPS R3000 32-bit yang saya buat. Pada umumnya setiap instruksinya terdiri dari nama instruksi yang menyatakan operasi apa yang dilakukan, source yang menyatakan sumber yang ingin dioperasikan, dan destination yang menyatakan tempat hasil dari nilai yang telah dioperasikan.
```
Misal : add, $s1, $s2, $t3

Artinya : Nilai yang ada di register $s2 ditambah dengan nilai yang ada di register $t3, dan hasilnya disimpan ke dalam register $s1.
```

Setiap komponen dari instruksi, direpresentasikan dalam kode yang disebut dengan op-code dan function-code yang direpresentasikan kembali ke dalam bilangan biner. Semua perhitungan yang dilakukan baik dari simulasi menggunakan VHDL maupun coret-coretan dilakukan dalam angka biner, untuk mempermudahnya bisa dilakukan di dalam angka heksadesimal.

MIPS Calculator ini saya buat untuk mempermudah saya dalam mengitung berapa representasi biner dari sebuah instruksi. Hanya dengan mengetik instruksi secara lengkap seperti contoh diatas, pengguna dapat melihat representasi instruksi tersebut dalam bilangan biner maupun heksadesimal. Daripada melihat-lihat tabel dan kemudian mencorat-coret (menghitung) bilangan biner dari sebuah instruksi, dengan menggunakan program ini, pengerjaan tugas perancangan MIPS jadi lebih mudah.

Program dibuat dalam bahasa JAVA dan dibuat untuk handphone dengan OS Android. Program bisa didownload [disini](http://cl.ly/0s2S3P182A2Z3e3E1P0h).
