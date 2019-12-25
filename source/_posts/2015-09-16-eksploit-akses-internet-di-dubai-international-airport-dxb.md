---
layout: post
date: 2015-09-16 17:35:59
title: Eksploit akses internet di Dubai International Airport (DXB)
description: 
summary: 
tags: 
- exploit
- wifi
- internet access
categories:
- Writings
---

Satu bulan yang lalu saya transit beberapa jam di bandara Dubai International Airport (DXB). Secara default, bandara ini hanya menyediakan internet gratis selama 60 menit. Cara mendapatkannya adalah dengan menggunakan Wi-Fi lalu kemudian buka browser. Untuk beberapa smartphone (browser), sebuah portal log-in akan terbuka secara otomatis. Akan tetapi ada beberapa smartphone (browser) yang tidak membuka portal log-in secara otomatis.

Ketika browser terbuka, halaman segera ter-redirect ke http://portal.boingohotspot.net/en/dxb dan terdapat tulisan Welcome to Dubai International Airport (Get Online Now). Contoh gambarnya tidak ada karena saya lupa melakukan screenshoot. Jika kita pilih (Get Online Now), maka akan terdapat dua pilihan yang muncul, Complimentary Wi-Fi 60 minutes dan Boingo 1 Hour. Pilihan pertama merupakan akses Wi-Fi gratis selama 60 menit dan hanya dapat dilakukan sekali saja. Pilihan kedua merupakan akses Wi-Fi berbayar yang dapat digunakan jika kita membayar menggunakan kartu kredit.

Cara yang digunakan sangat newbie-friendly tanpa harus mencari backdoor, bruteforce, menggunakan KaliLinux untuk melakukan pen-test dan lain-lainnya seperti yang dilakukan Elliot Alderson di serial Mr.Robot. Akan tetapi caranya sangat mudah yaitu dengan mengubah URL.

Di kasus ini kita ingin mendapatkan akses lebih dari server hotspot boingo untuk bisa berinternet. Kalau ada cara yang mudah, untuk apa susah-susah.

Berikut langkah-langkah untuk berinternet dengan santai di bandara Dubai.

1. Gunakan Wi-Fi gratis secara normal selama 60 menit untuk menghormati pihak bandara yang telah menyediakan Wi-Fi gratis (hanya) selama 60 menit.
2. Jika masih kurang lakukan cara berikut.
3. Langsung tembak URL http://portal.boingohotspot.net (tanpa /en/dxb). Kemudian halaman berikut akan terbuka.

![eksploit int dub](eksploit-int-dub.png)

Di halaman tersebut terdapat combo-box “Choose venue”. Di dalamnya terdapat daftar bandara-bandara yang akses internetnya disediakan oleh Boingo.

![eksploit int dub 1](eksploit-int-dub-1.png)

 Lalu pilih salah satu bandara yang diinginkan. Kebanyakan dari bandara-bandara tersebut menyediakan Wi-Fi gratis dengan durasi yang berbeda-beda. Contohnya adalah bandara AUS-Austin Bergstrom International Airport yang memiliki durasi 90 menit dan DTW-Detroit Metropolitan Wayne County Airport memiliki durasi 24 jam.

![eksploit int dub 2](eksploit-int-dub-2.png)

![eksploit int dub 3](eksploit-int-dub-3.png)

Gratis internet 90 menit

![eksploit int dub 4](eksploit-int-dub-4.png)

![eksploit int dub 5](eksploit-int-dub-5.png)

### Gratis Wi-Fi sehari penuh

Portal Wi-Fi Boingo ini sepertinya mencatat MAC address setiap device yang kita gunakan untuk berinternet sehingga kita hanya dapat menggunakan satu device sekali saja untuk berinternet. Trik ini juga kemungkinan besar dapat digunakan pada bandara-bandara yang terdapat di list sebelumnya.

Yak jadi begitu. Caranya mudah cukup dengan hanya mengganti URL.
