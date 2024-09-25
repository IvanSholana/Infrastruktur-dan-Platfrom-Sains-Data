# 2. Basic Python Programming

Python adalah bahasa pemrograman yang mudah dipelajari dan digunakan, serta banyak diaplikasikan di berbagai bidang, mulai dari pengembangan web hingga analisis data. Berikut adalah konsep dasar Python:

## 2.1. Variabel dan Tipe Data

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

## 2.2. Struktur Kontrol

### a. If-Else Statement

If-else digunakan untuk pengambilan keputusan.

_Contoh:_

```python
age = 20
if age >= 18:
    print("Dewasa")
else:
    print("Belum dewasa")
```

### b. Looping (Perulangan)

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

## 2.3. Fungsi

Fungsi adalah blok kode yang dapat digunakan kembali.

_Contoh:_

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Candra")
```

## 2.4. List dan Dictionary

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

## 2.5. Input dan Output

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