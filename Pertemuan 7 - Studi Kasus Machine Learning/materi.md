# Studi Kasus Machine Learning: Regresi, Klasifikasi, dan Klustering

## Pendahuluan
Dalam praktikum ini, kita akan mengeksplorasi penggunaan machine learning untuk melakukan regresi, klasifikasi, dan klustering menggunakan dataset yang tersedia di Kaggle. Studi kasus ini akan mengacu pada metode supervised dan unsupervised learning dengan mencakup regresi untuk prediksi nilai, klasifikasi untuk identifikasi kelompok, dan klustering untuk menemukan pola. Praktikum ini diharapkan dapat memberikan gambaran nyata mengenai penerapan ketiga metode ini.

### Tujuan Pembelajaran
1. **Memahami proses pre-processing dataset sebelum diterapkan pada algoritma machine learning**: Tahapan ini meliputi pembersihan data, penanganan nilai yang hilang, encoding data kategorikal, dan normalisasi data. Pre-processing sangat penting agar data siap untuk digunakan oleh model dan hasil yang diperoleh lebih akurat.

3. **Mengaplikasikan model regresi, klasifikasi, dan klustering menggunakan dataset di Kaggle**: Implementasi model-model ini bertujuan untuk memahami perbedaan metode supervised (regresi dan klasifikasi) dan unsupervised (klustering), serta bagaimana mereka dapat digunakan untuk memecahkan masalah yang berbeda.

5. **Mengimplementasikan teknik evaluasi yang tepat untuk setiap model**: Setiap metode memiliki metrik evaluasi yang berbeda untuk menilai performa model, seperti Mean Squared Error (MSE) untuk regresi, akurasi dan precision-recall untuk klasifikasi, serta silhouette score untuk klustering.

## Dataset
Dataset yang akan digunakan dalam praktikum adalah dataset [Student Performance Factors](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors). Dataset ini berisi data mengenai faktor-faktor yang mempengaruhi performa akademik siswa, seperti jenis kelamin, status sosial ekonomi, waktu belajar, hasil ujian dalam beberapa mata pelajaran, serta dukungan orang tua dan sekolah.

### Deskripsi Dataset

| Atribut                     | Deskripsi                                                                         |
|-----------------------------|-----------------------------------------------------------------------------------|
| **Hours_Studied**           | Jumlah jam belajar per minggu.                                                    |
| **Attendance**              | Persentase kehadiran di kelas.                                                    |
| **Parental_Involvement**    | Tingkat keterlibatan orang tua dalam pendidikan siswa (Rendah, Sedang, Tinggi).   |
| **Access_to_Resources**     | Ketersediaan sumber daya pendidikan (Rendah, Sedang, Tinggi).                     |
| **Extracurricular_Activities** | Partisipasi dalam kegiatan ekstrakurikuler (Ya, Tidak).                     |
| **Sleep_Hours**             | Rata-rata jam tidur per malam.                                                    |
| **Previous_Scores**         | Nilai dari ujian sebelumnya.                                                      |
| **Motivation_Level**        | Tingkat motivasi siswa (Rendah, Sedang, Tinggi).                                  |
| **Internet_Access**         | Ketersediaan akses internet (Ya, Tidak).                                          |
| **Tutoring_Sessions**       | Jumlah sesi les yang diikuti per bulan.                                           |
| **Family_Income**           | Tingkat pendapatan keluarga (Rendah, Sedang, Tinggi).                             |
| **Teacher_Quality**         | Kualitas pengajaran dari guru (Rendah, Sedang, Tinggi).                           |
| **School_Type**             | Jenis sekolah yang dihadiri (Negeri, Swasta).                                     |
| **Peer_Influence**          | Pengaruh teman terhadap performa akademik (Positif, Netral, Negatif).             |
| **Physical_Activity**       | Rata-rata jam aktivitas fisik per minggu.                                         |
| **Learning_Disabilities**   | Adanya disabilitas belajar (Ya, Tidak).                                           |
| **Parental_Education_Level** | Tingkat pendidikan tertinggi orang tua (SMA, Perguruan Tinggi, Pascasarjana).    |
| **Distance_from_Home**      | Jarak dari rumah ke sekolah (Dekat, Sedang, Jauh).                                |
| **Gender**                  | Jenis kelamin siswa (Laki-laki, Perempuan).                                       |
| **Exam_Score**              | Nilai ujian akhir.  


### Langkah Awal
1. **Unduh dataset dari Kaggle dan lakukan import ke dalam environment analisis**
   Setelah dataset diunduh, kita akan menggunakan Python dan library Pandas untuk membaca dan mengelola data. Langkah ini merupakan dasar untuk semua analisis lebih lanjut.
   
3. **Lakukan Exploratory Data Analysis (EDA) untuk memahami distribusi, korelasi, dan karakteristik data**
   EDA bertujuan untuk memberikan wawasan awal tentang bagaimana data didistribusikan, apakah terdapat outlier, dan bagaimana fitur-fitur dalam dataset saling berhubungan. Visualisasi menggunakan heatmap sangat membantu dalam melihat korelasi antar fitur.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Memuat dataset
df = pd.read_csv("student-performance-factors.csv")

# EDA
print(df.head())
print(df.describe())
```

## Regresi: Prediksi Nilai Akhir Siswa
### Persiapan Data
Dalam tugas regresi, kita akan mencoba memprediksi nilai akhir siswa berdasarkan fitur-fitur yang tersedia seperti waktu belajar, latar belakang sosial ekonomi, dukungan orang tua, dan dukungan sekolah. Model regresi akan membantu kita memahami bagaimana variabel input berkontribusi terhadap variabel target (nilai akhir).

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Preprocessing
df.dropna(inplace=True)

# Memilih fitur dan target
X = df.drop(columns=['Exam_Score'])
y = df['Exam_Score']

# Encoding fitur kategorikal
X = pd.get_dummies(X, drop_first=True)

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training model
model = LinearRegression()
model.fit(X_train, y_train)

# Evaluasi
y_pred = model.predict(X_test)
print(f"Mean Squared Error: {mean_squared_error(y_test, y_pred)}")
```

Model regresi linier ini akan menghasilkan prediksi nilai akhir berdasarkan variabel input yang ada. Evaluasi dilakukan menggunakan Mean Squared Error (MSE) yang menunjukkan seberapa jauh prediksi dari nilai sebenarnya. Semakin kecil nilai MSE, semakin baik model dalam memprediksi.

## Klasifikasi: Menentukan Kategori Performa Siswa
### Persiapan Data
Pada bagian ini, kita akan mengubah variabel target menjadi kategori, misalnya "Baik", "Cukup", dan "Kurang" untuk melihat apakah model dapat mengklasifikasikan performa siswa berdasarkan kategori tersebut. Pendekatan klasifikasi ini bermanfaat untuk memberikan label performa siswa secara otomatis berdasarkan fitur yang diberikan.

```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score, classification_report

# Mengubah target menjadi kategori
bins = [0, 50, 70, 100]
labels = ['Kurang', 'Cukup', 'Baik']
df['grade_category'] = pd.cut(df['Exam_Score'], bins=bins, labels=labels)

# Preprocessing
df.dropna(inplace=True)

# Memilih fitur dan target
X = df.drop(columns=['Exam_Score'])
y = df['grade_category']

# Encoding fitur kategorikal
X = pd.get_dummies(X, drop_first=True)

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Training model
classifier = KNeighborsClassifier(n_neighbors=3)
classifier.fit(X_train, y_train)

# Evaluasi
y_pred = classifier.predict(X_test)
print(f"Accuracy: {accuracy_score(y_test, y_pred)}")
print(classification_report(y_test, y_pred))
```

Model K-Nearest Neighbors (KNN) akan memberikan prediksi kategori untuk nilai siswa. Evaluasi dilakukan menggunakan akurasi dan classification report, yang mencakup precision, recall, dan F1-score. Metrik-metrik ini memberikan gambaran menyeluruh tentang kinerja model dalam memprediksi setiap kategori.

## Klustering: Mengelompokkan Siswa Berdasarkan Kesamaan Karakteristik
### Persiapan Data
Dalam tugas ini, kita akan menggunakan metode klustering untuk mengelompokkan siswa berdasarkan karakteristik mereka, misalnya waktu belajar, dukungan sekolah, dukungan orang tua, dan status sosial ekonomi. Teknik klustering ini berguna untuk menemukan kelompok siswa dengan karakteristik serupa tanpa perlu label yang sudah ditentukan.

```python
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

# Memilih fitur
X = df.drop(columns=['Exam_Score'])

# Encoding fitur kategorikal
X = pd.get_dummies(X, drop_first=True)

# Menentukan jumlah cluster optimal menggunakan elbow method
inertia = []
silhouette_scores = []
for n in range(2, 10):
    kmeans = KMeans(n_clusters=n, random_state=0)
    kmeans.fit(X)
    inertia.append(kmeans.inertia_)
    
    # Hitung silhouette score
    score = silhouette_score(X, kmeans.labels_)
    silhouette_scores.append(score)

# Plot elbow method untuk membantu menentukan jumlah klaster yang optimal
plt.figure(figsize=(8, 4))
plt.plot(range(2, 10), inertia, marker='o')
plt.xlabel('Number of Clusters')
plt.ylabel('Inertia')
plt.title('Elbow Method for Optimal Cluster Number')
plt.show()

# Plot silhouette score untuk membantu menentukan jumlah klaster yang optimal
plt.figure(figsize=(8, 4))
plt.plot(range(2, 10), silhouette_scores, marker='o', color='orange')
plt.xlabel('Number of Clusters')
plt.ylabel('Silhouette Score')
plt.title('Silhouette Score for Optimal Cluster Number')
plt.show()

# Pengelompokan menggunakan K-Means dengan jumlah cluster yang telah ditentukan sebelumnya, yaitu 2
optimal_clusters = 2
kmeans = KMeans(n_clusters=optimal_clusters, random_state=0)
kmeans.fit(X)

# Menambahkan hasil kluster ke dalam dataset
df['cluster'] = kmeans.labels_

# Evaluasi akhir dengan silhouette score untuk jumlah cluster yang dipilih
final_silhouette_score = silhouette_score(X, kmeans.labels_)
print(f'Silhouette Score untuk {optimal_clusters} cluster: {final_silhouette_score:.4f}')

# Visualisasi 1: Previous_Scores vs Hours_Studied
plt.figure(figsize=(8, 6))
sns.scatterplot(x='Previous_Scores', y='Hours_Studied', hue='cluster', palette='viridis', data=df)
plt.title('K-Means Clustering: Hours Studied vs. Previous Scores')
plt.xlabel('Previous Scores')
plt.ylabel('Hours Studied')
plt.legend(title='Cluster')
plt.show()
```

Dalam klustering ini, siswa dikelompokkan ke dalam 2 kluster berdasarkan karakteristik mereka. Kluster ini dapat menyoroti hubungan antara Previous_Scores dan Hours_Studied. Visualisasi klustering membantu kita memahami pola yang mungkin ada di dalam data. Misalnya, kita dapat melihat berdasarkan usaha dan performa akademik siswa.

## Evaluasi Model
- **Regresi**: Evaluasi menggunakan Mean Squared Error (MSE) untuk mengukur seberapa baik model dalam memprediksi nilai akhir siswa. MSE menunjukkan rata-rata kesalahan kuadrat antara nilai prediksi dan nilai aktual.
  
- **Klasifikasi**: Evaluasi menggunakan akurasi dan classification report (precision, recall, F1-score) untuk melihat performa model dalam mengkategorikan siswa. Precision mengukur akurasi prediksi positif, recall mengukur kemampuan model untuk menemukan semua contoh positif, dan F1-score merupakan rata-rata harmonik dari precision dan recall.
  
- **Klustering**: Evaluasi dengan menggunakan **Silhouette Score** untuk menentukan seberapa baik siswa dikelompokkan berdasarkan kesamaan karakteristik. Silhouette score berkisar antara -1 hingga 1, di mana nilai yang lebih tinggi menunjukkan bahwa objek berada dalam kluster yang benar. Evaluasi menggunakan silhouette score memberikan gambaran tentang kualitas klustering yang telah dilakukan. Nilai yang tinggi menunjukkan bahwa kluster yang terbentuk memiliki objek-objek yang serupa dan berbeda dari kluster lainnya.

## Kesimpulan
Dalam studi kasus ini, kita telah menerapkan tiga pendekatan machine learning yang berbeda, yaitu regresi untuk prediksi nilai akhir, klasifikasi untuk kategori performa, dan klustering untuk pengelompokan siswa. Setiap metode memiliki proses evaluasi yang spesifik untuk memastikan model yang dibuat dapat digunakan dengan baik dalam skenario nyata. Pemahaman tentang regresi, klasifikasi, dan klustering ini merupakan dasar yang penting untuk melanjutkan studi lebih lanjut dalam machine learning. Pendekatan ini memberikan wawasan tentang bagaimana mengelola data, membangun model, dan mengevaluasi performa model untuk berbagai jenis masalah yang mungkin dihadapi di dunia nyata.
