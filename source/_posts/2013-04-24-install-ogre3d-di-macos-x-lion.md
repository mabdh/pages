---
layout: post
date: 2013-04-24 17:35:59
title: Install Ogre3D di Mac OS X Lion
description: 
summary: 
tags:
- ogre3d
- computer graphics
categories:
- Writings
---

Dalam rangka memperingati tugas GPU, maka saya mencoba memakai 3D engine Ogre3D ini. Ada beberapa hal yang perlu didownload dan install.

1. Ogre3D SDK untuk Mac (http://www.ogre3d.org/download/sdk)
2. Ogre Dependencies (http://sourceforge.net/projects/ogre/files/) bisa juga lewat macport (http://www.ogre3d.org/tikiwiki/Prerequisites?tikiversion=Mac+OS+X+%26+iOS)
3. CG ToolKit untuk NVidia (developer.nvidia.com/cg-toolkit-download)
4. CMake (http://www.cmake.org/cmake/resources/software.html)
5. Dan tool-tool lain seperti OIS (http://sourceforge.net/projects/wgois/?source=dlp), Boost, dan lain lain (optional)

- Ogre3D SDK 1.9.0
- Ogre Dependencies 20120525
- ois v-1.3
- cg-3.1-february2012
- CMake 2.8.10

Jadi pertama kali nyoba, langsung download SDK, copy project SDK ke folder Applications, ekstrak dependencies, folder dependenciesnya dikopi ke folder project SDK tadi. Langsung buka project Xcodenya. Kemudian klik dua kali di project, muncul window baru project setting, pilih tab build, pilih User-defined setting, Add User-defined setting, namanya pilih OGRE_SDK , valuenya alamat folder project (~/Applications/OgreSDK/) terus langsung di build. Setelah selesai build ada error satu. Katanya ada error di CMake post build rules , ln ./: invalid argument.

Akhirnya nyoba cara kedua, build XCode project pake Cmake (http://www.ogre3d.org/tikiwiki/tiki-index.php?page=Setting+Up+An+Application+-+Mac+OSX). Ketika build project pake CMake, biar lebih pasti, maka file CMakeLists.txt diubah. Bagian-bagian penting yang harus diubah adalah :

```
set(OGRE_PROJECT_NAME
  "OGRETutorialFramework"
)
set(CMAKE_INSTALL_PREFIX "/Users/(username)/OgreProject/build/bin")
set(OGRE_SOURCE_DIR "/Users/(username)/Applications/OgreSDK")

juga tambahkan :

set(OGRE_HOME "/Users/(username)/Applications/OgreSDK")
Setelah itu baru run pake terminal :
```

Buka terminal, pindah ke folder `/Users/(username)/OgreProject/`,
```
cd /Users/(username)/OgreProject
```
Buat direktori baru
```
mkdir build
```
Pindah ke direktori tersebut
```
cd build
```
Baru run cmake di folder build
```
ccmake -GXcode ..
```
Ketika melakukan configure, ada yang harus diubah, ubah CMAKE_INSTALL_PREFIX menjadi :
```
CMAKE_INSTALL_PREFIX = /Users/(username)/OgreProject/build/install
```
Setelah selesai di configure, quit cmake.

Setelah itu barulah kita buka XCode, dan build & run. Pada akhirnya masih keluar error yang sama seperti cara pertama.

![ogre error](/images/ogre-error.png)

Sampai sekarang saya masih belum tahu solusinya bagaimana.
