# Palm-Recognition-Model
Repositori ini berisi kode dan alur kerja untuk membangun sebuah prototipe sistem pengenalan telapak tangan (palmprint recognition) dari awal hingga akhir. Proyek ini mencakup dua pendekatan utama: metode Computer Vision Klasik dan metode Deep Learning menggunakan Convolutional Neural Network (CNN).
-----------------
📜 Deskripsi
Proyek ini bertujuan untuk mengidentifikasi seseorang berdasarkan citra telapak tangannya. Proses ini melibatkan beberapa tahap, mulai dari pra-pemrosesan gambar mentah untuk mengisolasi area telapak tangan (Region of Interest - ROI), mengekstraksi fitur unik, hingga melatih model klasifikasi untuk mengenali identitas subjek.
-----------------
📊 Dataset
Dataset yang digunakan dalam proyek ini adalah Sapienza University Mobile Palmprint Database (SMPD). Dataset ini berisi koleksi citra telapak tangan dari 110 subjek yang diambil menggunakan smartphone dengan berbagai variasi rotasi dan perspektif, sehingga sangat cocok untuk melatih model yang tangguh.
Sumber: Kaggle - SMPD Dataset
-----------------
🛠️ Teknologi & Library
Proyek ini dibangun menggunakan Python dengan beberapa library utama:
* TensorFlow & Keras: Untuk membangun dan melatih model Convolutional Neural Network (CNN).
* OpenCV: Untuk semua tugas pemrosesan gambar (pra-pemrosesan, deteksi kontur, ekstraksi ROI).
* Scikit-learn: Untuk membagi dataset menjadi data latih dan data uji.
* Scikit-image: Untuk ekstraksi fitur Local Binary Patterns (LBP).
* NumPy: Untuk operasi numerik dan manipulasi array.
* Matplotlib: Untuk visualisasi gambar dan plot hasil training.
* Jupyter Notebook / Google Colab: Sebagai lingkungan pengembangan interaktif.
* Kaggle API: Untuk mengunduh dataset.
-----------------
⚙️ Alur Kerja (Workflow)
Proyek ini mengikuti alur kerja sistematis yang dibagi menjadi dua tahap utama: preprocessing dan pemodelan.

Tahap 1: Pra-pemrosesan (Preprocessing)
Tujuan dari tahap ini adalah untuk mengubah gambar telapak tangan mentah menjadi gambar ROI (Region of Interest) yang bersih, berukuran seragam (256x256), dan siap untuk dianalisis.

Binarisasi: Memisahkan telapak tangan dari latar belakang menggunakan Gaussian Blur dan Otsu's Thresholding.

Deteksi Kontur: Menemukan garis tepi dari bentuk telapak tangan.

Deteksi Titik Kunci: Menggunakan Convex Hull dan Convexity Defects untuk menemukan lembah antar jari sebagai titik acuan.

Ekstraksi ROI: Melakukan rotasi dan pemotongan (cropping) gambar berdasarkan titik kunci untuk menghasilkan ROI yang konsisten.

Tahap 2: Pemodelan (Pendekatan Deep Learning)
Persiapan Data:

Menjalankan pipeline preprocessing untuk semua gambar di dataset.

Menyimpan hasil ROI yang bersih ke penyimpanan permanen (Google Drive) untuk menghindari masalah RAM.

Memuat data ROI yang sudah diproses secara efisien menggunakan tf.keras.utils.image_dataset_from_directory.

Membangun Model CNN:

Merancang arsitektur CNN yang efisien dengan beberapa lapisan Conv2D, MaxPooling2D, dan GlobalAveragePooling2D untuk mencegah overfitting dan mengurangi jumlah parameter.

Training & Evaluasi:

Melatih model menggunakan data latih dan mengevaluasi performanya pada data validasi.

Menganalisis kurva akurasi dan loss untuk memahami dinamika training.
