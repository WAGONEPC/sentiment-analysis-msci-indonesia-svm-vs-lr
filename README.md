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

# Perbandingan Support Vector Machine dan Logistic Regression untuk Analisis Sentimen Pengguna Media Sosial X terhadap Usulan Reklasifikasi Pasar Indonesia dari Emerging Market menjadi Standalone Market oleh MSCI
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
| **Akurasi (*Accuracy*)** | **80.68%** | **80.68%** | **0.00% (Setara / Imbang)** |
| **Precision (*Macro Avg*)** | 62.14% | **63.93%** | **+1.79% (LR Lebih Unggul)** |
| **Recall (*Macro Avg*)** | 58.78% | **61.40%** | **+2.62% (LR Lebih Unggul)** |
| **F1-Score (*Macro Avg*)** | 59.87% | **61.30%** | **+1.43% (LR Lebih Unggul)** |
| **F1-Score (*Weighted Avg*)** | 79.75% | **79.94%** | **+0.19% (LR Lebih Unggul)** |
| **Hyperparameter Terbaik** | `C=5.0`, `kernel='linear'` (Calibrated) | `C=10.0`, `solver='lbfgs'`, `max_iter=1000` | Optimal via 5-Fold Stratified CV |
| **F1-Macro Cross-Validation (Latih)** | **96.44%** | 96.29% | Evaluasi data latih (pasca-SMOTE) |

> [!NOTE]
> **Kesimpulan Ilmiah:**  
> **Logistic Regression mempertahankan keunggulan atas Support Vector Machine (SVM)** pada seluruh metrik evaluasi makro pengujian (*unseen test data*), yakni **Precision Macro (+1.79%)**, **Recall Macro (+2.62%)**, dan **F1-Score Macro (+1.43%)**, dengan capaian **Akurasi yang setara (80.68%)**.  
> Pemilihan kernel **Linear (`C=5.0`)** pada SVM secara drastis memperbaiki performa SVM dibanding kernel non-linear RBF terdahulu (skor F1-Macro melonjak dari 43.24% menjadi 59.87%), membuktikan bahwa ruang fitur teks TF-IDF 1.000 dimensi term lebih optimal dipisahkan dengan hyperplane linear. Meskipun demikian, Logistic Regression dengan solver **LBFGS** terbukti paling tangguh dalam mengklasifikasikan kelas minoritas (khususnya sentimen Netral dengan recall **63.64%** vs **54.55%** pada SVM) serta menghasilkan estimasi probabilitas keyakinan yang proporsional.

---

### 2. Laporan Klasifikasi Rinci per Kategori Sentimen (*Classification Report*)

#### A. Support Vector Machine (SVM — Kernel Linear, C=5.0)
```text
              precision    recall  f1-score   support

     Negatif       0.88      0.91      0.89       162
      Netral       0.52      0.55      0.53        22
     Positif       0.47      0.30      0.37        23

    accuracy                           0.81       207
   macro avg       0.62      0.59      0.60       207
weighted avg       0.79      0.81      0.80       207
```

#### B. Logistic Regression (Multinomial — Solver LBFGS, C=10.0)
```text
              precision    recall  f1-score   support

     Negatif       0.88      0.90      0.89       162
      Netral       0.50      0.64      0.56        22
     Positif       0.54      0.30      0.39        23

    accuracy                           0.81       207
   macro avg       0.64      0.61      0.61       207
weighted avg       0.80      0.81      0.80       207
```

---

### 3. Analisis Matriks Konfusi (*Confusion Matrix*)

Matriks konfusi pengujian pada 207 data uji riil (*unseen test data*):

```text
Confusion Matrix SVM (Linear):             Confusion Matrix Logistic Regression (LBFGS):
            Pred: Neg   Net   Pos                     Pred: Neg   Net   Pos
Aktual Neg:   148     8     6             Aktual Neg:   146    12     4
Aktual Net:     8    12     2             Aktual Net:     6    14     2
Aktual Pos:    13     3     7             Aktual Pos:    14     2     7
```

* **Deteksi Sentimen Negatif:** Kedua model sangat akurat dan konsisten dalam mengidentifikasi sentimen negatif kepanikan pasar (SVM: 148 benar [91.36%], LR: 146 benar [90.12%]).
* **Deteksi Sentimen Netral:** Logistic Regression lebih unggul mendeteksi tweet netral (**14 tweet benar [63.64%]**) dibandingkan SVM yang menangkap **12 tweet benar [54.55%]**.
* **Deteksi Sentimen Positif:** Kedua model mendeteksi jumlah tweet positif benar yang setara (**7 tweet benar [30.43%]**), namun Logistic Regression memiliki presisi lebih tinggi (**53.85%** vs **46.67%** pada SVM) karena lebih sedikit menghasilkan *false positive* dari kelas negatif (4 kesalahan pada LR vs 6 pada SVM).

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
│ 2. Preprocessing Data Teks Bahasa Indonesia (5 Tahap NLP Sastrawi)    │
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
│    - Distribusi Awal: Negatif (77.86%), Positif (11.07%), Netral (11.07│
│    - Dataset Valid Modeling (1.033 data): Neg (78.3%), Pos/Net (11.1%) │
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
│    ├── Model A: Support Vector Machine (C=5.0, Kernel Linear, Calib)   │
│    └── Model B: Logistic Regression (C=10.0, Solver LBFGS, max_iter=1K)│
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

Dataset dikumpulkan dari platform media sosial X menggunakan Tweet-Harvest v2.7.1 dengan total **1.039 tweet mentah**.

### 1. Distribusi Hasil Pelabelan Sentimen Awal (1.039 Tweet)

| Kategori Sentimen | Jumlah Tweet | Persentase | Karakteristik Narasi Publik |
| :--- | :---: | :---: | :--- |
| **Negatif** | **809** | **77.86%** | Dominan kepanikan aksi jual asing (*outflow*), pelemahan IHSG, ketidakpastian pasar, kekhawatiran likuiditas status *standalone*. |
| **Positif** | **115** | **11.07%** | Harapan momentum *rebound*, peluang akumulasi saham fundamental di harga diskon (*buy on weakness*), dividen yield tinggi. |
| **Netral** | **115** | **11.07%** | Laporan berita reguler bursa, jadwal evaluasi berkala MSCI, pernyataan resmi OJK dan Bursa Efek Indonesia (BEI). |
| **Total** | **1.039** | **100.0%** | |

### 2. Distribusi Dataset Valid Tahap Pemodelan (1.033 Tweet)
Pada proses preprocessing teks, terdapat 6 tweet (seluruhnya berlabel Netral yang hanya berisi karakter non-alfanumerik/simbol) yang menghasilkan string kosong setelah proses stemming, sehingga dieksklusi (`dropna`) guna menjaga kualitas representasi fitur kata:
* **Negatif:** 809 tweet (78.32%)
* **Positif:** 115 tweet (11.13%)
* **Netral:** 109 tweet (10.55%)
* **Total:** 1.033 tweet valid

#### Pembagian Data Latih dan Uji (Stratified Split 80:20):
* **Data Latih (80%):** 826 sampel (Negatif: 647, Positif: 92, Netral: 87) $\rightarrow$ Diseimbangkan dengan **SMOTE** menjadi **1.941 sampel** (647 per kelas berimbang).
* **Data Uji (20%):** 207 sampel (Negatif: 162, Positif: 23, Netral: 22) dibiarkan alami tanpa modifikasi sintetis (*zero data leakage*).

### 3. Distribusi Berdasarkan Periode Pengumuman Usulan MSCI:
* **Sebelum Pengumuman (1 - 15 Oktober 2026):** **68 tweet** (Negatif: 54, Netral: 6, Positif: 8) — Sentimen pasar mulai tertekan membayangi pergerakan indeks.
* **Sesudah Pengumuman (15 - 27 Oktober 2026):** **971 tweet** (Negatif: 755, Netral: 109, Positif: 107) — Lonjakan drastis perbincangan publik pasca rilis konsultasi reklasifikasi MSCI.

---

## Struktur Direktori Repositori

```text
sentiment-analysis-msci-indonesia-svm-vs-lr/
│
├── README.md                                  # Dokumentasi teknis lengkap penelitian
├── LICENSE.txt                                # Lisensi terbuka Creative Commons CC BY-NC-ND 4.0
├── visualisasi_sentimen.png                   # Visualisasi sebaran sentimen & perbandingan periode
│
├── scraping_tw.ipynb                          # Notebook 1: Crawling, Preprocessing NLP, Pelabelan, TF-IDF, SMOTE
├── svm_training_testing.ipynb                 # Notebook 2: Pelatihan, Tuning GridSearch, & Pengujian SVM (Linear)
├── logistic_regression_training_testing.ipynb # Notebook 3: Pelatihan, Tuning GridSearch, & Pengujian Logistic Regression (LBFGS)
│
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
    ├── svm_model.pkl                          # Model SVM terbaik (Linear, C=5.0 terkalibrasi)
    ├── logistic_regression_model.pkl          # Model Logistic Regression terbaik (LBFGS, C=10.0)
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
1. **`scraping_tw.ipynb`**: Memuat seluruh alur prapemrosesan teks, kalkulasi skor polaritas leksikon, pembobotan TF-IDF, dan penyeimbangan SMOTE.
2. **`svm_training_testing.ipynb`**: Menjalankan pelatihan SVM Linear (`C=5.0`), pencarian hyperparameter *GridSearch* 5-Fold, evaluasi testing, visualisasi confusion matrix, dan pengujian inferensi tweet baru.
3. **`logistic_regression_training_testing.ipynb`**: Menjalankan pelatihan Logistic Regression multinomial (`lbfgs`, `C=10.0`), visualisasi probabilitas keyakinan kelas, dan perbandingan performa.

### 4. Menggunakan Model Tersimpan untuk Prediksi Teks Baru (Inferensi Python)
```python
import joblib
import re
from Sastrawi.Stemmer.StemmerFactory import StemmerFactory
from Sastrawi.StopWordRemover.StopWordRemoverFactory import StopWordRemoverFactory

# Muat model Logistic Regression (atau 'models/svm_model.pkl') dan vectorizer
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
    
    return label, dict(zip(model.classes_, (probabilitas * 100).round(2)))

# Uji coba kalimat baru
contoh_tweets = [
    "Kacau banget kalau sampai beneran turun ke Standalone. Outflow asing bakal makin deras, likuiditas anjlok, nasib porto ritel boncos parah ini.",
    "Peluang serok saham-saham undervalue! Valuasi lagi pada murah karena kepanikan isu MSCI, buat investor jangka panjang ini momentum akumulasi.",
    "ihsg bergerak flat menanti data inflasi dan rilis msci hari ini"
]

for tw in contoh_tweets:
    label, proba = prediksi_sentimen(tw)
    print(f"Teks: {tw[:70]}...")
    print(f"Prediksi: [{label}] | Probabilitas (%): {proba}\n")
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
git commit -m "feat: update latest model evaluation metrics for linear SVM and logistic regression"

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
