# Klasterisasi

## Outline
- [Definisi Klasterisasi](#definisi-klasterisasi)
- [Kasus yang Dapat Diselesaikan dengan Klasterisasi](#kasus-yang-dapat-diselesaikan-dengan-klasterisasi)
- [Tipe Klasterisasi](#tipe-klasterisasi)
- [Teknik Setiap Tipe Klasterisasi](#teknik-setiap-tipe-klasterisasi)
- [Penjelasan K-means dan Implementasinya](#penjelasan-k-means-dan-implementasinya)
- [Penjelasan DBScan dan Implementasinya](#penjelasan-dbscan-dan-implementasinya)
- [Perbandingan K-means dan DBScan](#perbandingan-k-means-dan-dbscan)
- [Metrik Evaluasi](#metrik-evaluasi)

---

## Definisi Klasterisasi

Klasterisasi adalah teknik dalam pembelajaran mesin yang bertujuan untuk mengelompokkan data ke dalam kelompok-kelompok (klaster) berdasarkan karakteristik yang mirip di antara data-data tersebut. Dalam klasterisasi, data yang berada dalam satu kelompok memiliki kemiripan yang tinggi satu sama lain dibandingkan dengan data di kelompok lain.

## Kasus yang Dapat Diselesaikan dengan Klasterisasi

Beberapa contoh kasus yang dapat diselesaikan dengan klasterisasi antara lain:
- **Segmentasi Pelanggan**: Mengelompokkan pelanggan berdasarkan pola pembelian mereka untuk rekomendasi produk.
- **Analisis Sosial Media**: Mengelompokkan postingan atau pengguna berdasarkan tema/topik atau perilaku pengguna.
- **Pengenalan Pola dalam Data Medis**: Mengidentifikasi kelompok pasien dengan karakteristik kesehatan serupa.
- **Pengelompokan Dokumen**: Mengelompokkan artikel atau dokumen berdasarkan topik yang serupa.

## Tipe Klasterisasi

Klasterisasi dapat dibagi menjadi beberapa tipe utama:
1. **Klasterisasi Berbasis Partisi**: Mengelompokkan data ke dalam klaster berdasarkan partisi atau pembagian, contohnya metode K-means.
2. **Klasterisasi Berbasis Hirarki**: Mengelompokkan data dalam struktur hierarki seperti pohon, contohnya Agglomerative dan Divisive Clustering.
3. **Klasterisasi Berbasis Kerapatan**: Mengelompokkan data berdasarkan kerapatan (density) di area tertentu, contohnya metode DBScan.
4. **Klasterisasi Berbasis Model**: Menggunakan model statistik untuk menentukan klaster data, contohnya Gaussian Mixture Model (GMM).

## Teknik Setiap Tipe Klasterisasi

Berikut teknik yang digunakan untuk setiap tipe klasterisasi:

- **Klasterisasi Berbasis Partisi**: Menggunakan algoritma seperti **K-means** yang menentukan jumlah klaster dan mempartisi data ke dalam klaster dengan cara iteratif.
- **Klasterisasi Berbasis Hirarki**: Menggunakan pendekatan seperti **Agglomerative Clustering** (penggabungan data) atau **Divisive Clustering** (pemisahan data).
- **Klasterisasi Berbasis Kerapatan**: Menggunakan algoritma seperti **DBScan** yang mengelompokkan data berdasarkan kerapatan, sangat efektif untuk data dengan bentuk yang tidak teratur.
- **Klasterisasi Berbasis Model**: Menggunakan **Gaussian Mixture Model (GMM)** untuk memodelkan data dan menentukan klaster yang sesuai.

## Penjelasan K-means dan Implementasinya

### Penjelasan K-means
![{C594236B-3449-4266-9394-9BCAFB367656}](https://github.com/user-attachments/assets/a624eab3-e143-4fbe-94d3-8f28d3c32851)
K-means adalah algoritma klasterisasi berbasis partisi yang mencoba membagi data menjadi \( K \) klaster yang ditentukan sebelumnya. Algoritma ini bekerja dengan menentukan centroid (pusat klaster) dan memperbaruinya secara iteratif hingga mencapai konvergensi. Langkah-langkah utama K-means:
1. Pilih jumlah klaster, \( K \).
2. Inisialisasi centroid secara acak.
3. Kelompokkan data ke centroid terdekat.
4. Perbarui centroid berdasarkan rata-rata data pada setiap klaster.
5. Ulangi langkah 3 dan 4 hingga centroid tidak berubah (konvergen).

### Implementasi K-means

```python
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt
import numpy as np

# Contoh data
X = np.array([[1, 2], [1, 4], [1, 0],
              [10, 2], [10, 4], [10, 0]])

# Membuat model K-means
kmeans = KMeans(n_clusters=2, random_state=0)
kmeans.fit(X)

# Hasil klasterisasi
print("Labels:", kmeans.labels_)
print("Centroid:", kmeans.cluster_centers_)

# Visualisasi
plt.scatter(X[:, 0], X[:, 1], c=kmeans.labels_, cmap='viridis')
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1], s=300, c='red')
plt.title("K-means Clustering")
plt.show()
```

Untuk menentukan jumlah klaster \( K \) yang optimal dalam algoritma K-means, salah satu metode yang populer adalah **Elbow Method**. Metode ini bekerja dengan menghitung **inertia** (jumlah kuadrat jarak data dalam klaster ke centroid) untuk berbagai nilai \( K \), kemudian memilih nilai \( K \) pada titik “siku” (elbow), yaitu titik di mana penurunan inertia mulai melambat. Titik elbow menunjukkan jumlah klaster optimal, karena menambahkan klaster baru setelah titik ini hanya memberikan sedikit peningkatan dalam pengelompokan data.

### Langkah-langkah Elbow Method:
1. Jalankan algoritma K-means untuk berbagai nilai \( K \) (misalnya dari 1 hingga 10).
2. Hitung inertia untuk setiap nilai \( K \).
3. Plot nilai inertia sebagai fungsi dari \( K \).
4. Pilih nilai \( K \) di mana terdapat penurunan inertia yang signifikan (titik elbow).

### Implementasi Elbow Method dalam Python

Berikut adalah implementasi Elbow Method untuk menentukan jumlah klaster optimal pada K-means:

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs
from sklearn.metrics import silhouette_score

# Step 1: Membuat dataset simulasi
X, y_true = make_blobs(n_samples=300, centers=4, cluster_std=0.6, random_state=42)

# Step 2: Menentukan jumlah klaster optimal menggunakan Elbow Method
inertias = []
K_values = range(2, 11)  # Nilai K dari 2 hingga 10

for k in K_values:
    kmeans = KMeans(n_clusters=k, random_state=42)
    kmeans.fit(X)
    inertias.append(kmeans.inertia_)

# Plot Elbow Method
plt.figure(figsize=(8, 5))
plt.plot(K_values, inertias, 'bo-', markersize=8)
plt.xlabel('Number of Clusters, K')
plt.ylabel('Inertia (Sum of Squared Distances)')
plt.title('Elbow Method for Optimal K')
plt.grid(True)
plt.show()
```

```python
# Step 3: Mengevaluasi hasil klasterisasi menggunakan Silhouette Score
silhouette_scores = []

for k in K_values:
    kmeans = KMeans(n_clusters=k, random_state=42)
    labels = kmeans.fit_predict(X)
    score = silhouette_score(X, labels)
    silhouette_scores.append(score)

# Plot Silhouette Score
plt.figure(figsize=(8, 5))
plt.plot(K_values, silhouette_scores, 'ro-', markersize=8)
plt.xlabel('Number of Clusters, K')
plt.ylabel('Silhouette Score')
plt.title('Silhouette Score for Various K')
plt.grid(True)
plt.show()

for i in silhouette_scores:
  print(i)
```
```python
# Step 4: Melakukan klasterisasi dengan K optimal
kmeans_optimal = KMeans(n_clusters=optimal_k, random_state=42)
labels_optimal = kmeans_optimal.fit_predict(X)

# Visualisasi hasil klasterisasi
plt.figure(figsize=(8, 5))
plt.scatter(X[:, 0], X[:, 1], c=labels_optimal, cmap='viridis', s=50, alpha=0.7)
plt.scatter(kmeans_optimal.cluster_centers_[:, 0], kmeans_optimal.cluster_centers_[:, 1], s=300, c='red', marker='X')
plt.title(f"K-means Clustering with Optimal K = {optimal_k}")
plt.xlabel("Feature 1")
plt.ylabel("Feature 2")
plt.grid(True)
plt.show()
```
Pada plot yang dihasilkan, titik di mana penurunan inertia mulai melambat adalah titik elbow, yang menunjukkan jumlah klaster optimal \( K \).
Berikut adalah implementasi sederhana K-means dalam Python menggunakan `sklearn`:



## Penjelasan DBScan dan Implementasinya

### Penjelasan DBScan
![{62E8D65E-2AD7-43F0-A625-BC756C1B2B07}](https://github.com/user-attachments/assets/25866214-0e21-4880-8350-d6c4fdcde549)
DBScan (Density-Based Spatial Clustering of Applications with Noise) adalah algoritma klasterisasi berbasis kerapatan yang mengelompokkan titik data dengan mempertimbangkan kerapatan titik di sekitarnya. Algoritma ini efektif untuk mendeteksi klaster dengan bentuk yang tidak beraturan dan dapat mengidentifikasi noise (data yang tidak termasuk dalam klaster mana pun).

Langkah-langkah DBScan:
1. Tentukan parameter **epsilon (ε)** sebagai radius kerapatan dan **minPts** sebagai jumlah minimum titik untuk membentuk klaster.
2. Mulai dari titik yang belum dikunjungi, dan tandai titik yang memiliki cukup titik tetangga (berdasarkan ε dan minPts) sebagai klaster.
3. Tambahkan titik yang memenuhi syarat ke klaster, dan lanjutkan hingga tidak ada lagi titik yang memenuhi syarat untuk klaster tersebut.
4. Data yang tidak masuk ke klaster dianggap sebagai noise.

![{1D4D44D5-2B50-4352-A7FB-77C386B21FAE}](https://github.com/user-attachments/assets/71022b03-f4d8-40e7-888e-4c0be7dfe3b3)

- **epsilon (eps)**: Nilai jarak maksimum antara dua titik untuk satu dianggap tetangga dari yang lain.
- **Minimum Points (MinPts)**: Jumlah minimum titik tetangga yang diperlukan agar suatu titik dianggap sebagai inti (core point).

### Implementasi DBScan

Implementasi sederhana DBScan dalam Python menggunakan `sklearn`:

```python
from sklearn.cluster import DBSCAN
import numpy as np
import matplotlib.pyplot as plt

# Contoh data
X = np.array([[1, 2], [2, 2], [2, 3], 
              [8, 7], [8, 8], [25, 80]])

# Membuat model DBScan
dbscan = DBSCAN(eps=3, min_samples=2)
dbscan.fit(X)

# Hasil klasterisasi
print("Labels:", dbscan.labels_)

# Visualisasi
plt.scatter(X[:, 0], X[:, 1], c=dbscan.labels_, cmap='plasma')
plt.title("DBScan Clustering")
plt.show()
```

## Perbandingan K-means dan DBScan

| Algoritma | K-means | DBScan |
|-----------|---------|--------|
| **Kebutuhan Parameter** | Harus menentukan jumlah klaster \( K \) | Hanya perlu epsilon dan minPts |
| **Bentuk Klaster** | Cocok untuk klaster berbentuk bulat atau simetris | Cocok untuk klaster dengan bentuk yang tidak beraturan |
| **Mengatasi Noise** | Tidak dapat mengidentifikasi noise | Mampu mengidentifikasi noise |
| **Skalabilitas** | Cenderung cepat pada data besar | Efektif untuk data besar tetapi tergantung pada nilai parameter |
| **Konvergensi** | Tergantung pada inisialisasi centroid | Tidak memerlukan konvergensi iteratif |

## Kelebihan dan Kekurangan

**K-means:**
- **Kelebihan**:
  - Mudah dan cepat untuk diimplementasikan.
  - Efektif untuk data dengan klaster yang berbentuk bulat atau simetris.
- **Kekurangan**:
  - Tidak efektif untuk bentuk klaster yang tidak beraturan.
  - Sulit menentukan jumlah klaster yang optimal.
  - Sensitif terhadap outlier.

**DBScan:**
- **Kelebihan**:
  - Mampu mendeteksi noise dan klaster yang tidak beraturan.
  - Tidak memerlukan jumlah klaster yang ditentukan sebelumnya.
- **Kekurangan**:
  - Pemilihan parameter epsilon dan minPts cukup sulit dan dapat memengaruhi hasil.
  - Kurang efektif untuk data dengan kepadatan yang bervariasi atau data berdimensi tinggi.

## Metrik Evaluasi

Beberapa metrik yang digunakan untuk mengevaluasi hasil klasterisasi antara lain:
- **Inertia (Sum of Squared Distances)**: Ukuran seberapa kompak klaster; semakin kecil nilai inertia, semakin baik klaster.
- **Silhouette Score**: Mengukur seberapa mirip data dalam satu klaster dan berbeda dengan klaster lain; skor antara -1 hingga 1, semakin mendekati 1 semakin baik.
- **Adjusted Rand Index (ARI)**: Mengukur kemiripan antara klaster yang dihasilkan dengan klaster yang sebenarnya, dengan memperhitungkan faktor acak.
- **Davies-Bouldin Index**: Ukuran rata-rata jarak antara klaster; semakin rendah nilainya, semakin baik klaster.

### Implementasi Metrik Evaluasi



Berikut adalah contoh implementasi metrik evaluasi untuk K-means dan DBScan dalam Python menggunakan `sklearn`:

```python
from sklearn.metrics import silhouette_score, davies_bouldin_score, adjusted_rand_score
from sklearn.datasets import make_blobs

# Membuat data contoh
X, y_true = make_blobs(n_samples=300, centers=4, cluster_std=0.6, random_state=0)

# K-means
kmeans = KMeans(n_clusters=4)
kmeans_labels = kmeans.fit_predict(X)

# DBScan
dbscan = DBSCAN(eps=0.8, min_samples=5)
dbscan_labels = dbscan.fit_predict(X)

# Metrik Evaluasi K-means
print("K-means Silhouette Score:", silhouette_score(X, kmeans_labels))
print("K-means Davies-Bouldin Index:", davies_bouldin_score(X, kmeans_labels))
print("K-means Adjusted Rand Index:", adjusted_rand_score(y_true, kmeans_labels))

# Metrik Evaluasi DBScan
print("DBScan Silhouette Score:", silhouette_score(X, dbscan_labels))
print("DBScan Davies-Bouldin Index:", davies_bouldin_score(X, dbscan_labels))
print("DBScan Adjusted Rand Index:", adjusted_rand_score(y_true, dbscan_labels))
```

--- 
