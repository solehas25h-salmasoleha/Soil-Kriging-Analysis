# Analisis Spasial Kandungan Zinc Tanah Menggunakan Ordinary Kriging
Pemodelan Variogram dan Prediksi Spasial Kandungan Zinc (Zn)
Pendahuluan
Analisis data spasial merupakan pendekatan statistik yang digunakan untuk memahami hubungan antar lokasi berdasarkan karakteristik variabel yang diamati.

Pada penelitian ini dilakukan analisis geostatistika terhadap distribusi kandungan Zinc (Zn) tanah menggunakan metode Ordinary Kriging.Tahapan analisis meliputi eksplorasi data, transformasi data, pemodelan variogram, prediksi spasial, validasi model, serta analisis ketidakpastian hasil prediksi.

# Data Spasial Zinc
Data yang digunakan terdiri atas informasi koordinat lokasi pengamatan dan nilai konsentrasi Zinc pada setiap titik observasi. Koordinat spasial digunakan untuk menggambarkan posisi geografis setiap sampel, sedangkan nilai Zinc digunakan sebagai variabel atribut yang akan dianalisis pola penyebaran spasialnya.

# 1. Exploratory Data Analysis (EDA)
Tahap Exploratory Data Analysis (EDA) dilakukan untuk memahami karakteristik awal distribusi data kandungan Zinc sebelum dilakukan analisis geostatistika lebih lanjut. Analisis eksplorasi meliputi pemeriksaan distribusi data menggunakan histogram dan identifikasi keberadaan nilai pencilan (outlier) menggunakan boxplot.Informasi yang diperoleh pada tahap ini digunakan sebagai dasar dalam menentukan perlakuan data selanjutnya, termasuk kebutuhan transformasi data sebelum proses pemodelan variogram dan Ordinary Kriging.
<img width="1389" height="490" alt="image" src="https://github.com/user-attachments/assets/2090c011-903a-474e-98dd-4b93618bb3ed" />

Berdasarkan hasil eksplorasi data menggunakan histogram dan boxplot, distribusi konsentrasi Zinc menunjukkan pola kemencengan positif (right-skewed). Sebagian besar nilai pengamatan berada pada rentang konsentrasi yang lebih rendah, namun terdapat beberapa nilai ekstrem dengan konsentrasi Zinc yang relatif tinggi.

Keberadaan nilai pencilan menunjukkan bahwa data memiliki variasi yang cukup besar sehingga dapat memengaruhi kestabilan varians dalam analisis geostatistika. Oleh karena itu, diperlukan transformasi data sebelum dilakukan pemodelan variogram dan proses prediksi menggunakan metode Ordinary Kriging.
