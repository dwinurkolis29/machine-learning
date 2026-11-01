# Machine Learning Case Studies

Repository ini berisi kumpulan studi kasus dan eksperimen Machine Learning menggunakan Python dan Jupyter Notebook. Setiap folder merepresentasikan satu topik mandiri beserta dataset yang digunakan.

## Daftar Proyek

| Folder | Topik / Metode | Notebook | Dataset |
| :--- | :--- | :--- | :--- |
| `01-estimasi-harga-mobil` | Regresi Linear (Estimasi Harga Mobil Bekas) | `estimasi_mobil-v2.ipynb` | `toyota.csv` (Lokal) |
| `02-prediksi-harga-rumah` | Regresi (Prediksi Harga Rumah) | `prediksi_harga_rumah.ipynb` | Otomatis via `kagglehub` (`shree1992/housedata`) |
| `03-customer-clustering` | K-Means Clustering + Integrasi Streamlit | `clustering_streamlit_colab.ipynb` | `Mall_Customers.csv` (Lokal) |
| `04-market-basket-analysis` | Association Rules / Apriori (Market Basket) | `market_basket_all_in_one.ipynb` | Otomatis via `kagglehub` (`mittalvasu95/the-bread-basket`) / `bread_basket.csv` |

## Cara Menjalankan (VS Code Lokal & Google Colab)

1. Masuk ke sub-folder proyek yang ingin dijalankan.
2. Buka file `.ipynb` menggunakan VS Code, PyCharm, Jupyter Notebook, atau Google Colab.
3. Klik **Run All**. Notebook akan otomatis mendeteksi environment:
   - **VS Code Lokal:** Menjalankan server Streamlit di background pada `http://localhost:8501`.
   - **Google Colab:** Mengunduh `cloudflared` dan membuka akses publik via tautan `.trycloudflare.com`.
