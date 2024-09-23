# _1. SDLC (Software Development Life Cycle)_

Software Development Life Cycle (SDLC) adalah proses terstruktur yang digunakan oleh pengembang perangkat lunak untuk merancang, mengembangkan, menguji, dan mendistribusikan perangkat lunak berkualitas tinggi. SDLC terdiri dari beberapa tahapan yang membantu memastikan perangkat lunak yang dikembangkan memenuhi kebutuhan pengguna, bebas dari kesalahan besar, dan dikirimkan tepat waktu. Berikut adalah tahapan-tahapan SDLC:

## _Tahapan SDLC:_

1. **Planning (Perencanaan):**

   - Langkah awal yang berfokus pada memahami apa yang ingin dicapai oleh perangkat lunak.
   - Termasuk analisis kebutuhan bisnis, serta estimasi biaya dan waktu.

2. **Requirement Analysis (Analisis Kebutuhan):**

   - Mengumpulkan dan mendokumentasikan kebutuhan sistem dari pemangku kepentingan.
   - Mengidentifikasi fitur dan fungsi yang diperlukan oleh perangkat lunak.

3. **Design (Desain):**

   - Tahap ini melibatkan pembuatan arsitektur sistem dan desain detail perangkat lunak.
   - Mencakup desain antarmuka, basis data, dan struktur logika.

4. **Implementation (Implementasi):**

   - Pengkodean atau pemrograman dimulai berdasarkan desain yang telah disepakati.
   - Pengembangan dilakukan sesuai dengan kebutuhan dan spesifikasi yang telah ditentukan.

5. **Testing (Pengujian):**

   - Pengujian perangkat lunak dilakukan untuk memastikan tidak ada bug atau masalah.
   - Meliputi unit testing, integration testing, dan user acceptance testing (UAT).

6. **Deployment (Distribusi):**

   - Setelah pengujian selesai dan perangkat lunak stabil, perangkat lunak diluncurkan ke lingkungan produksi.

7. **Maintenance (Pemeliharaan):**
   - Setelah perangkat lunak diluncurkan, tahap pemeliharaan dimulai.
   - Mencakup perbaikan bug, update fitur, dan peningkatan sistem berdasarkan feedback pengguna.

## _Metodologi SDLC:_

- **Waterfall:** Proses linier di mana satu fase harus diselesaikan sebelum fase berikutnya dimulai.
- **Agile:** Metodologi yang lebih fleksibel dan iteratif, di mana pengembangan dilakukan dalam sprint pendek dengan melibatkan feedback pengguna secara terus-menerus.
- **Scrum:** Subset dari Agile yang memecah proyek menjadi siklus kerja yang disebut sprints.

---

# _2. Basic Python Programming_

Python adalah bahasa pemrograman yang mudah dipelajari dan digunakan, serta banyak diaplikasikan di berbagai bidang, mulai dari pengembangan web hingga analisis data. Berikut adalah konsep dasar Python:

## _2.1. Variabel dan Tipe Data_

Di Python, variabel digunakan untuk menyimpan data, dan tipe data menentukan jenis nilai yang dapat disimpan. Beberapa tipe data dasar di Python adalah:

- **int:** Bilangan bulat, contoh: `x = 5`
- **float:** Bilangan desimal, contoh: `y = 3.14`
- **str:** String atau teks, contoh: `name = "Candra"`
- **bool:** Boolean, dengan nilai `True` atau `False`

_Contoh:_

```python
x = 5           # int
y = 3.14        # float
name = "Candra" # str
is_student = True # bool
```

## _2.2. Struktur Kontrol_

### _a. If-Else Statement_

If-else digunakan untuk pengambilan keputusan.

_Contoh:_

```python
age = 20
if age >= 18:
    print("Dewasa")
else:
    print("Belum dewasa")
```

### _b. Looping (Perulangan)_

- **For Loop:** Digunakan untuk iterasi pada elemen dalam list atau string.

  _Contoh:_

  ```python
  for i in range(5):
      print(i)
  ```

- **While Loop:** Perulangan berdasarkan kondisi yang terus berjalan sampai kondisi tersebut salah.

  _Contoh:_

  ```python
  count = 0
  while count < 5:
      print(count)
      count += 1
  ```

## _2.3. Fungsi_

Fungsi adalah blok kode yang dapat digunakan kembali.

_Contoh:_

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Candra")
```

## _2.4. List dan Dictionary_

- **List:** Kumpulan nilai yang dapat diakses dengan indeks.

  _Contoh:_

  ```python
  fruits = ["apple", "banana", "cherry"]
  print(fruits[0])  # Output: apple
  ```

- **Dictionary:** Kumpulan pasangan key-value.

  _Contoh:_

  ```python
  person = {"name": "Candra", "age": 21}
  print(person["name"])  # Output: Candra
  ```

## _2.5. Input dan Output_

- **Input:** Mengambil data dari pengguna.

  _Contoh:_

  ```python
  name = input("Enter your name: ")
  print(f"Hello, {name}")
  ```

- **Output:** Menampilkan data ke layar.

  _Contoh:_

  ```python
  print("Hello, World!")
  ```
