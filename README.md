# Analisis Spasial Kandungan Zinc (Zn) Tanah Menggunakan Ordinary Kriging

## Deskripsi Proyek

Repository ini berisi analisis geostatistika untuk mengetahui pola distribusi spasial kandungan Zinc (Zn) pada tanah menggunakan metode **Ordinary Kriging**.

Analisis dilakukan berdasarkan data titik pengamatan tanah yang memiliki informasi koordinat lokasi dan nilai konsentrasi Zinc. Metode Ordinary Kriging digunakan untuk melakukan interpolasi spasial sehingga dapat memperkirakan nilai Zinc pada lokasi yang tidak dilakukan pengamatan secara langsung.

Tahapan analisis meliputi eksplorasi data, transformasi data, analisis variogram, pemodelan variogram, prediksi spasial, validasi model, analisis ketidakpastian, dan transformasi kembali ke skala asli.

Seluruh proses analisis dilakukan menggunakan Python melalui Google Colab.

---

# Tujuan Analisis

Tujuan dari analisis ini adalah:

1. Mengetahui karakteristik statistik distribusi kandungan Zinc pada tanah.
2. Menganalisis hubungan spasial antar lokasi pengamatan.
3. Menentukan model variogram terbaik untuk menggambarkan struktur spasial data.
4. Melakukan prediksi distribusi spasial kandungan Zinc menggunakan Ordinary Kriging.
5. Mengevaluasi performa model prediksi menggunakan cross validation.
6. Mengetahui tingkat ketidakpastian hasil prediksi berdasarkan Kriging Variance.

---

# Data yang Digunakan

Dataset yang digunakan berupa data pengamatan tanah dengan variabel:

- **Coordinate X** : koordinat lokasi pengamatan arah X
- **Coordinate Y** : koordinat lokasi pengamatan arah Y
- **Zinc** : konsentrasi Zinc pada tanah


Jumlah titik observasi:

**155 titik pengamatan**

---

# Metode Analisis

Metode utama yang digunakan:

## Ordinary Kriging

Ordinary Kriging merupakan metode interpolasi geostatistik yang memanfaatkan hubungan spasial antar titik pengamatan berdasarkan model variogram.

Alur analisis:

```
Data Spasial Zinc
        ↓
Eksplorasi Data (EDA)
        ↓
Transformasi Log Zinc
        ↓
Experimental Variogram
        ↓
Pemodelan Variogram
        ↓
Pemilihan Model Terbaik
        ↓
Ordinary Kriging Prediction
        ↓
Validasi Model
        ↓
Analisis Ketidakpastian
        ↓
Back Transformation Zinc
```

---

# Library Python yang Digunakan

Library yang digunakan dalam analisis:

| Library | Fungsi |
|---|---|
| pandas | Pengolahan dan pembacaan data |
| numpy | Perhitungan numerik |
| matplotlib | Visualisasi grafik |
| seaborn | Visualisasi statistik |
| scipy | Analisis statistik |
| scikit-gstat | Analisis variogram |
| pykrige | Pemodelan Ordinary Kriging |

---

# Tahapan Analisis

## 1. Import Data Spasial Zinc

Data dimasukkan melalui proses upload file Excel.

File input:

```
soil.xlsx
```

Data kemudian dibaca dan digunakan sebagai dasar analisis spasial.

---

# 2. Pemilihan Variabel Analisis

Variabel yang digunakan:

- koordinat X
- koordinat Y
- konsentrasi Zinc


Variabel Zinc digunakan sebagai parameter utama dalam analisis geostatistik.

---

# 3. Exploratory Data Analysis (EDA)

Tahap eksplorasi dilakukan untuk mengetahui:

- jumlah data pengamatan
- distribusi nilai Zinc
- statistik deskriptif
- pola penyebaran data
- keberadaan nilai ekstrem


Hasil statistik Zinc:

- Jumlah data: 155 titik
- Mean: 469.716
- Minimum: 113
- Maksimum: 1839

Data menunjukkan adanya variasi nilai Zinc antar lokasi pengamatan.

---

# 4. Transformasi Log Zinc

Berdasarkan hasil eksplorasi, distribusi Zinc menunjukkan pola menceng ke kanan (*right-skewed*).

Untuk menstabilkan varians dilakukan transformasi:

\[
Z' = ln(Z)
\]


Transformasi bertujuan untuk:

- mengurangi pengaruh nilai ekstrem
- memperbaiki distribusi data
- meningkatkan kestabilan model variogram

---

# 5. Analisis Variogram Empiris

Variogram digunakan untuk mengetahui tingkat ketergantungan spasial antar lokasi pengamatan.

Konsep dasar:

- lokasi yang dekat memiliki nilai Zinc yang lebih mirip
- semakin jauh jarak antar lokasi maka perbedaan nilai semakin meningkat


Experimental variogram digunakan sebagai dasar pemodelan variogram teoritis.

---

# 6. Pemodelan Variogram

Beberapa model variogram dibandingkan:

1. Exponential
2. Spherical
3. Gaussian


Pemilihan model dilakukan berdasarkan nilai SSE (*Sum Squared Error*) terkecil.


Model variogram terbaik:

## Spherical Model


Parameter model:

| Parameter | Nilai |
|---|---:|
| Nugget | 0.0368 |
| Sill | 0.5285 |
| Range | 744.09 |

Model spherical dipilih karena memiliki kemampuan terbaik dalam menggambarkan struktur spasial data Zinc.

---

# 7. Prediksi Spasial Menggunakan Ordinary Kriging

Model variogram terbaik digunakan untuk melakukan interpolasi spasial.

Output yang dihasilkan:

- Peta prediksi spasial Zinc
- Distribusi kandungan Zinc pada wilayah penelitian


Hasil prediksi menunjukkan variasi spasial kandungan Zinc berdasarkan hubungan antar titik pengamatan.

---

# 8. Validasi Model

Evaluasi model dilakukan menggunakan metode cross validation.

Parameter evaluasi:

| Parameter | Nilai |
|---|---:|
| RMSE | 0.391 |
| MAE | 0.2919 |
| R² | 0.7047 |


Hasil menunjukkan bahwa model Ordinary Kriging mampu menjelaskan sekitar 70% variasi spasial kandungan Zinc.

---

# 9. Analisis Ketidakpastian

Analisis ketidakpastian dilakukan menggunakan:

## Kriging Variance


Interpretasi:

- Variance kecil → hasil prediksi lebih terpercaya
- Variance besar → tingkat ketidakpastian lebih tinggi


Ketidakpastian meningkat pada area yang jauh dari titik pengamatan karena informasi spasial yang tersedia lebih sedikit.

---

# 10. Back Transformation Log Zinc

Karena analisis menggunakan transformasi logaritma, hasil prediksi dikembalikan ke skala asli menggunakan:

 $$\[
Z = e^{Z'}
\]$$


Tahapan ini dilakukan agar nilai prediksi Zinc dapat diinterpretasikan dalam satuan asli.

---

# Struktur File

```
.
├── kriging_analysis.ipynb
├── soil.xlsx
└── README.md
```

---

# Cara Menjalankan Program

## Menggunakan Google Colab

1. Buka file:

```
kriging_analysis.ipynb
```

2. Upload dataset:

```
soil.xlsx
```

3. Jalankan setiap cell secara berurutan.

---

# Hasil Akhir Analisis

Analisis menghasilkan:

- Statistik distribusi Zinc
- Visualisasi distribusi data
- Transformasi Log Zinc
- Experimental variogram
- Perbandingan model variogram
- Model variogram terbaik
- Peta prediksi Ordinary Kriging
- Hasil validasi model
- Peta Kriging Variance
- Prediksi Zinc pada skala asli


---

# Kesimpulan

Berdasarkan analisis spasial menggunakan Ordinary Kriging, distribusi kandungan Zinc tanah menunjukkan adanya hubungan spasial antar lokasi pengamatan.

Model variogram **Spherical** merupakan model terbaik berdasarkan nilai SSE terkecil dan digunakan dalam proses interpolasi.

Hasil validasi menunjukkan performa model yang baik dengan nilai R² sebesar 0.7047.

Peta prediksi dan analisis ketidakpastian memberikan informasi mengenai pola penyebaran Zinc serta tingkat kepercayaan hasil estimasi pada wilayah penelitian.

---

# Author

Nama:
Salma Soleha H062252013
Salwa Soleha H062252013

Project:
Analisis Spasial Kandungan Zinc Tanah Menggunakan Ordinary Kriging
