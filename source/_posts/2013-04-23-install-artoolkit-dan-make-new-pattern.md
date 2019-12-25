---
layout: post
date: 2013-04-23 17:35:59
title: Install ARToolkit & Make New Pattern
description: 
summary: 
tags:
- artoolkit
- AR
- macos
categories:
- Writings
---

Setelah kemarin coba download ARToolKit dari http://www.hitl.washington.edu/artoolkit/download/ , di website situ juga ada penjelasan cara installnya ,

disini http://www.hitl.washington.edu/artoolkit/documentation/

dan disini http://www.hitl.washington.edu/artoolkit/documentation/usersetup.htm.

Tinggal download terus buka projectnya terus build salah satu project dan selesai.

Kalo ada pattern baru yang mau dikenali, perlu dibuat dulu patternnya dengan menggunakan tools yang ada di ARToolKit, ada di folder ARToolKit/bin . Ada file yang bernama mk_patt, untuk Linux atau MacOs jangan langsung diklik filenya karena akan error nantinya. Lebih baik pakai terminal kemudian pindah ke direktori ARToolKit, lalu buka lewat terminal dengan ./mk_patt . Setelah itu akan diminta camera parameter, langsung enter aja karena pattern ingin langsung diambil lewat kamera. Kemudian arahkan pattern ke depan kamera, usahakan pattern yang ingin dibuat ada border putih dipinggirnya agar program mengenali edge pattern. Jika edge pattern atau pinggiran pattern terdeteksi, maka akan ada garis merah dan hijau di sebelah kanan bawah dan kiri atas. Setelah itu putar patternnya dan lihat apakah garis merah dan hijau masih tetap mengelilingi pattern, jika masih maka klik kiri pada mouse. Setelah itu di terminal akan keluar ‘filename : ‘ simpan dengan nama apa saja, usahakan diakhiri dengan .pat. Setelah itu file pattern baru akan tersimpan di dalam folder yang sama dengan file mk_patt.
