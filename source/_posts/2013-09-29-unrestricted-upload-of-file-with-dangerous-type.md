---
layout: post
date: 2013-09-29 17:35:59
title: Unrestricted Upload of File with Dangerous Type
description: 
summary: 
tags: 
- security
- web
categories:
- Writings
---

Pada sebuah aplikasi biasanya terdapat fitur yang membutuhkan file untuk diupload seperti file gambar dan dokumen. Seorang penyerang aplikasi dapat memanfaat fitur tersebut dengan mengupload file-file yang berbahaya. File tersebut biasanya merupakan file yang berekstensi .php karena file .php merupakan file yang berisi kode-kode yang dijalankan pada server.

Pada contoh kasus kali ini terdapat sebuah file .html yang berisi form untuk mengupload gambar dan sebuah file .php di server yang akan menyimpan gambar yang diupload ke direktori di server.

![unrestricted upload 1](/images/unrestricted-upload-1.png)

Gambar 1. Tampilan file index.html

![unrestricted upload 2](/images/unrestricted-upload-2.png)

Gambar 2. Source kode file index.html

![unrestricted upload 3](/images/unrestricted-upload-3.png)

Gambar 3. Source code file upload_picture.php

Terdapat dua kasus yang akan dicoba pada aplikasi upload file ini. Pertama dengan mengupload file gambar yang semestinya dan kedua dengan mengupload sebuah file .php yang  berisi kode yang berbahaya.

- Mengupload file gambar
Pada kasus pertama ini sebuah file gambar berformat .png diupload dengan menekan tombol submit pada form aplikasi. Kemudian setelah berhasil diupload, file upload_picture.php memberikan informasi kepada pengguna nama, tipe, dan ukuran file gambar yang diupload. Untuk kasus ini aplikasi berjalan dengan semestinya karena memang ditujukan untuk menupload file gambar.

![unrestricted upload 4](/images/unrestricted-upload-4.png)

Gambar 4. Tampilan file index.html

![unrestricted upload 5](/images/unrestricted-upload-5.png)

Gambar 5. Tampilan file index.html setelah file gambar berhasil diupload

![unrestricted upload 6](/images/unrestricted-upload-6.png)

Gambar 6. Tampilan web ketika file gambar berhasil diupload

- Mengupload file .php
Namun apa yang terjadi bila seorang pengguna mengupload file .php yang berisi kode yang tidak diinginkan. File .php yang akan diupload merupakan file malicious.php yang memiliki kode sebagai berikut. File ini bertujuan agar penyerang dapat memberikan command melalui url.

![unrestricted upload 7](/images/unrestricted-upload-7.png)

Gambar 7. Tampilan source code malicious.php

![unrestricted upload 8](/images/unrestricted-upload-8.png)

Gambar 8. Tampilan file index.html ketika file malicious.php siap diupload

![unrestricted upload 9](/images/unrestricted-upload-9.png)

Gambar 9. Tampilan web ketika file malicious.php berhasil diupload

Setelah file malicious.php berhasil diupload, penyerang dapat memasukkan command pada URL web browser. Pada gambar dibawah terlihat bahwa command yang dimasukkan adalah “ls –l” dan URL yang dimasukkan adalah “localhost/images/malicious.php?cmd=ls%20-l” yang berfungsi untuk melihat file-file apa saja yang terdapat di dalam direktori tempat penyimpanan gambar pada server.

![unrestricted upload 10](/images/unrestricted-upload-10.png)

Gambar 10. Tampilan web ketika command dimasukkan(1)

Selain itu, mencoba mengubah atribut file yang berada pada direktori penyimpanan dengan memasukkan URL “localhost/images/malicious.php?cmd=chmod%20777%20LogoITB1920px600jpg.png”.

![unrestricted upload 11](/images/unrestricted-upload-11.png)

Gambar 11. Tampilan web ketika command dimasukkan(2)

Setelah itu, masukkan command untuk melihat daftar file beserta atributnya dan atribut dari file tersebut sudah berubah.Image

![unrestricted upload 12](/images/unrestricted-upload-12.png)

Gambar 12. Tampilan web ketika command dimasukkan(3)

### Pencegahan dan solusi
Beberapa cara pencegahan masalah upload file dengan format yang tidak inginkan adalah sebagai berikut.

Membuat sendiri format nama file yang dapat diterima oleh aplikasi sehingga pengguna tidak dapat mengupload dengan sembarang nama file,
Apabila syarat upload objek-objek file yang dapat diupload telah diketahui orang banyak sebaiknya buat parameter ID baru yang dipetakan ke nama file atau URL. Jika input yang diberikan bukan merupakan parameter ID maka harus ditolak,
Pertimbangkan untuk menyimpan seluruh file yang diupload diluar root web server, kemudian buat mekanisme yang baru untuk mengakses file tersebut,
Periksa setiap file yang dimasukkan termasuk tipe dan nama file.
### Implementasi pencegahan
Salah satu cara pencegahan pada upload file yang tidak diinginkan adalah dengan melakukan cek tipe file. Pada file upload_picture.php sebelumnya ditambahkan kondisi-kondisi untuk mengecek file. Gambarnya adalah sebagai berikut, bagian tulisan yang diblok biru adalah kondisi yang ditambahkan untuk mengecek apakah file yang diupload merupakan file gambar atau bukan.

![unrestricted upload 13](/images/unrestricted-upload-13.png)

Gambar 13. File upload_picture.php yang sudah ditambahkan dengan pengecekan tipe file

Setelah dicoba lagi untuk mengupload file malicious.php, maka aplikasi tidak dapat menerima file tersebut dan keluarannya adalah sebagai berikut.

![unrestricted upload 14](/images/unrestricted-upload-14.png)

Gambar 14. Tampilan website

Sumber:
Internet: http://cwe.mitre.org/data/definitions/434.html, Oct. 30, 2012 [Sep. 29, 2013].

Internet: http://www.w3schools.com/php/php_file_upload.asp, [Sep. 29, 2013].
