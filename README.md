
# 🤖 Proyek Capstone NLP: Analisis Sentimen Ulasan Aplikasi Gojek

Proyek ini bertujuan untuk mengembangkan model Deep Learning (IndoBERT) untuk mengklasifikasikan sentimen pengguna (Negatif, Netral, Positif) pada ulasan Gojek di Google Play Store.

| Detail Proyek | Keterangan |
| :--- | :--- |
| **Topik Analisis** | Ulasan Pengguna Aplikasi Gojek |
| **Kelas Sentimen** | 3 Kelas (Negatif, Netral, Positif) |
| **Target Akurasi** | **≥ 92% pada Testing Set** |
| **Metodologi Utama** | IndoBERT Fine-Tuning |

## 2. Metodologi dan Pipeline

Kami mengikuti pipeline ML yang ketat: Scraping → Preprocessing → Data Splitting (80/10/10) → Modeling.

### Eksperimen Modeling (3 Skema)

Untuk mencapai target 92%, kami menguji tiga skema berbeda:

| Eksperimen | Fitur Ekstraksi | Model | Akurasi Tercapai (Val Set) | Keterangan |
| :--- | :--- | :--- | :--- | :--- |
| **1. Baseline** | TF-IDF (1-2 gram) | LinearSVC | [88.15%] | Baseline cepat, performa bagus pada kelas mayoritas. |
| **2. Embedding** | Word2Vec (Gensim) | XGBoost | [87.75%] | Eksperimen dengan representasi vektor padat. |
| **3. Transformer** | IndoBERT Tokenizer | **IndoBERT Fine-Tuning** | [89.50% - 89.80%] | Upaya terbaik menggunakan model SOTA. |

---

## 3. Hasil & Evaluasi Akhir (Wajib Lapor)

Model yang dipilih untuk evaluasi akhir adalah **IndoBERT Fine-Tuning** yang dilatih dengan [3] Epoch .

### A. Akurasi Final (Testing Set)

| Metrik | Hasil (Validation Set) | **Hasil Akhir (TEST SET)** |
| :--- | :--- | :--- |
| **Akurasi** | [89.50%] | **[Akurasi Test Set]** |
| **F1 Macro** | [0.59(val set)] | **[...]** |

### B. Analisis Keterbatasan (Penting untuk Reviewer)

Meskipun kami berhasil mencapai akurasi [89.50%] pada Validation Set, target 92% gagal dicapai karena:

1.  **Class Imbalance:** Kelas 'Netral' hanya memiliki **~5%** dari total sampel. Model sangat kesulitan memprediksi kelas minoritas ini (F1-score Netral pada baseline sangat rendah: 0.07).
2.  **Overfitting Cepat:** Model IndoBERT menunjukkan tanda-tanda *overfitting* setelah Epoch 1, yang membatasi kemampuan *tuning* lebih lanjut.

---

## 4. Struktur File dan Etika

### A. Deliverables (File yang Dilampirkan)

Semua file berikut dikumpulkan dalam folder **submission_project.zip**:

* `experiment_bert.ipynb`: Semua 3 eksperimen modeling dan evaluasi akhir.
* `scraper.ipynb` (atau `.py`): Kode pengambilan data.
* `dataset_clean.csv`: Data bersih dan terlabel.
* `requirements.txt`: Daftar dependensi.
* `inference_demo.ipynb` (Opsional): Demonstrasi prediksi model.
* `README.md`: Dokumen ini.

### B. Catatan Etika Data

Data diambil dari halaman publik Google Play Store. Informasi pribadi telah dihapus, dan data digunakan secara ketat untuk tujuan akademik dan non-komersial.
