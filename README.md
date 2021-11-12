# Laporan Proyek Machine Learning - Muhammad Fadli Ramadhan

## Project Overview

Domain proyek yang saya pilih dalam proyek Machine Learning Sistem Rekomendasi ini adalah mengenai Tempat Kuliner dengan judul "Recommend top restaurants based on preference".

Menurut [Wikipedia](https://id.wikipedia.org/wiki/Rumah_makan), **Rumah makan** atau **restoran** adalah istilah umum untuk menyebut usaha gastronomi yang menyajikan hidangan kepada masyarakat dan menyediakan tempat untuk menikmati hidangan tersebut serta menetapkan tarif tertentu untuk makanan dan pelayanannya. Meski pada umumnya rumah makan menyajikan makanan di tempat, tetapi ada juga beberapa yang menyediakan layanan take-out dining dan delivery service sebagai salah satu bentuk pelayanan kepada konsumennya. Rumah makan biasanya memiliki spesialisasi dalam jenis makanan yang dihidangkannya. Sebagai contoh yaitu rumah makan chinese food, rumah makan Padang, rumah makan cepat saji (fast food restaurant) dan sebagainya. Di Indonesia, rumah makan juga biasa disebut dengan istilah restoran. Restoran merupakan kata resapan yang berasal dari bahasa Prancis yang diadaptasi oleh bahasa inggris; "restaurant" yang berasal dari kata "restaurer" yang berarti "memulihkan"

[Sistem Rekomendasi](https://en.wikipedia.org/wiki/Recommender_system)  adalah subkelas sistem penyaringan informasi yang berupaya memprediksi "peringkat" atau "preferensi" yang akan diberikan pengguna pada suatu item.
Sistem pemberi rekomendasi digunakan di berbagai bidang, dengan contoh yang umum dikenal berupa generator daftar putar untuk layanan video dan musik, pemberi rekomendasi produk untuk toko online, atau pemberi rekomendasi konten untuk platform media sosial dan pemberi rekomendasi konten web terbuka.

Proyek ini penting untuk diselesaikan agar Pelanggan atau User mendapatkan rekomendasi restoran dengan penilaian terbaik dan memberikan banyak pilihan untuk memilih restoran dengan ID yang tersedia. Dari pihak restoran, sistem pemberi rekomendasi ini sangat penting untuk mengingkatkan kualitas restoran dan meningkatkan jumlah pelanggan.


## Business Understanding

### Problem Statements

Sebagai data analyst, anda ingin memanfaatkan data tersebut untuk meningkatkan kualitas layanan dan rating perusahaan. Namun, anda memiliki rincian masalah berikut :
- Bagaimana membuat model machine learning untuk merekomendasikan ID restoran berdasarkan rating/penilaian tertinggi User ?
- Bagaimana cara membuat model Machine Learning untuk merekomendasikan ID restoran lain yang mungkin disukai dan belum pernah dikunjungi oleh user?

### Goals

Berdasarkan rincian masalah diatas, berikut adalah tujuan proyek ini:
- Membuat model Machine learning yang dapat merekomendasikan ID restoran berdasarkan penilaian tertinggi user dengan teknik *Popularity based Recomender Model* agar mendapatkan rekomendasi ID restoran dengan popularitas tertinggi.
- Membuat model Machine Learning untuk merekomendasikan ID restoran lain yang mungkin disukai dan belum pernah dikunjungi oleh user dengan teknik Collaborative Filtering : SDV.

### Solution statements

Untuk menyelesaikan masalah ini, saya mengajukan 2 solusi approach (algoritma atau pendekatan sistem rekomendasi). yaitu teknik Popularity based Recommender Model
Collaborative Filtering Model. Berikut adalah penjelasan teknik-teknik yang akan digunakan untuk masalah ini :
- **Popularity based Recommender Model :** Seperti namanya, ini merekomendasikan berdasarkan apa yang sedang tren/populer di seluruh situs. Ini sangat berguna ketika Anda tidak memiliki data masa lalu sebagai referensi untuk merekomendasikan produk kepada pengguna. Ini tidak cocok untuk kelompok penonton atau film tertentu.
- **Collaborative Filtering :** Pada tahap ini, sistem merekomendasikan sejumlah restoran berdasarkan rating yang telah diberikan sebelumnya. Dari data rating pengguna, kita akan mengidentifikasi restoran-restoran yang mirip dan belum pernah dikunjungi oleh pengguna untuk direkomendasikan. Teknik ini menggunakan model based collaborative filtering : SVD (Singular Value Decomposition)

## Data Understanding
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/DataUnderstanding1.png?raw=true)

Dataset ini digunakan untuk studi di mana tugasnya adalah menghasilkan daftar restoran teratas sesuai dengan preferensi konsumen dan menemukan fitur yang signifikan.
Sumber Dataset : [Kaggle Dataset : Recommend top restaurants based on preference](https://www.kaggle.com/uciml/restaurant-data-with-consumer-ratings)

Di dalam dataset ini terdapat 9 file csv dan 1 file readme. Untuk keperluan proyek saya ini, saya hanya menggunakan 1 file csv saja. Yaitu rating_final.csv yang memiliki 5 fitur.
**rating_final.csv**
- Instansces : 1161
- Attributes : 5
- `userID`  Nominal, merupakan ID Pengguna yang memberikan penilaian 
- `placeID` Nominal, merupakan ID Restoran yang akan dinilai 
- `rating`  Numeric 0 - 2, merupakan penilaian restoran menurut user 
- `food_rating`  Numeric 0 - 2, merupakan penilaian makanan restoran menurut user
- `service_rating`  Numeric 0 - 2, merupakan penilaian pelayanan restoran menurut user

Kami menggunakan dataset 'rating_final' untuk merekomendasikan restoran berdasarkan popularitas & berdasarkan Collaborative yaitu peringkat yang diberikan oleh pengguna lain.

Saya juga melakukan eksplorasi data untuk memahami variabel pada data serta korelasi antar variabel,dsb.
**rating_final.csv**
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)

Berdasarkan output diatas, diketahui bahwa file rating_final.csv memiliki 1161 entri.

![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/3.png?raw=true)

Berdasarkan output di atas, disimpulkan bahwa nilai maksimum dan minimum untuk seluruh rating adalah 2 dan 0. 

Untuk memahami dataset secara detail, penting untuk melakukan EDA, seperti pada langkah berikut :
* Jumlah pengguna unik, restoran unik, no. rating, food_ratings, service_ratings
* Berapa kali pengguna menilai
* Berapa kali restoran dinilai
* Bagaimana distribusi peringkat untuk makanan, layanan

![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/4.png?raw=true)

Berdasarkan output diatas

![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)
![image](https://github.com/fadlinisasiGit/Laporan-Proyek-Machine-Learning-2/blob/main/2.png?raw=true)


## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
