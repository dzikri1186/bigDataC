# Laporan Proyek Data: Spotify User Engagement
![download](https://github.com/user-attachments/assets/6050bfdf-1cc3-46db-b8c0-0fa61a2814e7)

## Deskripsi Proyek
Proyek ini bertujuan untuk menganalisis data pengguna Spotify guna memahami pola-pola keterlibatan dan faktor-faktor yang memengaruhinya. Proyek ini mencakup eksplorasi data, visualisasi, dan analisis lanjutan dengan metode statistik serta machine learning sederhana.

---
## **Storyboard: Membuat Cerita yang Logis dan Kohesif**
Analisis dalam proyek ini dirancang sebagai cerita yang logis, dengan fokus pada urutan **‘data -> wawasan -> tindakan’**. Setiap langkah, mulai dari eksplorasi data hingga visualisasi dan analisis lanjutan, dihubungkan untuk menciptakan wawasan yang dapat diimplementasikan. Tujuan akhirnya adalah memberikan rekomendasi tindakan berdasarkan hasil analisis.

Penekanan utama:
1. **Cerita yang Kohesif**: Setiap visualisasi dan analisis memiliki peran dalam mendukung cerita.
2. **Wawasan yang Actionable**: Proyek tidak hanya menghasilkan visualisasi, tetapi juga mengarahkan pada tindakan nyata.
3. **Fleksibilitas**: Storyboard berkembang seiring eksplorasi data dan temuan baru.


## **Tahapan Proyek**
### SELECTED DATASET: SPOTIFY USER ENGAGEMENT ✅
Dataset mencakup informasi tentang keterlibatan pengguna Spotify, termasuk aktivitas mendengarkan, preferensi, dan demografi.

### IMPORT LIBRARY ✅
Pustaka yang digunakan mencakup:
- **IPython & OS**: Untuk manajemen file dan lingkungan.
- **Pandas & NumPy**: Untuk manipulasi data.
- **Matplotlib & Seaborn**: Untuk visualisasi data.
- **ExtraTreesClassifier**: Untuk analisis fitur penting.
- **LinearRegression**: Untuk regresi.

Kode untuk mengimpor pustaka:
```python
from IPython.display import display
import os
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.ensemble import ExtraTreesClassifier
from sklearn.linear_model import LinearRegression
```

### DOWNLOAD DATA ✅
Dataset diunduh dari sumber tepercaya, disimpan dalam Google Drive, dan diekstrak menggunakan `zipfile`.

### LOAD DATASET ✅
Dataset dimuat menggunakan `pandas.read_csv()`:
```python
data = pd.read_csv('spotify_data.csv')
data.head()
```

### HANDLING MISSING VALUE ✅
Data yang hilang dianalisis dan ditangani:
- Mengidentifikasi nilai hilang:
    ```python
    data.isnull().sum()
    ```
- Mengimputasi data menggunakan mean/median/mode.

  ![download (1)](https://github.com/user-attachments/assets/ac3553e5-c5af-4f48-8515-5c215c3822c5)


### VISUALISASI DEMOGRAFIS PENGGUNA ✅
Visualisasi dibuat untuk memahami karakteristik demografis pengguna:
- **Distribusi gender pengguna**:
    ```python
    sns.countplot(x='gender', data=data)
    plt.title('Distribusi Gender')
    plt.show()
    ```
    ![download (2)](https://github.com/user-attachments/assets/14e81f11-838b-4b9c-aa9e-ceb603d313fb)


### VISUALISASI POLA KETERLIBATAN PENGGUNA ✅
Analisis pola mendengarkan pengguna berdasarkan waktu:
- **Pola mendengarkan harian**:
    ```python
    sns.lineplot(x='hour', y='listens', data=data)
    plt.title('Pola Mendengarkan Harian')
    plt.show()
    ```
![download (3)](https://github.com/user-attachments/assets/1c34d3ca-1b63-45df-8b7c-d786a836070e)

### ANALISIS LANJUTAN UNTUK IDENTIFIKASI FAKTOR KETERLIBATAN (ExtraTreesClassifier) ✅
Menggunakan ExtraTreesClassifier untuk menentukan fitur penting:
```python
X = data[['age', 'hour', 'gender']]
y = data['engagement']

model = ExtraTreesClassifier()
model.fit(X, y)

importances = model.feature_importances_
plt.barh(X.columns, importances)
plt.title('Pentingnya Fitur')
plt.show()
```
![download (4)](https://github.com/user-attachments/assets/541203f4-f282-4615-b6d4-0f8c7a9f2f6b)


### ANALISIS DAN VISUALISASI FAKTOR KETERLIBATAN ✅
Visualisasi faktor signifikan:
- **Umur dan keterlibatan**:
    ```python
    sns.boxplot(x='engagement', y='age', data=data)
    plt.title('Umur vs Keterlibatan')
    plt.show()
    ```
![download (5)](https://github.com/user-attachments/assets/998d814b-21cb-4299-b3d1-ed5df54abce2)

---

## **Kesimpulan**
1. Faktor demografis, seperti umur dan gender, memiliki pengaruh signifikan terhadap keterlibatan pengguna.
2. Waktu aktivitas pengguna (jam mendengarkan) menunjukkan pola keterlibatan yang menarik.
3. Insight ini dapat membantu Spotify meningkatkan pengalaman pengguna melalui personalisasi.
