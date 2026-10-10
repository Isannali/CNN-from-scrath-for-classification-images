# Klasifikasi Gambar Menggunakan CNN dari Awal dengan PyTorch

Proyek klasifikasi gambar menggunakan *Convolutional Neural Network* (CNN) yang dibangun dari awal (*from scratch*) menggunakan PyTorch untuk mengklasifikasikan gambar kartu ke dalam 53 kategori.

Berbeda dengan pendekatan *transfer learning*, model ini menggunakan bobot yang diinisialisasi secara acak tanpa memanfaatkan bobot model pralatih. Proyek ini berfokus pada implementasi arsitektur CNN, ekstraksi fitur visual, pelatihan model, dan inferensi gambar.

## Gambaran Proyek

Proyek ini mencakup alur pengembangan model klasifikasi gambar, mulai dari persiapan dataset dan prapemrosesan gambar hingga pembangunan arsitektur CNN, pelatihan, validasi, inferensi, dan ekspor model.

## Teknologi yang Digunakan

- **Bahasa Pemrograman:** Python
- **Framework Deep Learning:** PyTorch
- **Computer Vision:** Torchvision, Pillow
- **Pengolahan Data:** NumPy
- **Visualisasi:** Matplotlib
- **Pemantauan Pelatihan:** tqdm
- **Ekspor Model:** ONNX

## Dataset

- **Nama:** Cards Image Dataset Classification
- **Sumber:** [Kaggle](https://www.kaggle.com/datasets/gpiosenka/cards-image-datasetclassification)
- **Jenis Tugas:** Klasifikasi gambar multikelas
- **Jumlah Kelas:** 53
- **Pembagian Data:** Training, validation, dan testing

Dataset diunduh menggunakan KaggleHub dan dimuat menggunakan `ImageFolder` dari PyTorch.

## Arsitektur Model

Arsitektur CNN dibangun menggunakan `torch.nn.Module` dengan komponen berikut:

1. **Blok Konvolusi 1:** 3 kanal input menjadi 64 kanal output, dilanjutkan aktivasi ReLU dan *max pooling*.
2. **Blok Konvolusi 2:** 64 menjadi 256 kanal, dilanjutkan aktivasi ReLU dan *max pooling*.
3. **Blok Konvolusi 3:** 256 menjadi 1024 kanal, dilanjutkan aktivasi ReLU dan *max pooling*.
4. **Lapisan Klasifikasi:** Fitur hasil ekstraksi diratakan (*flatten*) dan diteruskan ke lapisan *fully connected* dengan 2048, 512, dan 53 unit output.
5. **Regularisasi:** Menggunakan *dropout* dengan probabilitas 0,5 pada lapisan *fully connected*.

Seluruh bobot model diinisialisasi secara acak tanpa menggunakan bobot pralatih.

## Konfigurasi Pelatihan

| Parameter | Konfigurasi |
|---|---|
| Ukuran gambar input | 128 × 128 piksel |
| Ukuran batch | 32 |
| Jumlah epoch | 10 |
| Optimizer | Adam |
| Learning rate | 0,001 |
| Fungsi loss | Cross-Entropy Loss |
| Perangkat komputasi | GPU CUDA jika tersedia, jika tidak menggunakan CPU |

Model dilatih menggunakan pendekatan *mini-batch gradient descent*. Nilai *training loss* dan *validation loss* dicatat pada setiap epoch untuk memantau proses pembelajaran model.

## Evaluasi dan Inferensi

Notebook mencakup beberapa proses berikut:

- Visualisasi *training loss* dan *validation loss*.
- Inferensi pada satu gambar menggunakan model yang telah dilatih.
- Perhitungan probabilitas prediksi menggunakan Softmax.
- Visualisasi gambar input, kategori kartu hasil prediksi, dan tingkat keyakinan prediksi.

Notebook belum menghitung metrik evaluasi keseluruhan pada data pengujian, seperti akurasi, precision, recall, dan F1-score.

## Ekspor Model

Model dapat disimpan dalam format berikut:

- `model_kartu.pth` — bobot model PyTorch.
- `model_kartu.onnx` — representasi model dalam format ONNX untuk digunakan pada lingkungan inferensi yang kompatibel.

## Cara Menjalankan

1. Buka notebook `CNN from scrath for classification image.ipynb` menggunakan Google Colab atau Jupyter Notebook.
2. Instal dependensi yang diperlukan.
3. Jalankan sel notebook secara berurutan untuk mengunduh dataset dan menyiapkan data loader.
4. Jalankan proses pelatihan CNN dan pantau perubahan loss selama training dan validation.
5. Jalankan sel inferensi untuk menguji prediksi pada gambar.
6. Jalankan proses ekspor untuk menyimpan model dalam format PyTorch dan ONNX.

Penggunaan GPU disarankan untuk mempercepat proses pelatihan.

## Pengembangan Selanjutnya

- Menambahkan evaluasi menggunakan accuracy, precision, recall, F1-score, dan confusion matrix.
- Menerapkan augmentasi data dan regularisasi tambahan untuk meningkatkan kemampuan generalisasi.
- Membandingkan arsitektur CNN dan konfigurasi hiperparameter yang berbeda.
- Mengintegrasikan model ONNX ke dalam aplikasi inferensi.

## Hasil Pembelajaran

Melalui proyek ini, beberapa kemampuan teknis yang dipraktikkan meliputi:

- Membangun arsitektur CNN dari awal menggunakan PyTorch.
- Memahami proses konvolusi, pooling, dan ekstraksi fitur visual.
- Mengimplementasikan alur pelatihan dan validasi model.
- Melakukan inferensi untuk klasifikasi gambar.
- Mengekspor model untuk digunakan pada lingkungan inferensi yang kompatibel.