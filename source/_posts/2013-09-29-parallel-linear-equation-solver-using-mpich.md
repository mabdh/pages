---
layout: post
date: 2013-09-29 17:35:59
title: Parallel Linear Equation Solver Using mpich
description: 
summary: 
tags: 
- mpi
- parallel
- numeric-method
categories:
- Writings
---

### Spesifikasi
- Program dapat memberikan solusi dari bermacam-macam persamaan linear
- Persamaan linear yang diberikan terdiri dari 100/512 variabel
- Program dibuat dalam serial serta parallel menggunakan MPI

## METODE SOLUSI LINEAR
Metode yang solusi persamaan linear yang akan digunakan dalam program adalah metode eliminasi gauss dengan partial pivoting.

### Eliminasi Gauss

Metode eliminasi gauss diimplementasikan dengan membuat matrix augmentasi, berikut ini adalah contoh persamaan linear :

Matrix augmentasinya adalah

![linear eq 1](/images/linear-eq-1.png)

Tujuan akhir dari eliminasi gauss adalah menghasilkan matrix triangular dengan bentuk row echelon, dimana diagonal atas dari matrix bernilai 1, sedangkan nilai dibawah diagonal adalah 0. Untuk mendapat  matrix triangular, dilakukan operasi baris elementer, yakni menggunakan baris acuan, dalam hal ini baris teratas dimana terdapat angka 1 pada bagian kiri matrix.

Pada matrix diatas, pivot pertama nya adalah baris ke 1. Gunakan operasi aritmatika terhadap baris lain agar kolom pertama pada matrix bernilai 0, selain pada baris pivot(ke 1). Setelah kolom berisi nol, pivot berpindah ke baris kedua, namun kali ini nilai yang harus nol adalah seluruh kolom kedua, lalu operasi berlanjut seterusnya hingga mencapai baris terakhir.

Berikut ini adalah contoh matrix triangular row echelon

Untuk mendapatkan solusi dari persamaan linear, matrix row echelon tersebut perlu direduksi dengan back-to-back substitution sehingga menghasilkan matrix :

![linear eq 2](/images/linear-eq-2.png)

Berikut ini adalah yang dilakukan operasi baris elementer

- Mengganti satu baris dengan menjumlahkan baris itu dan mengalikan pada baris lain
- Menukar tempat dua baris
- Mengalikan semua elemen dalam baris dengan konstanta bukan nol

### Partial Pivoting

Partial pivoting merupakan submetode dari eliminasi gauss , perbedaannya adalah, jika eliminasi gauss biasa pivot nya(baris acuannya) berada paling atas dari matrix, pada partial pivoting, pivotnya adalah nilai absolute maksimum dari matrix. Setelah mendapat nilai maksimum, nilai tersebut dipindah kebaris teratas, lalu dilakukan operasi baris elementer seperti diatas. Untuk pivot baris selanjutnya merupakan nilai absolute maksimum juga, hal ini iterative hingga baris terakhir.

### LANGKAH PENGERJAAN PROGRAM PARALEL
- Matrix augmentasi diimplementasikan dengan  sebuah matrix dan array. Matrix berisi koefisien-koefisien dari persamaan, sedangkan array berisi hasil dari persamaan. Solusi persamaan linear diimplementasikan dengan array.
- Persamaan linear diload dari file external, sedangkan solusinya juga disimpan pada file external
- Operasi eliminasi dilakukan pada tiap kolom, sehingga operasi ini berulang sebanyak besar dari kolom matrix
- Langkah dari operasi pertama adalah mencari pivot, dimana nilai koefisien dari kolom yang bersangkutan adalah nilai terbesar.
- Langkah berikutnya memindahkan pivot ke baris teratas dari wilayah operasi eliminasi
- Selanjutnya adalah melakukan operasi baris elementer. Dimana pada tiap baris pada kolom yang sama dilakukan operasi pengurangan dan pembagian yang mengacu pada nilai pivot yang representative
- Kemudian back-to-back substitution agar menghasilkan matrix reduced row echelon. Operasi yang dilakukan juga menggunakan operasi baris elementer.
- Processor rank = 0 , memiliki peran yakni :

  1. Melakukan pencarian nilai absolute maksimum tiap pivot
  2. Melakukan pengubahan baris pivot, menjadi teratas tiap wilayah operasi
  3. Mengirimkan data setelah pivot sudah benar, kepada processor rank lain
  4. Menerima kembali data dari processor lain setelah dilakukan operasi baris elementer
  5. Melakukan operasi back-subtitution

- Processor rank !=0 memiliki peran yakni melakukan operasi baris elementer
- Data dibagi secara seimbang sesuai jumlah processor yang digunakan

Contoh cara kerja program pada matriks 4 x 4 :

![linear eq 3](/images/linear-eq-3.png)

![linear eq 4](/images/linear-eq-4.png)

![linear eq 5](/images/linear-eq-5.png)

![linear eq 6](/images/linear-eq-6.png)

![linear eq 7](/images/linear-eq-7.png)

Hasil matriks triangular pada konsol :

![linear eq 8](/images/linear-eq-8.png)

Setelah itu barulah direduksi dengan back-to-back substitution untuk mendapatkan solusi persamaan linear.
