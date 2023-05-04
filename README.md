# Laporan Proyek Machine Learning - Arief Syahroni

## Domain Proyek

Sulit nya dalam menentukan seorang pasien mengalami kemungkinan diabetes berdasarkan riwayat medis nya dan beberapa faktor seperti usia, jenis kelamin, indeks massa tubuh (BMI), hipertensi, penyakit jantung, riwayat merokok, kadar HbA1c, dan kadar glukosa darah sehingga para tenaga medis sangat membutuhkan waktu yang cukup lama dan seringkali akurasi diagnose nya tidak sesuai harapan dan tidak sesuai.

## Business Understanding

### Problem Statements

- Bagaimana cara mempersingkat waktu diagnose seorang pasien yang mengalami diabetes ?
- Bagaimana agar memperoleh diagnose seorang pasien yang valid  ?

### Goals

- Untuk mempersingkat waktu seorang tenaga medis dalam mendiagnose seseorang yang mengalami diabetes.
- Agar seorang tenaga medis memperoleh ke akurat-an dalam mendiagnose seseorang yang mengalami diabetes.

## Data Understanding

Diabetes Prediction Dataset
kumpulan data medis dan demografis dari pasien, beserta status diabetesnya (positif atau negatif). Data tersebut mencakup fitur seperti usia, jenis kelamin, indeks massa tubuh (BMI), hipertensi, penyakit jantung, riwayat merokok, kadar HbA1c, dan kadar glukosa darah.

[Diabetes Prediction Dataset](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut :
- gender :
Jenis kelamin mengacu pada jenis kelamin biologis individu, yang dapat berdampak pada kerentanan mereka terhadap diabetes. Ada tiga kategori di dalamnya pria, wanita dan lainnya.

- age :
Usia merupakan faktor penting karena diabetes lebih sering didiagnosis pada orang dewasa yang lebih tua. Usia berkisar antara 0-80 dalam dataset kami.

- hypertension :
Hipertensi adalah kondisi medis di mana tekanan darah di arteri terus-menerus meningkat. Ini memiliki nilai 0 atau 1 dimana 0 menunjukkan mereka tidak memiliki hipertensi dan untuk 1 itu berarti mereka memiliki hipertensi.

- heart_desease :
Penyakit jantung adalah kondisi medis lain yang dikaitkan dengan peningkatan risiko diabetes. Ini memiliki nilai 0 atau 1 dimana 0 menunjukkan mereka tidak memiliki penyakit jantung dan untuk 1 itu berarti mereka memiliki penyakit jantung.

- smoking_history :
Riwayat merokok juga dianggap sebagai faktor risiko diabetes dan dapat memperburuk komplikasi yang terkait dengan diabetes. Dalam kumpulan data kami, kami memiliki 5 kategori yaitu tidak terkini, mantan, Tanpa Info, terkini, tidak pernah, dan selamanya.

- bmi :
BMI (Body Mass Index) adalah ukuran lemak tubuh berdasarkan berat dan tinggi badan. Nilai BMI yang lebih tinggi terkait dengan risiko diabetes yang lebih tinggi. Kisaran BMI dalam dataset adalah dari 10,16 hingga 71,55. BMI kurang dari 18,5 adalah kurus, 18,5-24,9 adalah normal, 25-29,9 adalah kelebihan berat badan, dan 30 atau lebih adalah obesitas.

- HbA1c_level :
Kadar HbA1c (Hemoglobin A1c) adalah ukuran kadar gula darah rata-rata seseorang selama 2-3 bulan terakhir. Tingkat yang lebih tinggi menunjukkan risiko lebih besar terkena diabetes. Sebagian besar lebih dari 6,5% dari Tingkat HbA1c menunjukkan diabetes.: 

- blood_glucose_level :
Tingkat glukosa darah mengacu pada jumlah glukosa dalam aliran darah pada waktu tertentu. Kadar glukosa darah yang tinggi merupakan indikator utama diabetes.

- diabetes :
Diabetes adalah variabel target yang diprediksi, dengan nilai 1 menunjukkan adanya diabetes dan 0 menunjukkan tidak adanya diabetes.

## Data Preparation
- Menggunakan metode .info() untuk mendapatkan informasi missing value & missing type pada dataframe.
  Perlu dilakukan agar tidak ada perbedaan jumlah data pada masing-masing field/fitur dan tidak ada missing type

- Menggunakan metode .isna().sum() & .isnull().sum()  untuk mendapatkan/menghitung jumlah data duplikat
  Mencari dan meastikan agar tidak ada duplikasi data yang bisa mengganggu proses modeling dan prediksi

- Menggunakan metode .drop_duplicates(inplace=True) untuk enghapus duplikasi data
  menindaklanjuti proses menghitung data duplikat untuk mengganti nya dengan nilai yang lain agar tidak duplikasi

- Menggunakan metode .duplicated().sum() untuk melihat & memastikan tidak ada lagi data duplicate
  Menindaklanjuti proses penggantian nilai yang duplikasi untuk memastikan apakah masih ada data yang duplikasi

- Menggunakan metode .describe() untuk melihat statistik pada dataframe
  Memastikan data tidak ada nilai NaN agar tidak mengganggu proses modeling dan prediksi

- Menggunakan metode .value_counts() untuk menghitung jumlah data berdasarkan 'gender'
  untuk melihat jumlah data berdasarkan masing-masing gender

- Menggunakan metode preprocessing.LabelEncoder().fit_transform() untuk mengganti value 'gender' menjadi data kuantitatif/numeric
  proses ini agar prediksi data lebih akurat karena tidak ada data kategorikal

- Menggunakan metode .value_counts() untuk menghitung jumlah data berdasarkan 'smoking_history'
  untuk melihat jumlah data berdasarkan history merokok

- Menggunakan metode .map() untuk mengganti value  'smoking_history' menjadi data kuantitatif/numeric
  proses ini agar prediksi data lebih akurat karena tidak ada data kategorikal

- Menggunakan metode .describe() untuk melihat statistik pada dataframe
  Memastikan data tidak ada nilai NaN agar tidak mengganggu proses modeling dan prediksi

- Menggunakan metode .mod(1) == 0 untuk membulatkan nilai 'age', agar tidak ada umur dengan nilai decimal
  proses ini agar memudahkan dalam kalkulasi untuk memastikan age tidak ada nilai decimal

- Menggunakan metode .astype(int) untuk merubah tipe data 'age' menjadi integer
  proses ini agar nilai age tidak ada decimal dan bulat menjadi bilangan integer

- Menggunakan metode .info() untuk mendapatkan informasi missing value & missing type pada dataframe.
  Perlu dilakukan untuk lebih memastikan agar tidak ada perbedaan jumlah data pada masing-masing field/fitur dan tidak ada missing type

- Menggunakan metode train_test_split() untuk membagi dataset kedalam data training dan data testing
  proses ini menggunakan train_size=0.8 dan random_state=42 agar memepercepat waktu train

- menggunakan metode preprocessing.StandardScaler().fit_transform() untuk melakukan normalisasi
  proses ini agar ormalisasi data agar data yang digunakan tidak memiliki penyimpangan yang besar.

## Modeling
Pada proses ini menggunakan model mechine learning
- Logistic Regrssion
  adalah model statistik yang memodelkan probabilitas suatu peristiwa yang terjadi dengan memiliki log-peluang untuk peristiwa tersebut menjadi kombinasi linier dari satu atau lebih variabel independen.

- KNClassifier
  adalah metode pembelajaran terawasi non-parametrik yang digunakan untuk klasifikasi dan regresi. Dalam kedua kasus, input terdiri dari k contoh pelatihan terdekat dalam kumpulan data.

  Pada model ini menggunakan :
  - n_neighbors = 5

- Decision Tree Classifier
  adalah pendekatan pembelajaran terawasi yang digunakan dalam statistik, penambangan data, dan pembelajaran mesin. Dalam formalisme ini, pohon keputusan klasifikasi atau regresi digunakan sebagai model prediksi untuk menarik kesimpulan tentang serangkaian pengamatan.

- Random Forest
  adalah metode pembelajaran ansambel untuk klasifikasi, regresi, dan tugas lain yang beroperasi dengan membangun banyak pohon keputusan pada waktu pelatihan. Untuk tugas klasifikasi, hasil hutan acak adalah kelas yang dipilih oleh sebagian besar pohon.

  Pada model ini menggunakan :
  - n_estimators = 10
  - criterion = 'entropy'
  - random_state = 0

Tahapan Modeling :

- Trainng Model dengan Logistic Regrssion
- Trainng Model dengan KNClassifier
- Trainng Model dengan Decision Tree Classifier
- Trainng Model dengan Random Forest

## Evaluation

Matrik yang digunakan adalah : accuracy_score()

Dari beberapa percobaan model dengan menggunakan confusion matrix, nilai akurasi yang paling bagus ada di Random Forest
berikut hasil matrix acuracy dari masing-masing model yang digunakan

| Model | Accracy |
| ----------- | :---------: |
| Logistic Regrssion| 0.95867 |
| KNClassifier| 0.95947 |
| Decision Tree Classifier | 0.95012 |
| Random Forest | 0.96759 |