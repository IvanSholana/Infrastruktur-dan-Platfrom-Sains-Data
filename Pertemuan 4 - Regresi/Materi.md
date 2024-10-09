# Machine Learning

## Pengertian Machine Learning
Machine learning adalah bagian dari **artificial intelligence** yang memungkinkan mesin belajar dari data atau pengalaman masa lalu (**data historis**) tanpa perlu diprogram secara manual. Dengan kemampuan belajar secara otomatis, sistem dapat meningkatkan akurasinya seiring waktu.

Metode ini mirip dengan cara manusia belajar dari pengalaman. Jika seorang anak diajari membaca huruf berulang kali, maka ia akan mampu mengenali huruf tersebut. Dalam machine learning, mesin belajar dari **data**, bukan pengalaman, sehingga data menjadi komponen krusial.

---

## Tipe Algoritma Machine Learning

![Gambar9](https://github.com/user-attachments/assets/7e7d9fe3-d9c8-45f0-9afc-ce7010b95e9f)

### 1. Supervised Learning
Supervised Learning adalah model machine learning yang menggunakan **data training** yang berisi jawaban untuk masalah yang ingin diselesaikan. Mesin diharapkan meniru pola pada input data (prediktor) untuk menghasilkan output serupa.

#### Tugas dalam Supervised Learning
- **Regresi**: Memprediksi hasil numerik, misalnya harga rumah atau jarak tempuh kendaraan.

  ![Gambar3](https://github.com/user-attachments/assets/b7ae398a-4c67-4097-b821-e431b5d19bef)
- **Klasifikasi**: Memprediksi hasil diskrit, misalnya apakah seseorang terkena penyakit jantung (ya/tidak).

  ![Gambar2](https://github.com/user-attachments/assets/a5bb1c84-a9a4-484b-82de-368ecb27970e)

### 2. Unsupervised Learning
Unsupervised learning bekerja pada **data tidak berlabel**. Algoritma ini bertugas mendeteksi pola, mengelompokkan data, dan belajar dari struktur yang ada tanpa arahan dari manusia.

  ![Gambar4](https://github.com/user-attachments/assets/87ab1bd2-d9fb-435a-b0aa-2abfb81fd088)

---

## Regression

### Pengertian Regresi dalam Machine Learning
Regresi adalah teknik yang digunakan untuk memodelkan hubungan antara variabel independen (**input**) dan variabel dependen (**output**), dengan tujuan memprediksi nilai **kontinu**.

### Metrik Evaluasi dalam Regresi
- **Koefisien (slope)**: Menunjukkan pengaruh setiap variabel independen terhadap variabel dependen.
- **Intercept**: Nilai prediksi ketika semua variabel independen bernilai 0.
- **MSE, RMSE, MAE**: Metrik kesalahan model prediksi.
- **R²**: Mengukur seberapa baik model menjelaskan variasi data.

---

### 1. Regresi Linier

Regresi linier digunakan untuk memprediksi variabel target (**Y**) berdasarkan hubungan linear dengan variabel input (**X**).

#### Rumus Regresi Linier
![Screenshot 2024-09-23 221730](https://github.com/user-attachments/assets/12cfe6a8-e3da-437e-8729-51c4ff8e4e02)
#### Contoh Kode Implementasi Regresi Linier Sederhana
```python
# Import libraries untuk visualisasi dan evaluasi
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score, mean_absolute_error

 #Data sederhana (ukuran rumah dan harga rumah)
X = np.array([50, 60, 70, 80, 90, 100, 110, 120, 130, 140]).reshape(-1, 1)  # Ukuran rumah
y = np.array([150, 160, 175, 180, 200, 210, 220, 230, 245, 260])  # Harga rumah

 #Membagi dataset menjadi data latih dan uji
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

 #Membuat model regresi linear
model_linear = LinearRegression()

 #Melatih model
model_linear.fit(X_train, y_train)

 #Prediksi pada data uji
y_pred_test = model_linear.predict(X_test)   #Prediksi pada data uji

 #Visualisasi hasil regresi linear pada seluruh dataset
plt.scatter(X, y, color='blue', label='Data Asli')
plt.plot(X, model_linear.predict(X), color='red', label='Regresi Linear')
plt.title('Regresi Linear: Ukuran Rumah vs Harga Rumah')
plt.xlabel('Ukuran Rumah (m^2)')
plt.ylabel('Harga Rumah (juta)')
plt.legend()
plt.grid(True)
plt.show()

 #Evaluasi model
mse = mean_squared_error(y_test, y_pred_test)  # Mean Squared Error
rmse = np.sqrt(mse)   #Root Mean Squared Error
mae = mean_absolute_error(y_test, y_pred_test)  #Mean Absolute Error
r2 = r2_score(y_test, y_pred_test)   #R-squared

 #Output hasil
print("Mean Squared Error (MSE) pada data uji:", mse)
print("Root Mean Squared Error (RMSE) pada data uji:", rmse)
print("Mean Absolute Error (MAE) pada data uji:", mae)
print("R-squared (R2) pada data uji:", r2)
print("Koefisien (slope):", model_linear.coef_[0])
print("Intercept:", model_linear.intercept_)

```
---

### 2. Multiple Linear Regression

**Multiple Linear Regression** memperluas regresi linier sederhana dengan menggunakan lebih dari satu variabel independen.

#### Rumus Multiple Linear Regression
![Screenshot 2024-09-23 222434](https://github.com/user-attachments/assets/b15caf12-87d1-4cde-9b16-6b3e3c9a3b83)

#### Contoh Implementasi Multiple Linear Regression

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score

# Data sederhana
data = {
    'ukuran_rumah': [50, 60, 70, 80, 90, 100, 110, 120, 130, 140],
    'jumlah_kamar': [1, 2, 2, 3, 3, 4, 4, 5, 5, 6],
    'harga_rumah': [150, 160, 175, 180, 200, 210, 220, 230, 245, 260]
}

X = np.array([data['ukuran_rumah'], data['jumlah_kamar']]).T
y = np.array(data['harga_rumah'])

# Membagi dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Membuat model regresi linear
model = LinearRegression()
model.fit(X_train, y_train)

# Prediksi pada data uji
y_pred_test = model.predict(X_test)

# Evaluasi model
mse = mean_squared_error(y_test, y_pred_test)
rmse = np.sqrt(mse)
mae = mean_absolute_error(y_test, y_pred_test)
r2 = r2_score(y_test, y_pred_test)

print("MSE:", mse)
print("RMSE:", rmse)
print("MAE:", mae)
print("R-squared:", r2)

# Visualisasi
plt.scatter(X_test[:, 0], y_test, color='blue', label='Data Asli')
plt.scatter(X_test[:, 0], y_pred_test, color='red', label='Prediksi')
plt.title('Multiple Linear Regression: Ukuran Rumah vs Harga Rumah')
plt.xlabel('Ukuran Rumah (m^2)')
plt.ylabel('Harga Rumah (juta)')
plt.legend()
plt.grid(True)
plt.show()
```

---

### 3. Regresi Logistik

Regresi logistik digunakan ketika variabel dependen bersifat **kategori** (misalnya, 0 atau 1). Meskipun disebut regresi, teknik ini lebih mirip dengan klasifikasi karena hasil yang diinginkan adalah **probabilitas** sebuah data masuk dalam kelas tertentu.


#### Contoh Implementasi Regresi Logistik

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report

# Data sederhana
X = np.array([[45], [50], [55], [60], [65], [70], [75], [80], [85], [90], [95], [100]])
y = np.array([0, 0, 0, 0, 1, 0, 1, 1, 1, 1, 1, 1])

# Membagi dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Membuat model regresi logistik
model_logistik = LogisticRegression()
model_logistik.fit(X_train, y_train)

# Prediksi pada data uji
y_pred_logistik = model_logistik.predict(X_test)

# Visualisasi kurva regresi logistik
probabilitas = model_logistik.predict_proba(X)[:, 1]
plt.scatter(X, y, color='blue', label='Data Asli')
plt.plot(X, probabilitas, color='red', label='Kurva Regresi')
plt.show()

# Evaluasi model
accuracy = accuracy_score(y_test, y_pred_logistik)
conf_matrix = confusion_matrix(y_test, y_pred_logistik)
class_report = classification_report(y_test, y_pred_logistik)

print("Accuracy:", accuracy)
print("Confusion Matrix:\n", conf_matrix)
print("Classification Report:\n", class_report)
```

---

### 4. Perbandingan Regresi Linier dan Logistik

- **Regresi Linier** memprediksi nilai numerik, sedangkan **Regresi Logistik** memprediksi probabilitas suatu kejadian.
- **Regresi Logistik** lebih cocok untuk variabel dependen yang bersifat biner, sedangkan **Regresi Linier** digunakan untuk variabel dependen yang kontinu.
