# Classification (Klasifikasi)

**Klasifikasi** adalah jenis supervised learning di mana model dilatih menggunakan data berlabel untuk memprediksi label kategori dari data baru. Model klasifikasi mencoba untuk mempelajari hubungan antara variabel fitur (input) dan label kelas (output). Contoh masalah klasifikasi meliputi:
- Mendeteksi apakah suatu email adalah spam atau tidak (binary classification).
- Memprediksi apakah seorang pasien menderita penyakit tertentu berdasarkan data medis (binary classification).
- Mengidentifikasi objek pada gambar seperti kucing, anjing, mobil, dsb. (multi-class classification).

#### **Supervised Learning**
Pada supervised learning, kita memiliki dataset yang terdiri dari pasangan input-output. Model dilatih untuk mempelajari hubungan antara input dan output tersebut sehingga dapat memprediksi output yang benar untuk data baru.

#### **Klasifikasi vs. Regresi**
Klasifikasi berbeda dari regresi. Pada regresi, kita memprediksi nilai kontinu (seperti harga rumah), sedangkan pada klasifikasi, kita memprediksi label diskrit (seperti kelas "spam" atau "not spam").

---
### **Konsep Split Train Test Data**

![image](https://github.com/user-attachments/assets/042be594-570a-4a1d-a953-dcc7472eb730)

**Train-test split** adalah teknik evaluasi dasar di mana dataset dibagi menjadi dua subset:
- **Training set**: Data yang digunakan untuk melatih model.
- **Test set**: Data yang digunakan untuk mengevaluasi model setelah dilatih.

Contoh pembagian umum adalah 80% data untuk pelatihan dan 20% untuk pengujian. Model dilatih menggunakan training set, lalu diuji pada test set untuk melihat seberapa baik model tersebut dapat menggeneralisasi pada data baru.

```python
from sklearn.model_selection import train_test_split

# Membagi dataset menjadi train dan test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```
---
### **Algoritma Klasifikasi Populer**

Dalam dunia machine learning, ada banyak algoritma yang bisa digunakan untuk klasifikasi. Tiga algoritma yang populer dan sering digunakan adalah:
1. **K-Nearest Neighbors (KNN)**
2. **Naive Bayes**
3. **Support Vector Machine (SVM)**

Setiap algoritma ini memiliki keunggulan dan kekurangan yang berbeda, tergantung pada jenis masalah dan data yang dihadapi.

---

### **K-Nearest Neighbors (KNN)**

#### **Konsep KNN**
**K-Nearest Neighbors (KNN)** adalah algoritma non-parametrik yang sangat sederhana namun efektif untuk masalah klasifikasi dan regresi. Algoritma ini bekerja berdasarkan prinsip bahwa objek yang mirip cenderung berada dekat satu sama lain di ruang fitur. Untuk klasifikasi, KNN memprediksi kelas dari data baru dengan melihat *K* tetangga terdekat dari data tersebut dalam ruang fitur.

![image](https://github.com/user-attachments/assets/bcdf3051-58d9-4191-b263-c1a2662b2c08)


#### **Cara Kerja KNN**:
1. **Memilih K**: Tentukan jumlah tetangga terdekat *K* yang akan diperiksa. Nilai *K* yang kecil (misalnya 1) cenderung membuat model terlalu sensitif terhadap noise, sedangkan nilai *K* yang besar bisa membuat prediksi kurang akurat.
2. **Menghitung Jarak**: Gunakan metrik jarak seperti **Euclidean distance** untuk menghitung jarak antara data baru dan setiap data dalam dataset.
   - **Euclidean distance** antara dua titik $$A = (x_1, y_1)$$ dan $$B = (x_2, y_2)$$ di ruang 2D dihitung sebagai:
   
   $$d(A,B) = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$
   
   Dalam kasus ruang berdimensi tinggi, rumusnya diperluas untuk lebih dari dua fitur.
4. **Menentukan K Tetangga Terdekat**: Ambil **K** data dengan jarak terdekat.
5. **Voting Kelas Mayoritas**: Prediksi kelas dari data baru berdasarkan kelas mayoritas dari tetangga terdekatnya. Jika ada dua kelas atau lebih yang memiliki jumlah tetangga yang sama, pilih secara acak atau gunakan strategi lain (misalnya, jarak rata-rata dari tetangga terdekat).

#### **Kelebihan KNN**:
- **Sederhana**: Tidak memerlukan pelatihan model yang kompleks, hanya menyimpan data dan menghitung jarak.
- **Non-parametrik**: Tidak membuat asumsi tentang distribusi data.

#### **Kekurangan KNN**:
- **Lambat**: Harus menghitung jarak dengan setiap data dalam dataset, yang menjadi tidak efisien untuk dataset besar.
- **Tidak Efektif pada Dimensi Tinggi**: Dalam dataset dengan banyak fitur, jarak antara titik-titik cenderung homogen, sehingga sulit untuk menemukan tetangga yang benar-benar relevan.
- **Sensitif terhadap Skala Fitur**: Fitur dengan skala besar bisa mendominasi perhitungan jarak. Oleh karena itu, normalisasi atau standardisasi data biasanya diperlukan.

#### **Contoh Implementasi KNN di Python:**

```python
# Import library
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score
from sklearn.datasets import load_iris

# Load dataset iris
data = load_iris()
X = data.data
y = data.target

# Split data menjadi training dan testing set (80% training, 20% testing)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Inisialisasi model KNN dengan k=3
knn = KNeighborsClassifier(n_neighbors=3)

# Train model dengan data training
knn.fit(X_train, y_train)

# Lakukan prediksi pada data testing
y_pred = knn.predict(X_test)

# Evaluasi akurasi model
accuracy = accuracy_score(y_test, y_pred)
print(f"Akurasi KNN: {accuracy * 100:.2f}%")
```

Dalam contoh di atas, kita menggunakan dataset Iris, di mana model KNN dilatih untuk mengklasifikasikan spesies bunga berdasarkan panjang dan lebar sepal serta petal.

---

### **Naive Bayes**

#### **Konsep Naive Bayes**
**Naive Bayes** adalah algoritma berbasis probabilistik yang didasarkan pada **Teorema Bayes**. Algoritma ini mengasumsikan bahwa semua fitur bersifat independen satu sama lain (asumsi naive). Teorema Bayes menghitung probabilitas suatu kelas diberikan fitur-fitur tertentu.

Teorema Bayes:

$$P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)}$$

Di mana:
- \( P(C | X) \) adalah probabilitas kelas \( C \) diberikan fitur \( X \).
- \( P(X | C) \) adalah probabilitas fitur \( X \) diberikan kelas \( C \).
- \( P(C) \) adalah probabilitas a priori dari kelas \( C \) (probabilitas awal tanpa mempertimbangkan fitur).
- \( P(X) \) adalah probabilitas fitur \( X \) secara keseluruhan.

#### **Jenis Naive Bayes**:
1. **Gaussian Naive Bayes**: Digunakan ketika fitur-fitur mengikuti distribusi Gaussian (normal). Cocok untuk data kontinu.
2. **Multinomial Naive Bayes**: Digunakan untuk data diskrit, seperti jumlah kata dalam teks.
3. **Bernoulli Naive Bayes**: Cocok untuk fitur biner, misalnya untuk masalah klasifikasi teks dengan fitur "ada/tidak ada" kata tertentu.

#### **Cara Kerja Naive Bayes**:
1. **Mencari Probabilitas A Priori**: Hitung probabilitas kelas berdasarkan data training.
2. **Mencari Probabilitas Likelihood**: Hitung probabilitas setiap fitur muncul dalam kelas tertentu.
3. **Menghitung Probabilitas Posterior**: Gunakan teorema Bayes untuk menghitung probabilitas bahwa data baru termasuk dalam setiap kelas.
4. **Memilih Kelas dengan Probabilitas Tertinggi**: Data baru diprediksi termasuk dalam kelas yang memiliki probabilitas tertinggi.

#### **Kelebihan Naive Bayes**:
- **Cepat dan Efisien**: Naive Bayes sangat cepat, baik untuk training maupun prediksi, bahkan untuk dataset yang besar.
- **Mudah Diinterpretasikan**: Probabilitas setiap prediksi bisa dianalisis untuk interpretasi hasil.

#### **Kekurangan Naive Bayes**:
- **Asumsi Independensi**: Asumsi bahwa fitur-fitur independen seringkali tidak realistis dalam kenyataan, sehingga performanya bisa terpengaruh.
- **Tidak Cocok untuk Data dengan Fitur Berkorelasi**: Jika fitur sangat berkorelasi, kinerja Naive Bayes dapat menurun.

#### **Contoh Implementasi Naive Bayes di Python:**

```python
# Import library
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score
from sklearn.datasets import load_iris

# Load dataset iris
data = load_iris()
X = data.data
y = data.target

# Split data menjadi training dan testing set
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Inisialisasi model Naive Bayes (Gaussian)
nb = GaussianNB()

# Train model
nb.fit(X_train, y_train)

# Lakukan prediksi pada data testing
y_pred = nb.predict(X_test)

# Evaluasi akurasi model
accuracy = accuracy_score(y_test, y_pred)
print(f"Akurasi Naive Bayes: {accuracy * 100:.2f}%

")
```

---

### **Support Vector Machine (SVM)**

#### **Konsep SVM**
**Support Vector Machine (SVM)** adalah algoritma klasifikasi yang mencari **hyperplane** terbaik untuk memisahkan kelas-kelas dalam data. SVM bekerja dengan mencari hyperplane yang memaksimalkan margin antara dua kelas yang berbeda. Titik-titik data yang paling dekat dengan hyperplane disebut **support vectors** dan memiliki peran penting dalam menentukan posisi hyperplane.

![image](https://github.com/user-attachments/assets/0dee7c02-b447-43a2-b1f7-280841ad11d1)


#### **Cara Kerja SVM**:
1. **Linear SVM**: Pada data yang dapat dipisahkan secara linear, SVM mencari hyperplane (garis di 2D, bidang di 3D) yang memisahkan dua kelas dengan margin terbesar.
2. **Non-Linear SVM**: Ketika data tidak dapat dipisahkan secara linear, SVM menggunakan teknik yang disebut **kernel trick** untuk memetakan data ke dimensi yang lebih tinggi, di mana data dapat dipisahkan dengan hyperplane. Kernel yang umum digunakan termasuk:
   - **Linear Kernel**
   - **Polynomial Kernel**
   - **Radial Basis Function (RBF) Kernel**: Paling umum digunakan untuk data non-linear.

#### **Kelebihan SVM**:
- **Efektif pada Dimensi Tinggi**: SVM sangat baik dalam menangani dataset dengan fitur yang banyak.
- **Fleksibel dengan Kernel Trick**: Dengan menggunakan kernel yang tepat, SVM dapat menangani data yang sangat kompleks.

#### **Kekurangan SVM**:
- **Komputasi Berat**: Pelatihan SVM bisa sangat lambat untuk dataset besar.
- **Pemilihan Kernel dan Parameter Sulit**: Menemukan kernel yang tepat dan mengoptimalkan parameter seperti **C** (penalty parameter) bisa sulit dan memerlukan eksperimen.

#### **Contoh Implementasi SVM di Python**:

```python
# Import library
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC
from sklearn.metrics import accuracy_score
from sklearn.datasets import load_iris

# Load dataset iris
data = load_iris()
X = data.data
y = data.target

# Split data menjadi training dan testing set
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Inisialisasi model SVM dengan kernel linear
svm = SVC(kernel='linear')

# Train model
svm.fit(X_train, y_train)

# Lakukan prediksi pada data testing
y_pred = svm.predict(X_test)

# Evaluasi akurasi model
accuracy = accuracy_score(y_test, y_pred)
print(f"Akurasi SVM: {accuracy * 100:.2f}%")
```

---

### **Perbandingan Algoritma Klasifikasi**

| **Algoritma** | **Kelebihan** | **Kekurangan** | **Kapan Digunakan** |
|---------------|---------------|----------------|---------------------|
| **KNN**       | Sederhana, intuitif | Lambat untuk dataset besar, sensitif terhadap skala fitur | Cocok untuk data dengan distribusi sederhana atau masalah klasifikasi multi-class |
| **Naive Bayes** | Cepat, efisien | Asumsi independensi fitur tidak selalu valid | Cocok untuk data teks atau masalah di mana distribusi data dapat dianggap independen |
| **SVM**       | Efektif pada data berdimensi tinggi | Lambat untuk dataset besar, sulit memilih kernel | Cocok untuk dataset berdimensi tinggi dan masalah dengan margin besar antara kelas |

---
### **Metrik Evaluasi Klasifikasi dalam Machine Learning**

## 1. Confusion Matrix

**Confusion matrix** adalah alat yang berguna untuk memvisualisasikan performa model klasifikasi dengan membandingkan prediksi model dengan nilai sebenarnya. Tabel ini terdiri dari empat komponen utama:

- **True Positives (TP)**: Model memprediksi positif dan benar.
- **True Negatives (TN)**: Model memprediksi negatif dan benar.
- **False Positives (FP)**: Model memprediksi positif tetapi salah (type I error).
- **False Negatives (FN)**: Model memprediksi negatif tetapi salah (type II error).

|                      | Predicted Positive | Predicted Negative |
|----------------------|--------------------|--------------------|
| **Actual Positive**   | TP                 | FN                 |
| **Actual Negative**   | FP                 | TN                 |

```python
from sklearn.metrics import confusion_matrix

# Prediksi dari model
y_pred = model.predict(X_test)

# Menghitung confusion matrix
cm = confusion_matrix(y_test, y_pred)

print(cm)
```


### **2. Accuracy**

**Accuracy** adalah metrik yang mengukur persentase prediksi yang benar dari total prediksi yang dilakukan. Ini merupakan metrik yang sederhana dan sering digunakan, tetapi mungkin tidak memberikan gambaran lengkap jika data tidak seimbang (misalnya, kelas mayoritas bisa mendominasi).

$$Accuracy = \frac{TP + TN}{TP + TN + FP + FN}$$

```python
from sklearn.metrics import accuracy_score

# Menghitung akurasi
accuracy = accuracy_score(y_test, y_pred)
print(f"Akurasi: {accuracy}")
```

**Kelemahan:**  
- Tidak cocok untuk dataset yang tidak seimbang. Misalnya, jika 95% data adalah kelas negatif, model bisa mendapatkan akurasi 95% hanya dengan selalu memprediksi negatif, meskipun tidak mendeteksi kelas positif dengan baik.

### **3. Precision**

**Precision** adalah proporsi prediksi positif yang benar (dari semua prediksi positif). Precision membantu memahami seberapa tepat model saat memprediksi kelas positif.

$$Precision = \frac{TP}{TP + FP}$$

Precision tinggi berarti sebagian besar prediksi positif adalah benar.

```python
from sklearn.metrics import precision_score

# Menghitung precision
precision = precision_score(y_test, y_pred, average='weighted')
print(f"Precision: {precision}")
```

### **5. Recall (Sensitivity)**

**Recall** (juga dikenal sebagai **sensitivity** atau **true positive rate**) adalah proporsi data positif yang berhasil diprediksi dengan benar oleh model.

$$Recall = \frac{TP}{TP + FN}$$

Recall tinggi berarti model berhasil mendeteksi sebagian besar contoh positif.

```python
from sklearn.metrics import recall_score

# Menghitung recall
recall = recall_score(y_test, y_pred, average='weighted')
print(f"Recall: {recall}")
```

### **6. F1-Score**

**F1-Score** adalah rata-rata harmonik dari precision dan recall. Metrik ini memberikan keseimbangan antara precision dan recall, dan berguna ketika dataset tidak seimbang atau ketika ada trade-off antara kedua metrik tersebut.

$$F1 = 2 \times \frac{Precision \times Recall}{Precision + Recall}$$

```python
from sklearn.metrics import f1_score

# Menghitung F1-score
f1 = f1_score(y_test, y_pred, average='weighted')
print(f"F1-Score: {f1}")
```

**Kelebihan:**  
- F1-score memberikan gambaran yang lebih lengkap dalam situasi di mana precision dan recall berbeda jauh.

### **7. ROC Curve dan AUC**

**ROC (Receiver Operating Characteristic) Curve** adalah grafik yang menggambarkan trade-off antara **True Positive Rate (Recall)** dan **False Positive Rate (FPR)** pada berbagai ambang batas. ROC Curve berguna untuk memvisualisasikan kinerja model klasifikasi pada berbagai tingkat sensitivitas.

- **True Positive Rate (Recall)**: Rasio prediksi positif yang benar.
- **False Positive Rate (FPR)**: Rasio prediksi positif yang salah.

**AUC (Area Under Curve)** adalah nilai numerik yang mewakili area di bawah ROC Curve. Nilai AUC berkisar antara 0 hingga 1:
- **AUC = 1**: Model sempurna.
- **AUC = 0.5**: Model tidak lebih baik dari tebak acak.

```python
from sklearn.metrics import roc_auc_score, roc_curve
import matplotlib.pyplot as plt

# Menghitung probabilitas prediksi
y_proba = model.predict_proba(X_test)[:, 1]

# Menghitung ROC curve
fpr, tpr, thresholds = roc_curve(y_test, y_proba)

# Plot ROC curve
plt.plot(fpr, tpr, label="ROC curve")
plt.xlabel("False Positive Rate")
plt.ylabel("True Positive Rate")
plt.title("ROC Curve")
plt.show()

# Menghitung AUC
auc = roc_auc_score(y_test, y_proba)
print(f"AUC: {auc}")
```

