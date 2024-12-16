# Social Network Analysis

![alt text](image.png)

## 1. Definisi Social Network Analysis
Metode untuk memahami hubungan dan interaksi antara individu, kelompok, atau entitas lainnya dalam suatu jaringan sosial. Di dalam analisis ini, jaringan sosial dipandang dan direpresentasikan sebagai suatu struktur yang terdiri dari `simpul (nodes)` yang mewakili `entitas` dan `sisi (edges)` yang mewakili hubungan atau interaksi antar entitas. 

Melalui SNA dapat diidentifikasi pola komunikasi dan peran masing-masing entitas dalam jaringan dan bagaimana struktur sosial tersebut dapat mempengaruhi keputusan individu dalam suatu jaringan. 

## Contoh Kasus : Analisis Jaringan Sosial di Media 
Sebuah perusahaan ingin memahami bagaimana kampanye pemasaran mereka tersebar melalui platform media sosial (misalnya, Twitter atau Instagram). Mereka ingin mengetahui siapa yang paling berpengaruh dalam percakapan mengenai produk mereka dan bagaimana informasi menyebar. Dalam hal ini setiap pengguna media sosial yang berbicara tentang produk perusahaan dianggap sebagai simpul. Hubungan antara pengguna tercipta melalui retweet, mention, atau tag yang berkaitan dengan kampanye pemasaran.

## 2. Representasi Jaringan

![alt text](image-1.png)

Jaringan dalam SNA digambarkan melalui graf yang terdiri dari dua komponen utama yaitu:
1. Simpul (Nodes): Mewakili aktor atau entitas dalam jaringan. Dalam jaringan sosial, simpul ini bisa berupa individu, kelompok, organisasi, atau bahkan hal-hal seperti pesan, konsep, atau lokasi.

2. Sisi (Edges): Mewakili hubungan atau interaksi antara dua simpul. Sisi ini bisa bersifat arah (directed) atau tak arah (undirected).
    - Arah: Hubungan satu arah, misalnya dalam hubungan pertemanan di media sosial (seperti Twitter), di mana satu orang mengikuti orang lain tetapi tidak sebaliknya.
    - Tak Arah: Hubungan dua arah, misalnya dalam hubungan pertemanan di Facebook, di mana kedua individu saling terhubung.

### Contoh Membuat Graf pada Python

**1. Membuat Graf**
```python
import networkx as nx
import matplotlib.pyplot as plt

# Membuat graf kosong
G = nx.Graph()

# Menambahkan simpul (nodes)
G.add_nodes_from(["A", "B", "C", "D"])

# Menambahkan sisi (edges)
G.add_edges_from([("A", "B"), ("A", "C"), ("B", "C"), ("C", "D")])

# Menggambar graf
plt.figure(figsize=(8, 6))
nx.draw(G, with_labels=True, node_color='lightblue', node_size=1000, font_size=15, font_weight='bold')
plt.title("Contoh Graf Sederhana", fontsize=16)
plt.show()
```

**2. Membuat Graf Dua Arah**
```python
import networkx as nx
import matplotlib.pyplot as plt

# Membuat graf berarah
DG = nx.DiGraph()

# Menambahkan simpul dan sisi berarah
DG.add_edges_from([("A", "B"), ("A", "C"), ("B", "D"), ("C", "D"), ("D", "A")])

# Menggambar graf
plt.figure(figsize=(8, 6))
nx.draw(DG, with_labels=True, node_color='lightgreen', node_size=1000, font_size=15, font_weight='bold', arrowsize=20)
plt.title("Contoh Graf Berarah", fontsize=16)
plt.show()
```

**3. Membuat Graf dengan Bobot**
```python
import networkx as nx
import matplotlib.pyplot as plt

# Membuat graf berarah dengan bobot
WG = nx.DiGraph()

# Menambahkan simpul dan sisi dengan bobot
WG.add_edge("A", "B", weight=5)
WG.add_edge("A", "C", weight=3)
WG.add_edge("B", "C", weight=2)
WG.add_edge("C", "D", weight=4)
WG.add_edge("D", "A", weight=1)

# Menggambar graf
pos = nx.spring_layout(WG)  # Layout untuk graf
plt.figure(figsize=(8, 6))

# Menggambar graf dengan bobot
nx.draw(WG, pos, with_labels=True, node_color='orange', node_size=1000, font_size=15, font_weight='bold', arrowsize=20)
labels = nx.get_edge_attributes(WG, 'weight')  # Mengambil atribut bobot
nx.draw_networkx_edge_labels(WG, pos, edge_labels=labels)

plt.title("Contoh Graf Berarah dengan Bobot", fontsize=16)
plt.show()
```

# 3. Ukuran Dasar dalam Social Network Analysis (SNA)
Dalam analisis jaringan sosial (Social Network Analysis - SNA), memahami struktur dan dinamika jaringan dilakukan dengan menghitung berbagai ukuran dasar. Ukuran ini membantu menjelaskan peran individu (node) dalam jaringan, serta karakteristik global jaringan secara keseluruhan. Materi ini dibagi menjadi dua bagian utama: Ukuran Node dan Ukuran Global.

## **Centrality Metrics (Ukuran Node)**
- **Degree Centrality** : Degree centrality mengukur jumlah koneksi langsung yang dimiliki oleh sebuah simpul (node). Dalam jaringan tak berarah, ini dihitung sebagai jumlah sisi (edges) yang terhubung ke simpul tersebut. Dalam jaringan berarah, dihitung sebagai `in-degree` atau jumlah koneksi masuk dan `out-degree` atau jumlah koneksi keluar. Nilai ini dapat diartikan bahwa Node dengan degree tinggi dianggap lebih terhubung atau lebih populer dalam jaringan.
- **Closeness Centrality** : Closeness centrality mengukur seberapa cepat sebuah node dapat mencapai node lain dalam jaringan. Semakin rendah jarak rata-rata dari sebuah node ke node lainnya, semakin tinggi closeness centrality-nya. Node dengan closeness centrality tinggi berada di posisi strategis untuk menyebarkan informasi dengan cepat ke seluruh jaringan.
- **Betweenness Centrality** : Betweenness centrality mengukur seberapa sering sebuah node menjadi perantara (penghubung) dalam jalur terpendek antara dua node lain. Hal ini dapat diartikan bahwa Node dengan betweenness tinggi adalah "broker" atau "jembatan" utama yang menghubungkan bagian-bagian berbeda dari jaringan dan Berguna untuk memahami node yang berpengaruh dalam jaringan.

## **Global Metrics**
Ukuran global menggambarkan karakteristik jaringan secara keseluruhan, memberikan wawasan tentang pola hubungan dalam jaringan.
- **Density** : ukuran yang menunjukkan seberapa padat jaringan, yaitu sejauh mana semua node dalam jaringan saling terhubung. Nilai density tinggi berarti banyak hubungan antara node dalam jaringan.
- **Clustering Coefficient** : Clustering coefficient mengukur kecenderungan node untuk membentuk kelompok (cluster). Ini menunjukkan seberapa kuat hubungan antar tetangga sebuah node.