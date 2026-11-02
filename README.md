# Machine Learning Case Studies & Learning Repository

Repository ini berisi kumpulan studi kasus dan eksperimen Machine Learning serta analisis pemodelan statistik menggunakan Python, Jupyter Notebook, dan Streamlit. Setiap sub-folder merepresentasikan satu topik mandiri beserta dataset dan penjelasan konsep algoritmanya.

## Ringkasan Proyek & Konsep Algoritma

| Folder | Kategori / Mata Kuliah | Algoritma Utama | Mengapa Algoritma Ini Digunakan? | Metrik Evaluasi Utama |
| :--- | :--- | :--- | :--- | :--- |
| [`01-estimasi-harga-mobil`](./01-estimasi-harga-mobil) | *Supervised Learning* (Regression) | **Multiple Linear Regression** (`scikit-learn`) | Target berupa nilai numerik kontinu (`price`) yang memiliki hubungan linier kuat dengan usia kendaraan (`year`), jarak tempuh (`mileage`), pajak (`tax`), konsumsi BBM (`mpg`), dan ukuran mesin (`engineSize`). Sangat cepat dan mudah diinterpretasikan (*white-box model*). | **R-Squared ($R^2$)** (Proporsi variasi harga yang mampu dijelaskan oleh fitur) |
| [`02-prediksi-harga-rumah`](./02-prediksi-harga-rumah) | *Supervised Learning* (Regression / Deep Learning Dasar) | **Single-Layer Artificial Neural Network / Perceptron** (`Dense(units=1)`) | Memperkenalkan cara kerja dasar jaringan saraf tiruan (*forward pass*, *loss*, dan *backpropagation*) menggunakan optimasi **Stochastic Gradient Descent (`SGD`)** untuk memprediksi harga rumah dari 4 fitur fisik. | **MAE (*Mean Absolute Error*)** (Rata-rata selisih absolut harga, tahan terhadap *outlier* rumah mewah) |
| [`03-customer-clustering`](./03-customer-clustering) | *Unsupervised Learning* (Clustering) | **K-Means Clustering** (`scikit-learn`) | Dataset pelanggan (`Mall_Customers.csv`) tidak memiliki label segmen sebelumnya. K-Means mengelompokkan pelanggan berdasarkan kemiripan jarak Euclidean pada pendapatan (`Income`) dan skor belanja (`Score`). | **Inertia (WCSS)** & **Elbow Method** (Menentukan jumlah klaster $K$ paling optimal) |
| [`04-market-basket-analysis`](./04-market-basket-analysis) | *Unsupervised Learning* (Association Rule Mining) | **Algoritma Apriori** (`mlxtend`) | Mencari pola keterkaitan barang yang dibeli bersamaan (*"Jika membeli A, maka membeli B"*) pada data transaksi toko roti (`bread_basket.csv`) untuk rekomendasi *cross-selling* dan penataan produk. | **Support** (Frekuensi kombinasi), **Confidence** (Peluang bersyarat), dan **Lift** (Kekuatan asosiasi $> 1$) |
| [`05-analisis-regresi`](./05-analisis-regresi) | **Mata Kuliah Data Insight** — *Supervised Learning* (Linear & Non-Linear Regression) | **Regresi Linear, Kuadratik, Eksponensial, & Logaritma** (`numpy`, `scipy`, `scikit-learn`) | Tugas **Mata Kuliah Data Insight** ($\alpha = 0,05$) pada dataset `Data Analisis Regresi.xlsx` (sheet `Onevar`) untuk menganalisis *scatter plot*, korelasi Pearson ($r$), dan memilih persamaan fungsi terbaik antara variabel independen `X` terhadap 4 variabel dependen (`Y`, `L`, `R`, `S`). | **R-Squared ($R^2$)** & **Uji Korelasi Pearson ($p\text{-value} < 0,05$)** |

---

## Ringkasan Hasil Tugas Analisis Regresi (Mata Kuliah: Data Insight)

Pada folder [`05-analisis-regresi`](./05-analisis-regresi), dilakukan pemodelan dengan taraf signifikansi $\alpha = 0,05$ terhadap variabel independen $X$ ($N = 80$) untuk empat model matematika:
- **a) Model Linear:** $Y = b_0 + b_1 X$
- **b) Model Kuadratik:** $Y = b_0 + b_1 X + b_2 X^2$
- **c) Model Eksponensial:** $Y = \exp(b_0 + b_1 X)$
- **d) Model Logaritma:** $Y = \ln(b_0 + b_1 X)$

| Variabel Dependen | Korelasi Pearson ($r$) | Model Paling Sesuai | Persamaan Regresi Terbaik | Nilai $R^2$ |
| :---: | :---: | :--- | :--- | :---: |
| **`Y`** | $0,9614$ ($p < 0,05$) | **a) Model Linear** | $Y = 5,2626 + 0,5040 X$ | **$0,9243$** |
| **`L`** | $0,8995$ ($p < 0,05$) | **d) Model Logaritma** | $L = \ln(5,2514 + 0,4992 X)$ | **$0,9948$** |
| **`R`** | $0,5618$ ($p < 0,05$) | **b) Model Kuadratik** | $R = 10,1186 + 1,0137 X + 1,9976 X^2$ | **$0,9999$** |
| **`S`** | $0,6345$ ($p < 0,05$) | **c) Model Eksponensial** | $S = \exp(5,1788 + 0,5111 X)$ | **$0,9890$** |

---

## Struktur Folder

```text
machine-learning/
├── README.md
├── requirements.txt
├── .gitignore
├── 01-estimasi-harga-mobil/
│   ├── estimasi_mobil-v2.ipynb
│   └── toyota.csv
├── 02-prediksi-harga-rumah/
│   ├── prediksi_harga_rumah.ipynb
│   └── data.csv                          # Tersedia lokal + fallback auto-download via kagglehub
├── 03-customer-clustering/
│   ├── clustering_streamlit_colab.ipynb
│   └── Mall_Customers.csv
├── 04-market-basket-analysis/
│   ├── market_basket_all_in_one.ipynb
│   └── bread_basket.csv                  # Tersedia lokal + fallback auto-download via kagglehub
└── 05-analisis-regresi/                  # Mata Kuliah: Data Insight (Tugas Analisis Regresi)
    ├── analisis_regresi.ipynb
    ├── Data Analisis Regresi.xlsx        # Sheet: "Onevar" (X, Y, S, L, R)
    └── onevar.csv
```

---

## Persiapan Environment Lokal (`.venv`)

Jika baru melakukan *clone* repository ini di komputer lokal, buat dan aktifkan *virtual environment* berikut:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Cara Menjalankan (VS Code Lokal & Google Colab)

1. Buka folder proyek ini di **VS Code** atau **PyCharm**.
2. Buka file `.ipynb` pada sub-folder yang ingin dipelajari, lalu pilih kernel Python dari **`.venv` (`Python 3.13 (.venv)`)** di pojok kanan atas notebook.
3. Klik **Run All**. Notebook akan otomatis mendeteksi environment tempat kode dijalankan:
   - **Di VS Code Lokal:** Menjalankan server Streamlit di *background* pada port terpisah agar bisa dibuka bersamaan tanpa bentrok:
     - `01-estimasi-harga-mobil`: `http://localhost:8501`
     - `03-customer-clustering`: `http://localhost:8502`
     - `04-market-basket-analysis`: `http://localhost:8503`
   - **Di Google Colab:** Mengunduh `cloudflared` dan membuka akses publik via tautan `.trycloudflare.com`.
