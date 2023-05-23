# Laporan Proyek Machine Learning Sistem Rekomendasi - ARIEF SYAHRONI

## Project Overview

Pesatnya pergerakan bidang digital saat ini membuat minat orang untuk membaca sangat minim, dan jika ada seseorang ingin mempelajari sesuai mereka lebih memilih Youtube karena terdapat sistem rekomendasi didalamnya sehingga semua artikel/topik yang muncul sesuai dengan apa yang ingin mereka pelajari, dengan data ini saya ingin membuat sebuah sistem rekomendasi jika seseorang mencari materi bacaan seperti buku di suatu toko buku agar materi-materi yang muncul berkaitan dengan topik yang pembaca butuhkan atau sukai.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi yang di personalisasi dengan teknik content-based filtering?
- Dengan data rating yang dimiliki, bagaimana toko buku dapat merekomendasikan buku lain yang mungkin disukai dan belum pernah dibaca oleh pengguna.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Menghasilkan sejumlah rekomendasi buku yang dipersonalisasi untuk pengguna dengan teknik content-based filtering.
- Menghasilkan sejumlah rekomendasi buku yang sesuai dengan preferensi pengguna dan belum pernah di baca sebelumnya dengan teknik collaborative filtering.


### Solution statements
- Menggunakan TF-IDF-Vectorizer untuk membangun sistem rekomendasi sederhana berdasarkan penulis buku
- Mengguanakan cosine_similarity untuk menghitung derajat kesamaan antar buku

## Data Understanding

Project ini menggunakan dataset "Book Recommendation Dataset"

Book Recommendation Dataset
https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset



Buku diidentifikasi oleh ISBN masing-masing. ISBN yang tidak valid telah dihapus dari kumpulan data. Selain itu, beberapa informasi berbasis konten diberikan (Judul Buku, Penulis Buku, Tahun Penerbitan, Penerbit). Perhatikan bahwa dalam kasus beberapa penulis, hanya penulis pertama yang diberikan. Tautan URL ke gambar sampul juga diberikan, muncul dalam tiga rasa berbeda (Gambar-URL-S, Gambar-URL-M, Gambar-URL-L), yaitu, kecil, sedang, besar.

Dataset books
Jumlah Baris : 51132
Jumlah Kolom : 8

Variabel-variabel pada Dataset books :
- books : merupakan data buku
  * isbn : merupakan nomor pokok/unik dari buku
  * bookTitle : merupakan Judul buku
  * bookAuthor : merupakan Penulis buku
  * yearOfPublication : merupakan tahun dimana buku diterbitkan
  * publisher : merupakan penerbit buku tersebut
  * imageUrlS : merupakan ukuran S dari gambar buku
  * imageUrlM : merupakan ukuran M dari gambar buku
  * imageUrlL : merupakan ukuran L dari gambar buku

Dataset users
Jumlah Baris : 278858
Jumlah Kolom : 3

Variabel-variabel pada Dataset users :
- users : merupakan data user
  * userID : merupakan ID unik user
  * location : merupakan lokasi tinggal user 
  * age : merupakan umur user

Dataset ratings
Jumlah Baris : 701122
Jumlah Kolom : 3

Variabel-variabel pada Dataset ratings :
- ratings : merupakan data rating yang diberikan oleh user/pengguna
  * userID : merupakan ID unik user yang memberian penilaian
  * isbn : merupakan ID unik buku yang diberikan penilaian oleh user
  * bookRating : merupakan nilai yang diberikan oleh user terhadap buku tersebut


## Data Preparation
- Menggunakan metode .head() untuk menampilkan 5 data teratas
  dilakukan untuk menampilkan dan menganalisa sample data dari 5 data yang di tampilkan

- Menggunakan metode .shape untuk menampilkan berapa jumlah row/baris dan column/kolom
  dilakukan untuk mengetahui ada berapa jumlah baris di dataset tersebut dan dengan berapa atribut

- Menggunakan metode .info() untuk menampilkan statistik info tentang dataframe tersebut
  dilakukan untuk menganalisis apakah ada missing data dan missing value dari dataframe tersebut

- Menggunakan metode .rename(columns={}) untuk menrubah nama column/kolom
  dilakukan untuk rename/merubah nama kolom agar terhindar dari special karakter

- Menggunakan metode .isna().sum() untuk melihat data null
  dilakukan untuk melihat ada berapa data null di masing-masing row/baris dari dataset tersebut

- Menggunakan metode .dropna() untuk menghapus data null
  dilakuan untuk menghapus seluruh data yang terdapat data null di dataset tersebut

- Menggunakan metode .merge() untuk menggabungkan beberapa dataframe
  dilakukan untuk menggabungkan beberapa table/dataframe dengan metode join(left, right, inner dll) agar mendapatkan informasi lebih
  - parameter pertama dari metmetodehode .merge() digunakan untuk table/dataframe pertama yang akan di gabungkan
  - parameter kedua dari metode .merge() digunakan untuk table/dataframe kedua yang akan di gabungkan
  - parameter ketiga on='' digunakan untuk kata kunci/primary key dari tabel pertama dan foreign key dari table kedua
  - parameter ke-empat how='' digunakan untuk cara/metode join seperti left, right, inner dll.

- Menggunakan metode .groupby() untuk menggabungkan data
  dilakukan untuk menggabungkan data berdasarkan kolom tertentu

- Menggunakan metode .sort_values() untuk mengurutkan data
  dilakukan untuk mengurutkan data berdasarkan kolom tertentu dengan metode urut seperti ascending atau descending
  - parameter pertama dari metode .sort_vaoues() digunakan untuk column/kolom mana yang akan di sorting data nya
  - parameter kedua dari metode .sort_values() digunakan untuk metode urut jika ascending=True maka data ascending begitu sebaliknya

- Menggunakan metode .unique() untuk melihat berpa jumlah data unik
  dilakukan untuk melihat ada berapa jumlah data unik atau data yang tidak redundant/duplikat

- Menggunakan metode .drop_duplicates('') untuk menghapus nilai tertentu
  dilakukan untuk menghapus nilai dari column/kolom tertentu dari dataframe

- Menggunakan metode .tolist() untuk membuat data list
  dilakukan untuk membuat suatu data dalam deretan dat List

- Menggunakan metode .DataFrame() untuk membuat dataframe
  dilakukan untuk membuat sebuah dataframe dengan komposisi tertentu

- Menggunakan metode .sample(5) untuk menampilkan data sample
  dilakukan untuk menampilkan data tertentu/sample/contoh jumlah data dengan jumlah yang di inginkan

- Menggunakan metode .fit() pada TfidfVerctorizer untuk menghitung idf
  dilakukan untuk melakuan perhitungan idf pada dataframe tersebut

- Menggunakan metode .get_feature_names_out() untuk mapping array
  dilakukan untuk mapping array dari fitur index integer ke fitur nama

- Menggunakan metode .fit_transform() untuk mentransformasi data
  dilakukan untuk melakukan fit lalu ditransformasikan ke bentuk matrix

- Menggunakan metode .todense() untuk mengubah ke matrix
  dilakukan untuk mengubah vector tf-idf dalam bentuk matriks

- Menggunakan metode cosine_simliarity() untuk menghitung kesamaan
  dilakukan untuk menghitung derajat kesamaan ( similarity degree ) antar buku, dalam konteks ini data matrix pada variable tfidf_matrix

- Menggunakan metode unique().tolist() untuk membuat list unique
  dilakukan untuk membuat sebuah list data dalam hal ini usser_id dalam kumpulan data yang unik/tidak duplikasi

- Menggunakan metode enumerate() untuk encode data
  dilakukan untuk mengembalikan panjang iterable dan mengulang itemnya secara bersamaan untuk membuat data key value dalam hal ini data user_id yang sebelumnya unik

- menggunakan metode map() untuk mapping data
  dilakukan untuk mapping/memetakan data dalam hal ini nilai unik yang telah di encode menjadi nilai key value tadi di tampung dalam dataframe yang berkaitan datanya, seperti hasil encode userid di tampung ke dalam  dataframe user dan hasil encode isbn ditampung dalam dataframe buku

- menggunakan metode .values.astype(np.float32) untuk konversi tipedata
  dilakukan untuk mengkonversi data ratings yang sebelumnya integer (int) menjadi data decimal (float32)

- Menggunakan metode .format() untuk memetakan nilai
  dilakukan untuk mapping/memetakan nilai dari format print yg telah dibuat secara berurut

- Menggunakan metode int(0.8 * df.shape[0]) untuk membagi data menjadi data train & test
  dilakukan untuk membagi data menjadi 0.8 atau 80% data train & sisanya 0.2 atau 20% data test berdasarkan jumlah row data/df.shape[0] lalu disimpan dalam variable train_indices, kemudian dibagi kedalam variable x_train, x_test, y_train, y_test

- Menggunakan model.fit() untuk melatih model
    dilakukan untuk melatih sebuah model yang didalamnya terdapat nilai :
      x -> diambil dari data x_train
      y -> diambil dari data y_train
      batch_size = 8
      epochs = 10, karena data yang akan di training begitu besar, lalu
      validation_data -> diambil dari data x_val & y_val


## Modeling

- Pada Content-based Filtering menggunakan :

  Content Based Filtering memanfaatkan informasi beberapa item / data untuk direkomendasikan kepada pengguna sebagai referensi yang terkait dengan informasi yang digunakan sebelumnya. Tujuan dari content based recommendation agar dapat memprediksi persamaan dari sejumlah informasi yang didapat dari pengguna.

  - TF-IDF Vectorizer

    Fungsi tfidfvectorizer memiliki beberapa parameter, antara lain:

    - min_df
      Digunakan untuk menghilangkan term/istilah yang terlalu jarang muncul. Sebagai contoh, jika diset min_df = 0.01, artinya kita mengabaikan term yang muncul kurang dari 1% dalam teks. Jika diset min_df = 5, artinya kita mengabaikan term yang muncul dalam kurang dari 5 dokumen.

    - max_df
      Digunakan untuk menghilangkan term yang terlalu sering muncul, biasanya merupakan stop words yang telah kita bahas pada materi sebelumnya. Sebagai contoh, jika diset max_df=0.8, artinya kita mengabaikan term yang muncul lebih dari 80% dalam teks. Jika diset 25, artinya kita mengabaikan term yang muncul di lebih dari 25 dokumen.

    - sublinear_tf
      Berfungsi untuk melakukan scaling dan bernilai boolean dengan default false. Sublinear_tf=True akan mengubah vektor frekuensi menjadi bentuk logaritmik (1+log(tf)). Sehingga dapat menormalisasi bias terhadap teks yang panjang dan teks yang pendek.

    - use_idf
      Bernilai boolean dengan default True. Parameter ini memungkinkan kita untuk menggunakan Inverse Document Frequency (IDF). Hal ini berarti term yang terlalu sering muncul dalam teks akan diberi skor lebih sedikit dibanding term yang jarang muncul (hanya muncul pada teks yang spesifik saja).


  - Cosine Similarity

    Cosine similarity mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama. Ia menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai cosine similarity.

    Jika ingin merekomendasikan item yang mungkin disukai oleh pengguna, tentu kita perlu mencari informasi mengenai item yang memang disukai oleh pengguna. Dengan informasi ini, kita bisa menentukan item yang sama atau mirip (similar) untuk direkomendasikan kepada pengguna.

    Pengukuran tingkat kesamaan erat kaitannya dengan perhitungan jarak antar item. Secara umum hubungan antara kesamaan dan jarak adalah sebagai berikut:

    - Semakin besar jarak, kesamaan semakin kecil (menuju nol).
    - Semakin kecil jarak, kesamaan semakin besar (menuju satu).

  - Menampilkan Top-N (5) Rekomendasi pada Content-Based Filtering
    -	The Debacle (The Penguin Classics)	Emile Zola
    -	VÃ?Â©ritÃ?Â©	Emile Zola
    -	The Earth (Penguin Classics)	Emile Zola
    -	L' Assommoir	Emile Zola
    -	Collected Works of Emile Zola	Emile Zola
  
- Pada Collaborative Filtering menggunakan : 
  
  Collaborative Filtering memanfaatkan transaksi suatu produk / item yang didasarkan kepada perilaku / kebiasaan si pengguna. Tujuannya agar pengguna yang sama dan item yang serupa dapat disukai oleh pengguna sebagai rekomendasi pilihan. Collaborative Filtering umumnya terbagi atas 2 metode :

  - User-Based Collaborative Filtering
    merekomendasikan item suatu produk dengan menemukan pengguna yang mirip dengan pengguna yang lainnya. Contoh, kita ingin merekomendasikan film kepada teman kita. Kita bisa berasumsi bahwa orang yang sama akan memiliki selera yang sama. Misalkan saya dan si B telah menonton film yang sama, dan kami menilai semuanya hampir identik. Tapi si B belum melihat film ‘Harry Potter : Bagian II’ dan saya tahu. Jika saya suka film itu, itu masuk akal untuk berpikir bahwa dia juga.

    User-Based Collaborative Filtering mempunyai 2 metode perhitungan, yaitu Cosine similarity dan Pearson Correlation.

    Pearson Correlation tidak berubah untuk menambahkan konstanta pada semua elemen. Pada pembuatannya, algoritma yang umum digunakan K-Nearest Neighbor (KNN). Dan algoritma KNN bisa dilihat di Scikit-learn.

  - Item-Based Collaborative Filtering
    merekomendasikan kesamaan antara item yang menargetkan / berinteraksi dengan pengguna dan item lainnya. Contoh, seorang pengguna menyukai tim sepak bola “Bayern Munich”. Sistem secara otomatis akan merekomendasikan suatu item yang berhubungan dengan “Bayern Munich”, seperti jersey, bola, poster, dan lain sebagainya yang berhubungan.

    Pada Item-Based Collaborative Filtering menggunakan Matrix Factorization (MF)

    Matrix Factorization (MF) dengan mendekomposisi interaksi matriks item - pengguna menjadi produk dari dua matriks dua dimensi yang lebih rendah. Satu matriks dapat dilihat sebagai matriks pengguna di mana baris mewakili pengguna dan kolom adalah latent factor. Matriks lain adalah matriks item di mana baris merupakan latent factor dan kolom mewakili item.

  Menampilkan Top-N (5) Buku high rating pada Collaborative Filtering
  pada user 16966 sebagai berikut : 
  - Bachelor Brothers' Bed &amp; Breakfast : Bill Richardson
  - Expendable : James Alan Gardner
  - Elf Defense : Esther Friesner
  - Tea with the Black Dragon : R. A. MacAvoy
  - Summon the Keeper : Tanya Huff

  Menampilkan Top-N (10) Rekomendasi pada Collaborative Filtering
  pada user 16966 sebagai berikut  :
  - Complete Chronicles of Narnia : C. S. Lewis
  - The Baby Book: Everything You Need to Know About Your Baby from Birth to Age Two : Martha Sears
  - Nine Princes In Amber : Roger Zelazny
  - A Little Princess : Frances Hodgson Burnett
  - Marching Through Culpeper : A Novel of Culpeper, Virginia, Crossroads of the Civil War : Virginia Beard Morton
  - There's Treasure Everywhere--A Calvin and Hobbes Collection : Bill Watterson
  - Homicidal Psycho Jungle Cat: A Calvin and Hobbes Collection : Bill Watterson
  - Love You Forever : Robert N. Munsch
  - Julia's Last Hope (Oke, Janette, Women of the West.) : Janette Oke
  - Neverwhere : Neil Gaiman

## Evaluation

Pada Project kali ini menggunakan Metrik :

- Pada Content-Based Filtering menggunakan matrik Precision sebagai Evaluasi
  dengan output dari 5 item yang direkomendasikan itu ada 5 item yang relvan artiannya 100% untuk Precision

  precision adalah jumlah item rekomendasi yang relevan. Kita tidak bisa menghitung dengan memanggil library scikit learn karena tidak ada data target/label seperti pada supervised learning.

  berikut formulanya : 

  Precision = #of recommendation that are relevant/#of item we recommend.
  Precision = 5/5
  Precision = 100%

  berikut  Top-N (5) Rekomendasi pada Content-Based Filtering:

  -	The Debacle (The Penguin Classics)	Emile Zola
  -	VÃ?Â©ritÃ?Â©	Emile Zola
  -	The Earth (Penguin Classics)	Emile Zola
  -	L' Assommoir	Emile Zola
  -	Collected Works of Emile Zola	Emile Zola


- Pada Collaborative Filtering menggunakan matrik RMSE ( Root Mean Squared Error )

  Metrik evaluasi adalah ukuran yang digunakan untuk mengukur kinerja suatu model atau sistem.  

  Root Mean Square Error (RMSE) adalah  metode pengukuran dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. Root Mean Square Error adalah hasil dari akar kuadrat Mean Square Error. Keakuratan metode estimasi kesalahan pengukuran ditandai dengan adanya nilai RMSE yang kecil. Metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih kecil dikatakan lebih akurat daripada metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih besar.

  Cara Menghitung Root Mean Square Error (RMSE) adalah dengan mengurangi nilai aktual dengan nilai peramalan kemudian dikuadratkan dan dijumlahkan keseluruhan hasilnya kemudian dibagi dengan banyaknya data. Hasil perhitungan tersebut selanjutnya dihitung kembali untuk mencari nilai dari akar kuadrat.


  dengan menggunakan :

  - Binary Crosentropy untuk menghitung loss function
  - Adam adaptive sebagai optimizer dengan learning rate = 0.001
  - lalu menggunakan RMSE sebagai metric itu sendiri

- Pada proses Rekomendasi, saat menggunakan : 

  - Operator Bitwise (~) pada variable book_not_read
  - Metode model.predict() untuk mendapatkan rekomendasi

  Top-N (5) Buku high rating pada Collaborative Filtering
  pada user 16966 sebagai berikut : 
  - Bachelor Brothers' Bed &amp; Breakfast : Bill Richardson
  - Expendable : James Alan Gardner
  - Elf Defense : Esther Friesner
  - Tea with the Black Dragon : R. A. MacAvoy
  - Summon the Keeper : Tanya Huff

  Top-N (10) Rekomendasi pada Collaborative Filtering
  pada user 16966 sebagai berikut  :
  - Complete Chronicles of Narnia : C. S. Lewis
  - The Baby Book: Everything You Need to Know About Your Baby from Birth to Age Two : Martha Sears
  - Nine Princes In Amber : Roger Zelazny
  - A Little Princess : Frances Hodgson Burnett
  - Marching Through Culpeper : A Novel of Culpeper, Virginia, Crossroads of the Civil War : Virginia Beard Morton
  - There's Treasure Everywhere--A Calvin and Hobbes Collection : Bill Watterson
  - Homicidal Psycho Jungle Cat: A Calvin and Hobbes Collection : Bill Watterson
  - Love You Forever : Robert N. Munsch
  - Julia's Last Hope (Oke, Janette, Women of the West.) : Janette Oke
  - Neverwhere : Neil Gaiman


  ![Visualisasi Training](https://github.com/Syahro/dataset/blob/main/download.png)
  


- Kesimpulan : 
  dari 15 epoch yang dilakukan terlihat loss & root_mean_squared_error (RMSE) semakin mengecil dan sesuai descripsi Root Mean Square Error ( RMSE ) bahwa Metode estimasi yang mempunyai oot Mean Square Error (RMSE) lebih kecil dikatakan lebih akurat daripada metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih besar.
