# Laporan Proyek Machine Learning - Arief Syahroni

## Domain Proyek

Sulit nya dalam menentukan seorang pasien mengalami kemungkinan diabetes dari beberapa faktor berdasarkan riwayat medis nya dan membutuhkan waktu yang cukup lama.

## Business Understanding

Pada bagian ini, kamu perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Butuh waktu yang cukup lama untuk menentukan pasien mengalami diabetes.

### Goals

Untuk memprediksi kemungkinan diabetes pada pasien berdasarkan riwayat medis dan detail demografis mereka.

## Data Understanding

Diabetes Prediction Dataset
kumpulan data medis dan demografis dari pasien, beserta status diabetesnya (positif atau negatif). Data tersebut mencakup fitur seperti usia, jenis kelamin, indeks massa tubuh (BMI), hipertensi, penyakit jantung, riwayat merokok, kadar HbA1c, dan kadar glukosa darah.

[Diabetes Prediction Dataset](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
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
- Mencari missing value & missing type pada dataframe.
  Perlu dilakukan agra tidak ada perbedaan jumlah data pada masing-masing field/fitur

- Menghitung jumlah data duplicate
  Mencari dan meastikan agar tidak duplikasi data agar tidak mengganggu proses modeling dan prediksi

- Menghapus duplikasi data
  menindaklanjuti proses menghitung data duplikat agar data yang ada tidak duplikat lagi

- Melihat & Memastikan tidak ada lagi data duplicate
- Melihat statistik pada dataframe
  Memastikan data tidak ada nilai NaN agar tidak mengganggu proses modeling dan prediksi

- Menghitung jumlah data berdasarkan 'gender'
  untuk melihat jumlah data berdasarkan masing-masing gender

- Melakukan one hot encode untuk mengganti value 'gender' menjadi data kuantitatif/numeric
  agar prediksi data lebih akurat karena tidak ada data kategorikal

- Menghitung jumlah data berdasarkan 'smoking_history'
  untuk melihat jumlah data berdasarkan history merokok 

- Melakukan one hot encode untuk mengganti value 'smoking_history' menjadi data kuantitatif/numeric
  agar prediksi data lebih akurat karena tidak ada data kategorikal

- Melihat statistik pada dataframe
  memastikan tidak ada data NaN

- Membulatkan nilai 'age', agar tidak ada umur dengan nilai decimal
  agar memudahkan dalam kalkulasi untuk memastikan age tidak ada nilai decimal

- Merubah tipe data 'age' menjadi integer
  agar nilai age tidak ada decimal dan bulat

- Melihat informasi missing value, field & data type pada dataframe

## Modeling
Pada proses ini menggunakan model mechine learning
- Logistic Regrssion
- KNClassifier
- Decision Tree Classifier
- Random Forest

Tahapan Modeling : 
- Membagi dataset kedalam data training dan data testing
- Melakukan feature Scaling
- membagi data menjadi tain & test dan mengalokasikan data training 0.8 (80%)
- Trainng Model dengan Logistic Regrssion 
- Trainng Model dengan KNClassifier 
- Trainng Model dengan Decision Tree Classifier
- Trainng Model dengan Random Forest

## Evaluation

Matrik yang digunakan adalah : Confusion Matrix
Dari beberapa percobaan model dengan menggunakan confusion matrix, nilai akurasi yang paling bagus ada di Random Forest

