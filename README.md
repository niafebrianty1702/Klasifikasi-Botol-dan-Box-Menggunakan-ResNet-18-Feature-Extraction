# Klasifikasi-Botol-dan-Box-Menggunakan-ResNet-18-Feature-Extraction
Image classification using ResNet18 and PyTorch
# Klasifikasi Botol dan Box Menggunakan ResNet-18 Feature Extraction

## 1. Deskripsi

Proyek ini merupakan implementasi klasifikasi citra untuk membedakan dua kelas objek, yaitu **botol** dan **box**, menggunakan model **ResNet-18** sebagai feature extractor.

Model ResNet-18 menggunakan bobot pretrained dan bagian feature extraction dibekukan selama proses training. Hanya bagian classifier yang dilatih untuk menyesuaikan model dengan dua kelas pada dataset.

## 2. Dataset

Dataset terdiri dari dua kelas:

- Botol
- Box

Dataset dibagi menjadi data training dan validation.

| Split | Botol | Box | Total |
|---|---:|---:|---:|
| Train | 40 | 40 | 80 |
| Validation | 10 | 10 | 20 |
| Total | 50 | 50 | 100 |

Metadata dataset disimpan dalam file `metadata.csv`.

## 3. Model

Model yang digunakan adalah ResNet-18 pretrained.

Arsitektur secara umum:

```text
Input Image
     ↓
Resize 224 × 224
     ↓
ResNet-18 Feature Extractor
     ↓
512-dimensional Feature
     ↓
Linear Classifier
     ↓
Botol / Box
```

Parameter pada feature extractor ResNet-18 dibekukan, sedangkan classifier dilatih menggunakan dataset yang tersedia.

## 4. Training

Training dilakukan menggunakan optimizer Adam dan loss function Cross Entropy Loss.

Jumlah epoch, learning rate, dan batch size dicantumkan berdasarkan konfigurasi yang digunakan pada notebook Google Colab.

Grafik training accuracy dan validation accuracy digunakan untuk melihat perubahan performa model selama proses training.

## 5. Hasil Evaluasi

Hasil akhir dievaluasi menggunakan validation dataset.

Metrik yang digunakan meliputi:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

Nilai akhir dimasukkan berdasarkan hasil eksperimen pada Google Colab.

## 6. Latensi

Latensi model diukur menggunakan waktu rata-rata inference ResNet-18 terhadap input berukuran 224 × 224 piksel.

Hasil pengukuran:

```text
Average Latency : [ISI HASIL COLAB] ms
Estimated FPS   : [ISI HASIL COLAB] FPS
```

Pengukuran dilakukan setelah beberapa proses warm-up untuk memperoleh waktu inference yang lebih stabil.

## 7. Analisis

Berdasarkan hasil training, perubahan accuracy per epoch digunakan untuk melihat kemampuan model dalam mempelajari karakteristik kedua kelas. Perbandingan training accuracy dan validation accuracy dapat digunakan untuk melihat apakah model mengalami peningkatan performa yang konsisten atau terdapat indikasi overfitting.

Penggunaan ResNet-18 sebagai feature extractor mengurangi jumlah parameter yang perlu dilatih karena bobot feature extractor tidak diperbarui selama training. Pendekatan ini juga memanfaatkan feature yang telah dipelajari dari dataset ImageNet.

Latensi menjadi parameter tambahan yang penting karena model tidak hanya perlu menghasilkan prediksi yang benar, tetapi juga perlu memberikan hasil inference dalam waktu yang sesuai dengan kebutuhan aplikasi.

## 8. Kesimpulan

ResNet-18 feature extraction digunakan untuk melakukan klasifikasi dua kelas objek, yaitu botol dan box. Evaluasi dilakukan menggunakan accuracy, precision, recall, F1-score, confusion matrix, serta pengukuran latensi inference.

Hasil akhir performa model ditentukan berdasarkan eksperimen yang dilakukan pada Google Colab menggunakan dataset yang telah disediakan.
