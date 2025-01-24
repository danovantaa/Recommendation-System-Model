# Laporan Proyek Machine Learning - Zefanya Danovanta Tarigan

## Project Overview

Buku adalah kumpulan lembaran atau kertas yang mengandung tulisan, gambar, atau tempelan, yang dijilid pada salah satu sisinya. Bahan-bahan pembentuk buku bisa berupa kertas, kayu, bahkan gading gajah. Setiap sisi lembaran dalam buku disebut halaman. Seiring kemajuan teknologi, hadir pula buku elektronik (e-book) yang dapat diakses menggunakan perangkat seperti komputer, tablet, atau ponsel dengan perangkat lunak khusus [1].

Sistem rekomendasi digunakan untuk memprediksi atau mengidentifikasi barang, termasuk buku, yang sesuai dengan minat pengguna. Dengan kemajuan teknologi, tersedia berbagai platform yang memudahkan pengguna mencari referensi buku, baik melalui aplikasi digital maupun secara langsung [2].

Jumlah buku yang sangat banyak sering kali membuat pembaca kesulitan menentukan pilihan bacaan berikutnya. Beberapa pembaca lebih suka buku dengan reputasi penjualan tinggi, sementara yang lain mencari buku serupa dengan yang pernah mereka baca. Ada juga pembaca yang memilih buku berdasarkan rating atau ulasan yang tersedia.

### Alasan Pembuatan Proyek dan Referensi Terkait Proyek :

- Pengembangan proyek sistem rekomendasi ini memiliki peran yang sangat penting. Tujuannya adalah memberikan solusi atas kesulitan pengguna dalam memilih buku yang belum pernah mereka baca. Oleh karena itu, dibutuhkan sebuah sistem yang dapat merekomendasikan buku-buku menarik yang sesuai dengan minat pengguna. Ketika pengguna merasa puas dengan fitur-fitur yang tersedia di dalam platform, mereka cenderung akan terus menggunakan dan berlangganan layanan yang disediakan [3].


### Referensi
- [1] [Moh. Irfan, D. A. C, and H. F. R, “SISTEM REKOMENDASI: BUKU ONLINE DENGAN METODE COLLABORATIVE FILTERING,” JURNAL TEKNOLOGI TECHNOSCIENTIA, vol. 7, no. 1, pp. 76–84, Aug. 2014.](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612) 
- [2] [S. Kasiyun, “UPAYA MENINGKATKAN MINAT BACA SEBAGAI SARANA UNTUK MENCERDASKAN BANGSA,” JURNAL PENA INDONESIA (JPI), vol. 1, no. 1, pp. 79–95, Mar. 2015.](https://journal.unesa.ac.id/index.php/jpi/article/view/140)
- [3] [G. Indah Marthasari, Y. Azhar, and D. Kurnia Puspitaningrum, “SISTEM REKOMENDASI PENYEWAAN PERLENGKAPAN PESTA MENGGUNAKAN COLLABORATIVE FILTERING DAN PENGGALIAN ATURAN ASOSIASI,” Jurnal SimanteC, vol. 5, no. 1, pp. 1–8, Dec. 2015.](https://eco-entrepreneur.trunojoyo.ac.id/simantec/article/view/1008)

## Business Understanding

### Problem Statements

Berdasarkan uraian yang telah dipaparkan pada latar belakang diatas, maka dapat diambil sebuah rumusan masalah yang dirumuskan sebagai berikut :

- bagaimana menerapkan metode item-based collaborative filtering sebagai pendekatan dari sistem rekomendasi ?
- bagaimana proses untuk menentukan rekomendasi buku dengan menggunakan metode item-based collaborative filtering ?
- Bagaimana evaluasi model machine learning dapat menentukan rekomendasi buku?

### Goals

Berdasarkan rumusan masalah yang telah dipaparkan di atas, maka proyek penelitian ini memiliki tujuan, yaitu:

- Membuat sistem untuk merekomendasikan buku kepada pengguna.
- Membuat sistem rekomendasi yang sesuai dengan preferensi pengguna dengan teknik Collaborative Filtering.
- Mengetahui hasil evaluasi model machine learning dalam menentukan rekomendasi buku.

### Solution Statements

Untuk menyelesaikan permasalahan di atas, kita akan menggunakan satu algoritma sistem rekomendasi sebagai solusi permasalahan, yakni :

- Collaborative filtering bergantung pada pendapat komunitas pengguna. Ia tidak memerlukan atribut untuk setiap itemnya seperti pada sistem berbasis konten. Kelebihan dari teknik ini yakni dapat membantu pengguna menemukan minat baru. Kekurangannya yakni tidak dapat menangani item baru/fresh. Jadi, jika item tidak terlihat selama pelatihan, sistem tidak dapat melakukan proses embedding untuk item tersebut dan tidak dapat mengkueri model dengan item ini.


## Data Understanding
Dataset yang digunakan dalam proyek machine learning ini adalah Book Recommendation Dataset, yang terdiri dari 271.360 data buku, 278.858 data pengguna, dan 1.149.780 data penilaian. Dataset ini bersifat open-source dan dipublikasikan oleh MÖBIUS melalui platform Kaggle. Dataset ini mencakup tiga kategori utama: buku (format CSV), penilaian/rating (format CSV), dan pengguna (format CSV).

**Tautan Dataset :** [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset)

Dataset yang pertama adalah **Users.csv** memiliki jumlah 278858 data dan 3 kolom, yakni :
1. `User-ID` : ID pengguna dari toko buku online. **Tipe data =** `Int64`
2. `Location`: lokasi pengguna. **Tipe data =** `Object`
3. `Age` : usia pengguna. **Tipe data =** `Float64`

Dataset yang kedua yakni 'Books' yang memiliki jumlah 278858 data dan memiliki 8 kolom, diantaranya :
1. `ISBN`: identifikasi dari masing-masing buku. **Tipe data =** `Object`
2. `Book-Title`: judul buku. **Tipe data =** `Object`
3. `Book-Author`: penulis buku. **Tipe data =** `Object` 
4. `Year-Of-Publication`: tahun dipublikasikannya buku. **Tipe data =** `Object`
5. `Publisher`: penerbit buku. **Tipe data =** `Object`
6. `Image-URL-S`: URL gambar cover buku dalam ukuran S(Small) **Tipe data =** `Object`
7. `Image-URL-M`: URL gambar cover buku dalam ukuran M(Medium) **Tipe data =** `Object`
8. `Image-URL-L`: URL gambar cover buku dalam ukuran L(Large) **Tipe data =** `Object`

Dataset yang ketiga yakni 'Ratings' yang memiliki jumlah 1149780 data dan memiliki 3 kolom, berikut penjelasan mengenai kolom-kolomnya :
Ratings.csv

1. `User-ID`: ID dari user yang memberikan rating terhadap buku. **Tipe data =** `Int64`
2. `Kolom 'ISBN`: identifikasi buku atau nomor buku yang diberi rating oleh user **Tipe data =** `Object`
3. `Book-Rating`: nilai Rating dari buku, skala yang ada dalam rating ini yakni dari 0-10. **Tipe data =** `Int64`

### Visualisasi Data dan analisis eksplorasi data (EDA)
Membuat barplot dengan judul "10 Tahun terbanyak publikasi" digunakan untuk melihat lonjakan terbanyak dalam publikasi buku.    

<img width="856" alt="Screenshot 2025-01-22 at 09 58 20" src="https://github.com/user-attachments/assets/7002e89e-896b-42e1-9ad8-0b34b135bdaf" />

Untuk menampilkan "Jumlah Rating Buku yang Diberikan Pengguna" menggunakan barplot dimana menampilkan Jumlah Buku dan Book_Rating. Berikut merupakan tampilan dari barplot 10 ID Pengguna terpopuler:
<img width="865" alt="Screenshot 2025-01-22 at 10 33 03" src="https://github.com/user-attachments/assets/323dbeb5-9db9-4a5d-b662-ac199b5a519f" />

Untuk menampilkan "10 penulis terpopuler" dengan menggunakan barplot dimana menampilkan count dan nama penulis. Berikut merupakan tampilan dari barplot 10 penulis terpopuler:
<img width="1008" alt="Screenshot 2025-01-22 at 10 34 45" src="https://github.com/user-attachments/assets/6a143616-f361-44c0-b041-66db5d2a44fa" />
  penulis dengan nama “James Patterson” menjadi peringkat pertama pada penulis terpopuler dan penulis peringkat kedelapan dan kesembilan memiliki jumlah yang sama.

Untuk menampilkan "10 Lokasi Penulis Terpopuler" menggunakan barplot dimana menampilkan count dan nama penulis. Berikut merupakan tampilan dari barplot 10 Lokasi Penulis Terpopuler:
<img width="1032" alt="Screenshot 2025-01-22 at 10 39 56" src="https://github.com/user-attachments/assets/7b282b95-a746-4aee-9477-ffe753e91bf5" />
  Lokasi "minneapolis, minnesota, usa" menjadi peringkat pertama pada lokasi penulis terpopuler serta peringkat dua dan peringkat ketiga adalah lokasi “porto, porto, portugal” dan “dumas, arkansas, usa”.

menggunakan barplot kembali untuk menampilkan "10 publisher teratas" dimana terdiri dari nama publisher dan count. Berikut ini merupakan tampilan dari barplot 10 publisher teratas:
<img width="999" alt="Screenshot 2025-01-22 at 10 44 52" src="https://github.com/user-attachments/assets/0d7dd246-72a5-4331-9f59-f60ae5976e35" />
  dapat disimpulkan bahwa publisher yang berada di peringkat atas yaitu “Ballantine Books” dengan jumlah yang lebih banyak dibandingkan dengan publisher yang lain. Namun bila dilihat kembali pada peringkat sembilan dan sepuluh memiliki jumlah yang sama.

membuat rata-rata rating dengan buku terbanyak dibaca dimana untuk menampilkannya menggunakan barplot. Saat menampilkannya terdapat data “Book_Title” dan “Book_Rating”. Berikut ini hasil dari tampilan rata-rata rating dengan buku terbanyak dibaca:
<img width="1075" alt="Screenshot 2025-01-22 at 10 47 00" src="https://github.com/user-attachments/assets/4d651948-913a-4330-84bd-470a5a37c406" />
  buku dengan judul “A Painted House” memiliki rating terbanyak dari pengguna dibandingkan buku yang lainnya.


## Data Preparation
Data preparation bertujuan untuk menyiapkan data sebelum masuk ke proses modeling. Selain itu, data preparation juga berguna untuk meningkatkan akurasi saat training data. Pada dataset ini, yang akan kita lakukan yaitu menggabungkan dataset dengan fungsi merge() dan key ISBN, menghapus missing value serta menurut dataset berdasarkan ISBN serta menghapus hasil duplikat.

Karena ketiga dataset yang digunakan merupakan dataset dalam jumlah yang banyak yaitu ada lebih dari 200.000, maka di pada proses ini hanya mengambil 12.000 data pertama dari setiap variabel di atas dalam pembuatan sistem rekomendasi ini.

Agar dapat memudahkan untuk proses kualifikasi, maka ketiga dataset tersebut digabungkan satu sama lain yaitu : 
1. Dataset `Books` dengan Dataset `Ratings`
    - Dengan menggabungkan dataset tersebut, akan dimasukkan kedalam dataset baru yang bernama **`data_train`**
        <img width="885" alt="Screenshot 2025-01-22 at 12 08 29" src="https://github.com/user-attachments/assets/1c88b00d-1280-41cb-b3d3-aed9230e3f55" />

      Dengan 3341 baris dan 7 kolom

2. Dataset `Ratings` dengan Dataset `Users`
    - Dengan menggabungkan dataset tersebut, akan dimasukkan kedalam dataset baru yang bernama **`data_using`**
        <img width="710" alt="Screenshot 2025-01-22 at 12 07 14" src="https://github.com/user-attachments/assets/034aaa23-ef9e-4263-8b30-40007fad604b" />
      Dengan 2439 baris dan 4 kolom

### Pengecekan Missing Values
Jumlah nilai null adalah 0 pada masing masing kolom, dari 5 dataset. Hal ini menandakan bahwa dataset yang diambil tidak memiliki missing value

### Pengecekan Duplikasi Data
Dilakukan persiapan penghapusan data duplikat, dengan membuat variable baru dengan nama `data_prep` yang berisi dataframe `data_train` yang diurutkan berdasarkan **ISBN** dan nama **data_prus** yang berisi dataframe `data_using` yang diurutkan berdasarkan **UserID**.
<img width="1046" alt="Screenshot 2025-01-22 at 11 00 21" src="https://github.com/user-attachments/assets/8ae37182-bc6e-42a0-a127-cc0e7d4be06d" />

  setelah dilakukan persiapan dilanjutkan dengan penghapusan data duplikat menggunakan fungsi drop_duplicates. Penghapusan data duplikat berguna bila data train dan data test ada yang sama maka akan dihasilkan jumlah rows berkurang ketika dilakukan penghapusan data duplikat.
### Konversi data series dan pembuatan dictionary
Melakukan proses pengkonversian data series dalam bentuk list dimana menggunakan fungsi  `tolist()` dari library numpy. Proses ini menampilkan output dari jumlah books_id, books_title dan books_author yang memiliki jumlah yang sama yaitu 2519. Tahap berikutnya, membuat dictionary yang gunanya untuk menentukan pasangan key-value dari data books_id, books_title dan books_author.

### Encode
pada proses ini digunakan untuk menyandikan (encode) fitur ke dalam indeks integer dimana fitur yang digunakan yaitu fitur `UserID` dan `ISBN`.

### Split Data
Tahap ini dilakukan pengacakan dataset agar distribusi yang dilakukan menjadi random. Kemudian, dilakukan pembagian data train dan validasi dengan komposisi 90:10 dimana perlu dipetakkan (mapping) terlebih dahulu pada data user dan book menjadi satu value. Proses ini dilakukan untuk menguji model terhadap data baru. Selanjutnya, membuat rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training.

## Modeling
Pada tahap ini menggunakan model collaborative filtering dimana menggunakan metode deep learning yang bertujuan menghasilkan rekomendasi buku.

1. Tahap awal yang dilakukan yaitu melakukan proses embedding terhadap data user dan book. Lalu dilanjutkan dengan operasi perkalian dot product antara embedding user dan book serta menambahkan bias untuk kedua data. Skor kecocokan di tetapkan dalam skala [0,1] dengan fungsi aktivasi sigmoid

2. Langkah selanjutnya dengan melakukan proses compile terhadap model yang terdiri dari loss function yang menggunakan Binary Crossentropy, optimizer yang menggunakan Adam (Adaptive Moment Estimation) dan untuk metrics evaluation yaitu root mean squared error (RMSE) kemudian dilanjutkan dengan proses training

3. Tahap akhir yaitu dengan mengambil sampel user secara acak dan definisikan variabel **book_not_visited** yang merupakan daftar book yang belum pernah dikunjungi oleh pengguna. Variabel book_not_visited diperoleh dengan menggunakan operator bitwise (~) pada variabel **book_visited_by_user**. Kemudian dalam memperoleh rekomendasi buku menggunakan fungsi model.predict() dari library Keras.
    <img width="704" alt="Screenshot 2025-01-24 at 02 08 23" src="https://github.com/user-attachments/assets/849df559-9ff1-445d-bae2-d238b1c9bb83" />

Gambar tersebut merupakan hasil rekomendasi dari model collaborative filtering dimana user dengan id 914.  10 Rekomendasi Buku Teratas yang salah satunya yaitu ‘Les Fourmis : Bernard Werber’.
## Evaluation
Menggunakan dua metrik evaluasi yang digunakan untuk mengukur kinerja model pada collaborative filtering, yang pertama menggunakan metrik Root Mean Squared Error (RMSE) dan metrik Accuracy, berikut penjelasannya :

1. **Root Mean Squared Error (RMSE)** merupakan besarnya tingkat kesalahan hasil prediksi, dimana metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih kecil dikatakan lebih akurat daripada metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih besar.
Rumus dari RMSE sebagai berikut:
![Rumus RMSE](https://github.com/user-attachments/assets/a823c4a4-376b-4414-b219-e465c751484d)

lalu visualisasi metrik tersebut menggunakan plot dari library
  <img width="575" alt="Screenshot 2025-01-22 at 11 43 13" src="https://github.com/user-attachments/assets/74f76139-1b5a-41bd-ab3a-35e1d07363b4" />
  Dari plot di atas dapat memperoleh nilai error akhir sebesar sekitar 0.39 dan error pada data validasi kurang dari 0.2. Nilai tersebut cukup bagus untuk sistem rekomendasi.

|Metrik|Nilai|
|:--------|:----:|
|root_mean_squared_error|0.1526|
|val_root_mean_squared_error| 0.2949|

  Pada Tabel tersebut diperoleh pada epoch 100/100 nilai root_mean_squared_error sebesar 0.1526 dan nilai val_root_mean_squared_error sebesar 0.2949

2. **Mean Squared Error (MSE)**. Teknik ini menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi.
Rumus dari MSE sebagai berikut :
  ![Rumus MSE](https://github.com/user-attachments/assets/236a0604-b06d-414a-b677-a08533da977f)
    <img width="486" alt="Screenshot 2025-01-24 at 02 06 58" src="https://github.com/user-attachments/assets/d47dfb9d-ad00-4d6c-8e33-8714f6d0077e" />


  Pada Gambar Tersebut, Hasil dari kode program di atas yakni : 
  - MSE dari pada data train = 2.111916844346724e-05
  - MSE dari pada data validation = 8.685258439506148e-05

### Kesimpulan
Berdasarkan dari hasil visualisasi metrik RMSE , MSE dari pada data train adalah 2.1176639194068425e-05 dan MSE dari pada data validation adalah 8.684515903366322e-05. berdasarkan hal tersebut, pembuatan model dengan pendekatan Collaborative Filtering ini dapat digunakan untuk merekomendasikan buku yang belum pernah dibaca atau mungkin disukai pengguna. Selain itu, kini pengguna dapat mempersingkat waktu pencarian buku dengan memanfaatkan hasil rekomendasi yang telah diberikan oleh model.


