# Sistem Identifikasi Kontainer Logistik Berbasis Warna Menggunakan Algoritma K-Nearest Neighbor (KNN)

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-green.svg)](https://opencv.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-orange.svg)](https://scikit-learn.org/)
[![Accuracy](https://img.shields.io/badge/Accuracy-90.16%25-brightgreen.svg)]()

Repositori ini memuat implementasi lengkap sistem visi komputer dan *machine learning* untuk mendeteksi dan mengklasifikasi warna peti kemas (kontainer) logistik secara otomatis menggunakan algoritma **K-Nearest Neighbor (KNN)** dan **OpenCV**.

Proyek ini dikembangkan oleh **Firstyatama Auzan Farhadi** (NIM: 1203220009) sebagai bagian dari pemenuhan tugas akademik mata kuliah Artificial Intelligence / Pengolahan Citra Digital di **Universitas Telkom Surabaya**, serta disusun dalam format naskah publikasi ilmiah standar **IF0202**.

---

## 📌 Latar Belakang & Tujuan
Pada terminal kargo pelabuhan peti kemas, identifikasi jenis dan kepemilikan kontainer secara cepat merupakan elemen krusial dalam rantai pasok logistik (*supply chain*). Metode manual rentan terhadap *human error* dan lambat.

Proyek ini bertujuan untuk:
1. Mengotomasi proses klasifikasi warna bodi kontainer ke dalam 4 kelas utama:
   - ⚪ **Putih (White)**
   - 🔴 **Merah (Red)**
   - 🟢 **Hijau (Green)**
   - 🔵 **Biru (Blue)**
2. Mengekstraksi fitur visual warna yang optimal melalui ruang warna **RGB** dan **HSV**.
3. Menguji efektivitas algoritma **K-Nearest Neighbor (KNN)** dengan metrik *Euclidean Distance* di berbagai nilai parameter $K$.

---

## 🔬 Metodologi & Alur Sistem

```
[Akuisisi Citra Kontainer]
         │
         ▼
[Prapemrosesan Citra]
  ├── Segmentasi Region of Interest (ROI) pada Dinding Kontainer
  ├── Reduksi Noise (Gaussian Filter)
  └── Konversi Ruang Warna (RGB & HSV)
         │
         ▼
[Ekstraksi Vektor Fitur]
  ├── Rata-rata Intensitas Warna (R, G, B)
  └── Rata-rata Hue, Saturation, Value (H, S, V)
         │
         ▼
[Klasifikasi K-Nearest Neighbor (KNN)]
  ├── Perhitungan Jarak Euclidean
  └── Voting Kelas Terdekat ($K=1, 3, 5, 7, 9$)
         │
         ▼
[Evaluasi & Matriks Konfusi]
  └── Akurasi, Presisi, Recall, dan F1-Score
```

---

## 📊 Hasil Eksperimen & Evaluasi

Pengujian model dilakukan pada dataset citra kontainer outdoor riil dengan variasi pencahayaan dan sudut pengambilan:

| Nilai $K$ | Akurasi (\%) | Keterangan |
|:---:|:---:|---|
| $K = 1$ | 86.88% | Rentan terhadap *outlier/noise* piksel |
| $K = 3$ | 88.52% | Peningkatan stabilitas voting |
| **$K = 5$** | **90.16%** | **Akurasi Tertinggi (Optimal)** |
| $K = 7$ | 88.52% | *Boundary* mulai terlalu halus |
| $K = 9$ | 86.88% | Terjadi *oversmoothing* batas kelas |

Model mencapai performa optimal pada **$K = 5$** dengan tingkat akurasi **90,16%**, membuktikan bahwa ekstraksi fitur warna yang tepat dipadukan dengan algoritma KNN mampu memberikan klasifikasi yang andal dengan biaya komputasi rendah.

---

## 📁 Struktur Direktori

```
├── data/                                      # Dataset citra kontainer (train & validation)
├── data new/                                  # Dataset pengujian tambahan
├── aviewdataset.ipynb                         # Notebook eksplorasi visual dataset
├── colorDetection_KNN.ipynb                   # Eksperimen pipeline deteksi warna & KNN
├── KNNTERBARUU.ipynb                          # Notebook utama pelatihan & evaluasi model KNN
├── Confusion_matrix.ipynb                     # Perhitungan matriks konfusi & metrik performa
├── noLibrarryProgram.ipynb                    # Implementasi KNN dari dasar (scratch) tanpa library
├── labeling2.py / newLabelling.py             # Script utilitas otomatisasi anotasi data
├── data_new.json / titik_tengah*.json         # Koordinat bounding box & metadata anotasi
└── Laporan_IF0202_Firstyatama_Sistem Identifikasi Kontainer Berbasis Warna Menggunakan Algoritma KNN.pdf # Laporan ilmiah lengkap
```

---

## 🚀 Panduan Menjalankan

### 1. Kloning Repositori
```bash
git clone https://github.com/FirstyatamaAuzan/Container-Detector-Use-KNN.git
cd Container-Detector-Use-KNN
```

### 2. Instalasi Dependensi
```bash
pip install opencv-python numpy scikit-learn matplotlib jupyter
```

### 3. Menjalankan Jupyter Notebook
```bash
jupyter notebook KNNTERBARUU.ipynb
```

---

## 📄 Dokumen Laporan Ilmiah
Laporan riset lengkap mencakup kajian pustaka, formulasi matematis, dan pembahasan hasil dapat diakses langsung pada berkas:
👉 **[Laporan_IF0202_Firstyatama_Sistem Identifikasi Kontainer Berbasis Warna Menggunakan Algoritma KNN.pdf](Laporan_IF0202_Firstyatama_Sistem%20Identifikasi%20Kontainer%20Berbasis%20Warna%20Menggunakan%20Algoritma%20KNN.pdf)**

---

## 👤 Penulis
**Firstyatama Auzan Farhadi**  
- LinkedIn: [linkedin.com/in/firstyatama](https://www.linkedin.com/in/firstyatama/)  
- GitHub: [@FirstyatamaAuzan](https://github.com/FirstyatamaAuzan)  
- Institusi: S1 Informatika, Universitas Telkom Surabaya
