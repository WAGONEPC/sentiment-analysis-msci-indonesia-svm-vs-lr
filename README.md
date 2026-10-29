<p align="center">
  <a href="https://creativecommons.org/licenses/by-nc-nd/4.0/"><img src="https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg" alt="License: CC BY-NC-ND 4.0"></a>
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue.svg" alt="Python Version">
  <img src="https://img.shields.io/badge/Scikit--Learn-1.4%2B-orange.svg" alt="Scikit-Learn">
  <img src="https://img.shields.io/badge/NLP-Sastrawi%20%7C%20TF--IDF-green.svg" alt="NLP">
  <img src="https://img.shields.io/badge/Status-Completed-success.svg" alt="Status">
</p>

# TIM PENELITI & PEMBAGIAN KONTRIBUSI

Penelitian komparasi analisis sentimen ini dilakukan secara kolaboratif oleh tim peneliti Program Studi Teknologi Informasi, Universitas Darma Persada. Berikut rincian peran dan kontribusi masing-masing anggota:

| Foto / Avatar | Nama Peneliti | Peran & Tanggung Jawab | Rincian Kontribusi |
| :---: | :--- | :--- | :--- |
| <img src="https://res.cloudinary.com/dexbm5dzz/image/upload/v1793279294/142272351_zzbdqh.jpg" width="70" style="border-radius:50%"/> | **Sayyid Abdullah Azzam**<br><sub>Lead Researcher</sub><br>[@WAGONEPC](https://github.com/WAGONEPC) | **Project Lead & Data Scraping** | • Perancangan metodologi riset<br>• Pengumpulan dataset tweet X (Scraping)<br>• Data cleaning & eliminasi noise (emoji/regex) |
| <img src="https://res.cloudinary.com/dexbm5dzz/image/upload/v1793279294/152648672_t1rneq.png" width="70" style="border-radius:50%"/> | **Andreas Rio Christian**<br><sub>NLP Specialist</sub><br>[@anrchrt275](https://github.com/anrchrt275) | **Text Preprocessing & Lexicon** | • Pipeline Sastrawi (Stemming & Stopwords)<br>• Pelabelan leksikon InSet & Market Lexicon<br>• Analisis negasi kata bahasa Indonesia |
| <img src="https://github.com/github-username-3.png" width="70" style="border-radius:50%"/> | **Ridwan Wahyu Kurniawan**<br><sub>ML Engineer</sub><br>[@rwku](https://github.com/rwku) | **Modeling & Hyperparameter Tuning** | • Ekstraksi fitur TF-IDF & penanganan SMOTE<br>• Pelatihan model SVM & Logistic Regression<br>• Evaluasi Confusion Matrix, Akurasi, & F1-Score |
| <img src="https://github.com/github-username-4.png" width="70" style="border-radius:50%"/> | **Dr. Aji Setiawan, S.Kom, MMSI**<br><sub>Advisor / Supervisor</sub><br>[@username-4](https://github.com/username-4) | **Dosen Pembimbing / Reviewer** | • Supervisi arah penelitian & metodologi ilmiah<br>• Validasi hasil komparasi algoritma<br>• Penelaahan naskah publikasi ilmiah |

--- 

# Analisis Sentimen Usulan Reklasifikasi MSCI Indonesia di Media Sosial X: Komparasi Model SVM vs. Logistic Regression
**Publikasi Ilmiah / Tugas Akhir — Program Studi Teknologi Informasi, Universitas Darma Persada (UNSADA)**  
**Repositori GitHub:** [https://github.com/WAGONEPC/sentiment-analysis-msci-indonesia-svm-vs-lr](https://github.com/WAGONEPC/sentiment-analysis-msci-indonesia-svm-vs-lr)

---

## Ringkasan Eksekutif Penelitian

Penelitian ini mengkaji respons dan sentimen publik di media sosial **X (sebelumnya Twitter)** terkait wacana usulan Morgan Stanley Capital International (**MSCI**) untuk menurunkan klasifikasi pasar saham Indonesia dari status *Emerging Market* menjadi *Standalone Market*. 

Eksperimen dilakukan secara komprehensif mulai dari penarikan data (*crawling*), prapemrosesan teks Bahasa Indonesia (*NLP Preprocessing*), pelabelan sentimen berbasis leksikon (*InSet + Kamus Pasar Modal*), ekstraksi fitur **TF-IDF**, penanganan ketidakseimbangan kelas menggunakan **SMOTE**, hingga perbandingan kinerja klasifikasi antara **Support Vector Machine (SVM)** dan **Logistic Regression (LR)**.

---

## Temuan Utama & Hasil Komparasi Model

Pengujian dilakukan pada **Data Testing murni (*unseen test data*)** sebanyak **207 sampel (20%)** yang dibiarkan alami tanpa augmentasi SMOTE guna menjamin integritas ilmiah (*zero data leakage*).

### 1. Tabel Perbandingan Kinerja (SVM vs. Logistic Regression)

| Metrik Evaluasi | Support Vector Machine (SVM) | Logistic Regression (LR) | Selisih / Keunggulan |
| :--- | :---: | :---: | :---: |
| **Akurasi (*Accuracy*)** | 79.23% | **81.16%** | **+1.93% (LR Lebih Unggul)** |
| **Precision (*Macro Avg*)** | 64.05% | **64.47%** | **+0.42% (LR Lebih Unggul)** |
| **Recall (*Macro Avg*)** | 41.47% | **60.29%** | **+18.82% (LR Jauh Lebih Unggul)** |
| **F1-Score (*Macro Avg*)** | 43.24% | **61.21%** | **+17.97% (LR Jauh Lebih Unggul)** |
| **F1-Score (*Weighted Avg*)** | 73.73% | **80.19%** | **+6.46% (LR Lebih Unggul)** |
| **Hyperparameter Terbaik** | `C=10.0`, `kernel='rbf'`, `gamma='scale'` | `C=10.0`, `solver='saga'`, `max_iter=1000` | Optimal via 5-Fold Stratified CV |
| **F1-Macro Cross-Validation (Latih)** | 98.37% | 95.92% | Evaluasi internal data training |

> **Kesimpulan Ilmiah:**  
> **Logistic Regression mengungguli Support Vector Machine (SVM) di seluruh metrik evaluasi pengujian**, khususnya pada **Recall Macro (+18.82%)** dan **F1-Score Macro (+17.97%)**. Meskipun SVM memperoleh akurasi 79.23%, SVM mengalami bias mayoritas dan gagal mengenali kelas minoritas dengan baik. Sebaliknya, Logistic Regression mampu menggeneralisasi ruang fitur sintetis hasil SMOTE secara jauh lebih seimbang dan tangguh pada data dunia nyata.

---

### 2. Laporan Klasifikasi Rinci per Kategori Sentimen (*Classification Report*)

#### A. Support Vector Machine (SVM — Kernel RBF)
```text
              precision    recall  f1-score   support

     Negatif       0.81      0.98      0.89       162
      Netral       0.44      0.18      0.26        22
     Positif       0.67      0.09      0.15        23

    accuracy                           0.79       207
   macro avg       0.64      0.41      0.43       207
weighted avg       0.76      0.79      0.74       207
```

#### B. Logistic Regression (Multinomial — Solver SAGA)
```text
              precision    recall  f1-score   support

     Negatif       0.88      0.91      0.89       162
      Netral       0.52      0.59      0.55        22
     Positif       0.54      0.30      0.39        23

    accuracy                           0.81       207
   macro avg       0.64      0.60      0.61       207
weighted avg       0.80      0.81      0.80       207
```

---

### 3. Analisis Matriks Konfusi (*Confusion Matrix*)

Matriks konfusi pengujian pada 207 data uji riil:

```text
Confusion Matrix SVM:                     Confusion Matrix Logistic Regression:
            Pred: Neg   Net   Pos                     Pred: Neg   Net   Pos
Aktual Neg:   158     4     0             Aktual Neg:   148    10     4
Aktual Net:    17     4     1             Aktual Net:     7    13     2
Aktual Pos:    20     1     2             Aktual Pos:    14     2     7
```

* **Deteksi Sentimen Negatif:** Kedua model sangat akurat dalam mengidentifikasi kepanikan pasar (SVM: 158 benar, LR: 148 benar).
* **Deteksi Sentimen Netral:** Logistic Regression berhasil mendeteksi **13 tweet netral** dibandingkan SVM yang hanya mampu menangkap **4 tweet**.
* **Deteksi Sentimen Positif:** Logistic Regression berhasil mendeteksi **7 tweet positif** (3.5x lipat lebih banyak dari SVM yang hanya menangkap **2 tweet**).

---

## Arsitektur Alur Metodologi

Diagram berikut menggambarkan alur terpadu penelitian:

```
┌────────────────────────────────────────────────────────────────────────┐
│ 1. Pengumpulan Data Media Sosial X (Tweet-Harvest v2.7.1)              │
│    - Periode Sebelum Pengumuman Usulan (1 - 15 Oktober 2026)           │
│    - Periode Sesudah Pengumuman Usulan (15 - 27 Oktober 2026)          │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 2. Preprocessing Data Teks Bahasa Indonesia (5 Tahap NLP)             │
│    ├── a. Data Cleaning (Hapus URL, mention, hashtag, simbol, emoji)   │
│    ├── b. Case Folding (Konversi ke huruf kecil / lowercase)           │
│    ├── c. Tokenization (Pemecahan kalimat menjadi kata/token)          │
│    ├── d. Stopword Removal (Penyaringan kata tidak bermakna Sastrawi)  │
│    └── e. Stemming (Pengubahan ke bentuk dasar Sastrawi Memoization)   │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 3. Pelabelan Sentimen Berbasis Leksikon (Lexicon-Based Labeling)       │
│    ├── InSet Lexicon (Fajri Koto & Gemala Y. Rahmaningtyas)            │
│    ├── Leksikon Pasar Modal Indonesia (cuan, rebound, anjlok, dll.)    │
│    └── Penanganan Negasi (membalik polaritas kata: tidak, bukan, dll.) │
│    Hasil Distribusi: Negatif (78.3%), Positif (11.1%), Netral (10.6%)  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 4. Ekstraksi Fitur TF-IDF (Term Frequency - Inverse Document Freq)     │
│    - Matriks numerik X berdimensi 1.000 fitur term representatif       │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 5. Pembagian Data (Train-Test Split 80:20 Stratified)                  │
│    - Data Latih (80%): 826 sampel                                      │
│    - Data Uji   (20%): 207 sampel (Alami, Tanpa Augmentasi)            │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 6. Penyeimbangan Data Training Menggunakan SMOTE                       │
│    - Mengatasi ketimpangan ekstrem (78.3% vs 11.1% vs 10.6%)           │
│    - Menyeimbangkan Data Latih menjadi 1.941 sampel (647 per kelas)    │
│    - Data Uji TETAP ALAMI untuk mencegah kebocoran data (Data Leakage) │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 7. Pelatihan & Optimasi Hyperparameter (GridSearchCV 5-Fold)          │
│    ├── Model A: Support Vector Machine (C=10.0, Kernel RBF)            │
│    └── Model B: Logistic Regression (C=10.0, Solver SAGA, max_iter=1K) │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 8. Evaluasi Komparatif & Penyimpanan Model (.pkl)                      │
│    - Evaluasi: Accuracy, Precision, Recall, F1-Score, Confusion Matrix │
│    - Model disimpan di direktori models/ menggunakan Joblib            │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Statistik & Karakteristik Dataset

Total tweet yang dikumpulkan dan telah divalidasi berjumlah **1.039 tweet unik**:

| Kategori Sentimen | Jumlah Tweet | Persentase | Karakteristik Narasi Publik |
| :--- | :---: | :---: | :--- |
| **Negatif** | **809** | **78.32%** | Dominan kepanikan aksi jual asing (*outflow*), penurunan IHSG, ketidakpastian pasar, kekhawatiran status *standalone*. |
| **Positif** | **115** | **11.13%** | Harapan momentum *rebound*, peluang akumulasi saham fundamental di harga murah (*buy on weakness*), dividen yield tinggi. |
| **Netral** | **109** | **10.55%** | Laporan berita reguler, jadwal evaluasi berkala MSCI, pernyataan resmi OJK dan Bursa Efek Indonesia (BEI). |
| **Total** | **1.039** | **100.0%** | |

### Distribusi Berdasarkan Periode Pengumuman Usulan MSCI:
* **Sebelum Pengumuman (1 - 15 Oktober 2026):** 68 tweet (Sentimen pasar mulai tertekan membayangi IHSG).
* **Sesudah Pengumuman (15 - 27 Oktober 2026):** 971 tweet (Lonjakan drastis perbincangan publik pasca rilis konsultasi reklasifikasi MSCI).

---

## Struktur Direktori Repositori

```text
sentiment-analysis-msci-indonesia-svm-vs-lr/
│
├── README.md                                  # Dokumentasi teknis lengkap penelitian
├── LICENSE.txt                                # Lisensi terbuka Creative Commons CC BY-NC-ND 4.0
├── visualisasi_sentimen.png                   # Visualisasi sebaran sentimen & perbandingan periode
│
├── scraping-tw.ipynb                          # Notebook 1: Crawling, Preprocessing NLP, Pelabelan, TF-IDF, SMOTE
├── svm_training_testing.ipynb                 # Notebook 2: Pelatihan, Tuning GridSearch, & Pengujian SVM
├── logistic_regression_training_testing.ipynb # Notebook 3: Pelatihan, Tuning GridSearch, & Pengujian Logistic Regression
│
├── dataset_msci_bersih.csv                    # Dataset hasil crawling dan deduplikasi
├── dataset_msci_labeled.csv                   # Dataset berlabel sentimen (Positif, Netral, Negatif)
├── dataset_msci_preprocessed.csv              # Dataset lengkap dengan 5 kolom tahapan NLP Sastrawi
│
├── tweets-data/                               # Berkas mentah per query pencarian Twitter/X
│   ├── sebelum_1.csv                          # Query: "MSCI Indonesia" (Sebelum)
│   ├── sebelum_2.csv                          # Query: "MSCI IHSG" (Sebelum)
│   ├── sebelum_3.csv                          # Query: "MSCI saham" (Sebelum)
│   ├── sesudah_1.csv                          # Query: "MSCI Indonesia" (Sesudah)
│   ├── sesudah_2.csv                          # Query: "MSCI IHSG" (Sesudah)
│   └── sesudah_3.csv                          # Query: "MSCI standalone" (Sesudah)
│
├── lexicon/                                   # Berkas kamus leksikon sentimen Bahasa Indonesia
│   ├── positive.tsv                           # InSet Positive Lexicon (3.610 kata berbobot)
│   └── negative.tsv                           # InSet Negative Lexicon (6.610 kata berbobot)
│
└── models/                                    # Model biner terkompilasi siap inferensi
    ├── svm_model.pkl                          # Model SVM terbaik (RBF, C=10.0)
    ├── logistic_regression_model.pkl          # Model Logistic Regression terbaik (SAGA, C=10.0)
    └── tfidf_vectorizer.pkl                   # Objek TF-IDF Vectorizer (1.000 fitur term)
```

---

## Panduan Replikasi & Penggunaan

### 1. Kloning Repositori
```bash
git clone https://github.com/WAGONEPC/sentiment-analysis-msci-indonesia-svm-vs-lr.git
cd sentiment-analysis-msci-indonesia-svm-vs-lr
```

### 2. Pemasangan Pustaka Dependensi
Pastikan Python 3.10+ telah terpasang. Jalankan instalasi pustaka:
```bash
pip install pandas numpy scikit-learn imbalanced-learn Sastrawi matplotlib seaborn joblib
```

### 3. Eksekusi Notebook
1. **`scraping-tw.ipynb`**: Memuat seluruh alur prapemrosesan teks, kalkulasi skor polaritas leksikon, pembobotan TF-IDF, dan penyeimbangan SMOTE.
2. **`svm_training_testing.ipynb`**: Menjalankan pelatihan SVM, pencarian hyperparameter *GridSearch* 5-Fold, evaluasi testing, visualisasi confusion matrix, dan pengujian inferensi tweet baru.
3. **`logistic_regression_training_testing.ipynb`**: Menjalankan pelatihan Logistic Regression multinomial, visualisasi probabilitas keyakinan kelas, dan perbandingan performa.

### 4. Menggunakan Model Tersimpan untuk Prediksi Teks Baru (Inferensi Python)
```python
import joblib
import re
from Sastrawi.Stemmer.StemmerFactory import StemmerFactory
from Sastrawi.StopWordRemover.StopWordRemoverFactory import StopWordRemoverFactory

# Muat model dan vectorizer
model = joblib.load('models/logistic_regression_model.pkl')
tfidf = joblib.load('models/tfidf_vectorizer.pkl')

stemmer = StemmerFactory().create_stemmer()
stopword = StopWordRemoverFactory().create_stop_word_remover()

def prediksi_sentimen(tweet_baru):
    # Cleaning & Normalisasi
    clean = re.sub(r'https?://\S+|[@#]\S+|[^\w\s]|\d+', ' ', tweet_baru).lower().strip()
    stemmed = stemmer.stem(stopword.remove(clean))
    
    # Transformasi TF-IDF & Prediksi
    vektor = tfidf.transform([stemmed]).toarray()
    label = model.predict(vektor)[0]
    probabilitas = model.predict_proba(vektor)[0]
    
    return label, dict(zip(model.classes_, probabilitas.round(4)))

# Uji coba
tweet_contoh = "Pasar saham Indonesia mulai rebound hari ini seiring investor kembali akumulasi saham perbankan!"
hasil, proba = prediksi_sentimen(tweet_contoh)
print(f"Prediksi: {hasil}")
print(f"Probabilitas: {proba}")
```

---

## Panduan Push ke Repositori GitHub

Untuk memperbarui repositori GitHub Anda di `https://github.com/WAGONEPC/sentiment-analysis-msci-indonesia-svm-vs-lr.git`, jalankan perintah Git berikut dari direktori proyek:

```bash
# 1. Inisialisasi Git (jika belum)
git init

# 2. Tambahkan remote repository
git remote add origin https://github.com/WAGONEPC/sentiment-analysis-msci-indonesia-svm-vs-lr.git

# 3. Tambahkan seluruh berkas proyek
git add .

# 4. Buat commit
git commit -m "feat: complete end-to-end sentiment analysis pipeline with SVM and Logistic Regression models"

# 5. Pastikan berada di branch main
git branch -M main

# 6. Push ke GitHub
git push -u origin main
```

*(Catatan: Jika repositori di GitHub sudah memiliki berkas awal seperti commit default, tambahkan opsi `--force` saat push pertama jika diperlukan: `git push -u origin main --force`)*.

---

## Lisensi & Atribusi

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-nd/4.0/)

Proyek penelitian dan dataset ini dilisensikan di bawah **[Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0)](https://creativecommons.org/licenses/by-nc-nd/4.0/)**.

* **Attribution (BY):** Wajib mencantumkan atribusi penghargaan dan sitasi kepada penulis/peneliti asli.
* **NonCommercial (NC):** Tidak diperkenankan untuk penggunaan komersial dalam bentuk apa pun.
* **NoDerivatives (ND):** Jika Anda menggubah, mengubah, atau membuat turunan dari materi ini, Anda tidak boleh menyebarluaskan materi yang telah diubah tersebut.

---

**Peneliti / Kontributor:** Mahasiswa Semester 7, Program Studi Teknologi Informasi, Universitas Darma Persada (UNSADA)  
**Tahun Penelitian:** 2026
