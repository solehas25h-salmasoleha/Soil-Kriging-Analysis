# Analisis Spasial Kandungan Zinc Tanah Menggunakan Ordinary Kriging

Pemodelan variogram dan prediksi spasial kandungan Zinc (Zn) pada tanah menggunakan metode **Ordinary Kriging** dengan Python.

## Deskripsi Proyek

Proyek ini menganalisis sebaran spasial konsentrasi Zinc (Zn) tanah berdasarkan titik-titik observasi. Hasil akhirnya berupa peta prediksi kandungan Zinc pada lokasi yang tidak diamati, lengkap dengan peta ketidakpastian (kriging variance).

Tahapan analisis:

1. Persiapan library
2. Import data spasial
3. Pemilihan variabel (koordinat X, Y, dan Zinc)
4. Exploratory Data Analysis (histogram dan boxplot)
5. Transformasi logaritma natural untuk mengatasi data yang menceng ke kanan (right-skewed)
6. Visualisasi sebaran spasial
7. Variogram empiris
8. Pemodelan variogram teoritis (Spherical, Exponential, Gaussian)
9. Ordinary Kriging pada grid 100×100
10. Validasi model (cross validation) dan analisis residual
11. Analisis ketidakpastian (kriging variance)

## Data

Data berupa file Excel (`.xlsx`) dengan kolom:

| Kolom  | Keterangan                          |
|--------|-------------------------------------|
| `x`    | Koordinat X lokasi pengamatan       |
| `y`    | Koordinat Y lokasi pengamatan       |
| `zinc` | Konsentrasi Zinc (Zn) pada lokasi   |

> **Sumber data:** *(isi dengan sumber dataset Anda, misalnya nama dataset, instansi, atau tautan)*

## Hasil Utama

**Pemilihan model variogram** (berdasarkan SSE terkecil):

| Model       | SSE      |
|-------------|----------|
| Spherical   | 0,066443 |
| Gaussian    | 0,067576 |
| Exponential | 0,085624 |

Model **Spherical** dipilih sebagai model terbaik. Range model sekitar **744 unit**, artinya lokasi dengan jarak kurang dari itu masih memiliki hubungan spasial.

**Validasi (cross validation) pada Log(Zinc):**

| Metrik | Nilai  |
|--------|--------|
| RMSE   | 0,391  |
| MAE    | 0,2919 |
| R²     | 0,7047 |

Model mampu menjelaskan sekitar 70,47% variasi Log(Zinc). Residual menyebar di sekitar nol, sehingga tidak terlihat kecenderungan over/under-estimasi yang sistematis

## Cara Menjalankan

### Opsi 1: Google Colab

1. Buka `kriging_analysis.ipynb` di Google Colab.
2. Jalankan sel instalasi library.
3. Saat diminta, unggah file data Excel.
4. Jalankan seluruh sel secara berurutan.

> Catatan: notebook menggunakan `google.colab.files.upload()` untuk memuat data. 

## Library yang Digunakan

- `numpy`, `pandas`
- `matplotlib`, `seaborn`
- `scipy`, `scikit-learn`
- `pykrige`
- `scikit-gstat`
- `openpyxl` (untuk membaca file Excel)

## Struktur Repositori

```
├── data   # Notebook analisis utama
├── README.md         # Dataset 
└── Kriging_analysis.ipynb
```

## Penulis

**Salwa Soleha**
*(Universitas Hasanuddin / Magister Statistika)*

## Lisensi

*(Contoh: MIT License. Hapus bagian ini jika tidak diperlukan.)*
