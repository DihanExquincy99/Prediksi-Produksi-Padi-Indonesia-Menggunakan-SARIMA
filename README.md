# Prediksi Produksi Padi Indonesia Menggunakan SARIMA
Implementasi metode SARIMA (Seasonal Autoregressive Integrated Moving Average) untuk menganalisis pola musiman dan memprediksi produksi padi Indonesia tahun 2026 berdasarkan data produksi bulanan periode 2018–2025 dengan tingkat akurasi peramalan sebesar MAPE 8,35%.

# Abstrak

Penelitian ini bertujuan untuk melakukan peramalan produksi padi Indonesia menggunakan metode Seasonal Autoregressive Integrated Moving Average (SARIMA) berdasarkan data bulanan periode 2018–2025. Tahapan analisis meliputi statistik deskriptif, visualisasi pola data, identifikasi pola musiman, uji stasioneritas menggunakan Box-Cox Transformation dan Augmented Dickey-Fuller Test, differencing non-musiman dan musiman, identifikasi parameter melalui plot ACF dan PACF, estimasi kandidat model, evaluasi diagnostik residual, serta peramalan produksi padi tahun 2026. Hasil analisis menunjukkan bahwa data produksi padi Indonesia memiliki pola musiman tahunan dengan periode musiman 12 bulan. Model terbaik yang diperoleh adalah **SARIMA(1,1,2)(0,1,1)₁₂** dengan nilai MAPE validasi sebesar **8,35%**, p-value Ljung-Box sebesar **0,685**, dan p-value Kolmogorov-Smirnov sebesar **0,1162**. Hasil peramalan tahun 2026 menunjukkan bahwa produksi padi diperkirakan mencapai puncak pada bulan Maret sebesar **8,6611 juta ton** dan April sebesar **8,4392 juta ton**, kemudian menurun hingga Desember sebesar **2,0669 juta ton**. Dengan demikian, model SARIMA mampu menangkap pola musiman produksi padi Indonesia dengan baik dan dapat digunakan sebagai alat bantu dalam perencanaan produksi pertanian serta kebijakan ketahanan pangan.

---

## Deskripsi Project

Project ini dibuat untuk menganalisis dan memprediksi produksi padi Indonesia berbasis data time series bulanan. Metode SARIMA digunakan karena data produksi padi memiliki pola musiman yang berulang setiap tahun, terutama akibat siklus tanam dan panen.

Analisis dilakukan dengan membandingkan beberapa kandidat model SARIMA, kemudian memilih model terbaik berdasarkan uji diagnostik residual dan nilai kesalahan prediksi terkecil.

---

## Dataset

Dataset yang digunakan adalah data produksi padi Indonesia bulanan periode **2018–2025** dengan satuan **juta ton**.

| Komponen | Keterangan |
|---|---|
| Jenis data | Time series bulanan |
| Periode | Januari 2018 – Desember 2025 |
| Jumlah observasi | 96 data |
| Satuan | Juta ton |
| Metode | SARIMA |

---

## Statistik Deskriptif

| Statistik | Nilai |
|---|---:|
| Minimum | 1.516 |
| Q1 | 3.216 |
| Median | 4.312 |
| Mean | 4.635 |
| Q3 | 5.494 |
| Maksimum | 9.768 |
| Standar Deviasi | 2.122 |

## Tahapan Analisis

1. Melakukan statistik deskriptif data produksi padi.
2. Membuat visualisasi pola data time series.
3. Mengidentifikasi pola musiman bulanan.
4. Menentukan periode musiman `s = 12`.
5. Melakukan uji stasioneritas varians menggunakan Box-Cox Transformation.
6. Melakukan uji stasioneritas rataan menggunakan Augmented Dickey-Fuller Test.
7. Melakukan differencing non-musiman dan seasonal differencing.
8. Mengidentifikasi parameter model menggunakan ACF dan PACF.
9. Membentuk dan mengestimasi kandidat model SARIMA.
10. Mengevaluasi model menggunakan Ljung-Box Test, Kolmogorov-Smirnov Test, dan MAPE.
11. Memilih model terbaik.
12. Melakukan prediksi produksi padi Indonesia tahun 2026.

---
## Kandidat Model SARIMA

Beberapa kandidat model yang diuji antara lain:

| No | Model SARIMA |
|---:|---|
| 1 | SARIMA(1,1,1)(1,1,1)₁₂ |
| 2 | SARIMA(2,1,1)(1,1,1)₁₂ |
| 3 | SARIMA(1,1,2)(1,1,1)₁₂ |
| 4 | SARIMA(2,1,2)(1,1,1)₁₂ |
| 5 | SARIMA(3,1,1)(1,1,1)₁₂ |
| 6 | SARIMA(1,1,2)(0,1,1)₁₂ |
| 7 | SARIMA(2,1,2)(0,1,1)₁₂ |
| 8 | SARIMA(3,1,1)(0,1,1)₁₂ |

---

## Evaluasi Model

| Peringkat | Model | MAPE |
|---:|---|---:|
| 1 | SARIMA(1,1,2)(0,1,1)₁₂ | 11.52 |
| 2 | SARIMA(1,1,2)(1,1,1)₁₂ | 11.55 |
| 3 | SARIMA(3,1,1)(0,1,1)₁₂ | 11.64 |
| 4 | SARIMA(2,1,2)(0,1,1)₁₂ | 11.76 |
| 5 | SARIMA(2,1,2)(1,1,1)₁₂ | 11.79 |

Model terbaik yang dipilih adalah:
(1 - ϕ₁B)(1 - B)(1 - B¹²)Yₜ =
(1 + θ₁B + θ₂B²)(1 + Θ₁B¹²)εₜ

(1 + 0.2124B)(1 - B)(1 - B¹²)Yₜ =
(1 - 0.3863B - 0.6137B²)(1 - 1.0000B¹²)εₜ
```text
SARIMA(1,1,2)(0,1,1)₁₂
