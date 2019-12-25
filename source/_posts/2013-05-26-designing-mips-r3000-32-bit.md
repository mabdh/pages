---
layout: post
date: 2013-05-26 17:35:59
title: Designing MIPS R3000 32-bit Processor
description: 
summary: 
tags: 
- mips
- processor
- design
- 32bit
categories:
- Writings
---

Sekitar tepat tahun lalu kira-kira bulan Mei 2012, pada semester 6, saya mengambil kuliah yang bernama Struktur Prosessor Digital. Jangan ditanya alasan kenapa saya mengambil mata kuliah ini. Karena saya sendiri tidak tahu. Mungkin karena bosan dengan mata kuliah-mata kuliah yang jumlah pesertanya banyak. Bisa jadi. Mungkin karena bosan dengan mata kuliah-mata kuliah yang hanya membahas teori saja. Bisa jadi. Mungkin juga karena tertantang untuk bekerja keras. Karena yang saya dengar, dengan mengambil kuliah ini, pesertanya diberikan tugas dan project yang banyak dan sulit.

Kata pertama yang tepat ketika mengambil mata kuliah ini adalah “Welcome to Digital World”. Di dalamnya dibahas mengenai seluk beluk dunia digital, mulai dari Data Flow Diagram, komponen-komponen digital, datapath, hingga perancangan prosessor. Semuanya serba menarik untuk dipelajari.

Pada akhir perkuliahan, setiap peserta diberikan sebuah tugas project yang isinya kira-kira berikut :

```
Buatlah rancangan suatu mikroprosesor MIPS-Sederhana sampai pada level diskripsi dalam VHDL yang synthesizable.

MIPS-Sederhana ini mengadopsi  ISA MIPS 32-bit (MIPS R3000)  dan menggunakan organisasi  pipelined 5-tahap, serta mampu mendukung 30 instruksi MIPS yang tertera  pada Tabel.
```

Isi dari tabel adalah daftar 30 instruksi beserta function code dan op-code seperti instruksi and, sub, add, or, sll, srl, dan lain-lain. Selain ditugaskan untuk membuat single-cycle processor, peserta juga ditugaskan untuk membuat pipelined processor sekaligus dengan hazard unit-nya. Hazard unit merupakan suatu unit pada prosessor yang berfungsi sebagai pengendali apabila hazard akan terjadi sehingga hazard dapat dihindari.

Datapath hasil dari perancangan prosessor MIPS R3000 32-bit yang saya buat adalah sebagai berikut :

![pipeline](/images/pipeline.png)

Sebenarnya saya tidak tahu gambar datapath diatas merupakan datapath yang final atau bukan, tapi karena di komputer nemunya yang itu, maka saya pajang saja.

Setelah kira-kira datapath-nya selesai dibuat, barulah design setiap kompoenen dengan menggunakan VHDL. Begitu ceritanya.

Tapi sayang sekali di kurikulum 2013 ini, mata kuliah struktur prosessor digital ini sudah tidak ada lagi. Padahal, mata kuliah ini juga dapat membantu mahasiswa khususnya seperti saya untuk memiliki pengalaman mendesain prosessor dan juga untuk berpikir secara digital.
