<div align="center">

<h3>Mobile Price Classification & Explainability (SVM + SHAP)</h3>

<p>
  <strong><em>Beyond the brand: Using data to reveal a phone's true price tag.</em></strong>
</p>

<p>
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python" alt="Python Version">
  <img src="https://img.shields.io/badge/Framework-Scikit--learn-orange?style=for-the-badge&logo=scikit-learn" alt="Scikit-learn">
  <img src="https://img.shields.io/badge/Tool-SHAP-brightgreen?style=for-the-badge" alt="SHAP">
  <img src="https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white" alt="Google Colab">
</p>

</div>

---

## 📖 Gambaran Umum Proyek

Pasar *mobile phone* sangat jenuh, membuatnya sulit bagi konsumen untuk menilai harga yang wajar. Proyek ini bertujuan untuk memecahkan masalah tersebut dengan **mengklasifikasikan rentang harga ponsel** berdasarkan spesifikasi teknisnya menggunakan model **Support Vector Machine (SVM)**.

Lebih dari sekadar prediksi, proyek ini menggunakan **SHAP (SHapley Additive exPlanations)** untuk membongkar "kotak hitam" model dan memahami **faktor pendorong utama** di balik harga sebuah ponsel. Tujuannya adalah untuk memberikan wawasan berbasis data yang transparan dan dapat ditindaklanjuti.

---

## 🚀 Teknologi yang Digunakan

| Library | Kegunaan |
| :--- | :--- |
| **Pandas** | Manipulasi dan pembersihan data. |
| **Scikit-learn** | Implementasi model SVM dan evaluasi metrik. |
| **SHAP** | Explainability AI untuk interpretasi hasil model. |
| **Matplotlib & Seaborn** | Visualisasi data eksplorasi dan hasil SHAP. |
| **Jupyter Notebook** | Lingkungan kerja interaktif untuk analisis. |

---

## 📂 Dataset Mentah
- Sumber: [Kaggle – Mobile Price Classification](https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification)
- File yang digunakan:
  - `train.csv` → Dataset utama yang berisi 21 fitur ponsel dan variabel target `price_range`.

<div align="center">

## ⚙️ Alur Kerja Analisis
Tabel berikut merangkum setiap tahapan dalam proyek ini, mulai dari pemuatan data hingga interpretasi hasil.

</div>

<table align="center" width="95%">
  <thead>
    <tr align="center">
      <th width="20%">Langkah</th>
      <th width="30%">Metode & Teknik</th>
      <th width="50%">Alasan Penggunaan</th>
    </tr>
  </thead>
  <tbody>
    <tr valign="center">
      <td><strong>1. Pemuatan Data</strong></td>
      <td><code>pandas.read_csv()</code></td>
      <td>Memuat dataset dari file <code>train.csv</code> ke dalam DataFrame untuk analisis lebih lanjut.</td>
    </tr>
    <tr valign="center">
      <td><strong>2. Pra-pemrosesan</strong></td>
      <td><code>train_test_split</code></td>
      <td>Membagi data menjadi set latih dan uji untuk memastikan evaluasi model yang objektif dan tidak bias.</td>
    </tr>
    <tr valign="center">
      <td><strong>3. Pemodelan</strong></td>
      <td><code>Support Vector Classifier (SVC)</code></td>
      <td>Model yang efektif untuk masalah klasifikasi, terutama dalam menemukan batas keputusan yang optimal antar kelas.</td>
    </tr>
    <tr valign="center">
      <td><strong>4. Evaluasi</strong></td>
      <td><code>accuracy_score</code> & <code>classification_report</code></td>
      <td>Mengukur kinerja model secara kuantitatif untuk mengetahui seberapa akurat prediksinya.</td>
    </tr>
    <tr valign="center">
      <td><strong>5. Explainability</strong></td>
      <td>Library <code>SHAP</code></td>
      <td>Membongkar "kotak hitam" model untuk memahami kontribusi dan dampak setiap fitur terhadap hasil prediksi.</td>
    </tr>
    <tr valign="center">
      <td><strong>6. Visualisasi</strong></td>
      <td>Plot SHAP (Bar, Beeswarm, Force)</td>
      <td>Menerjemahkan data SHAP yang kompleks menjadi wawasan visual yang intuitif dan mudah dipahami.</td>
    </tr>
  </tbody>
</table>

<div align="center">

## 📊 Visualisasi Hasil

Ringkasan visual untuk memahami bagaimana spesifikasi ponsel memengaruhi prediksi harga.

</div>

<table align="center" width="100%">
  <!-- ROW 1: BAR PLOT -->
  <tr valign="center">
    <td width="50%" align="left">
      <h3>📊 Peringkat Fitur Global (Bar Plot)</h3>
      <p><strong>Penjelasan:</strong> Fitur diurutkan berdasarkan dampak rata-rata absolut pada prediksi harga. <strong>RAM</strong> tampil paling dominan, diikuti resolusi layar (<code>px_height</code>, <code>px_width</code>) dan daya baterai (<code>battery_power</code>). Ketiganya menjadi pendorong nilai utama.</p>
    </td>
    <td width="50%" align="center">
      <img src="https://github.com/user-attachments/assets/03538157-a9cd-49f8-8475-1fa73fd1b93f" alt="SHAP Bar Plot" width="95%" />
    </td>
  </tr>

  <tr><td colspan="2"><br><hr><br></td></tr>

  <!-- ROW 2: BEESWARM -->
  <tr valign="center">
    <td width="50%" align="left">
      <h3>🐝 Distribusi Dampak Fitur (Beeswarm Plot)</h3>
      <p><strong>Penjelasan:</strong> Setiap titik mewakili satu sampel. Sumbu X adalah nilai SHAP (dampak pada output), warna titik menunjukkan nilai fitur (merah = tinggi, biru = rendah). Contohnya, <code>ram</code> tinggi cenderung mendorong ke harga lebih mahal (nilai SHAP positif).</p>
    </td>
    <td width="50%" align="center">
      <img src="https://github.com/user-attachments/assets/b747e890-8695-4d9b-a4a5-6d27f04db170" alt="SHAP Beeswarm Plot" width="95%" />
    </td>
  </tr>

  <tr><td colspan="2"><br><hr><br></td></tr>

  <!-- ROW 3: FORCE PLOT -->
  <tr valign="center">
    <td width="50%" align="left">
      <h3>🔬 Analisis Prediksi Individual (Force Plot)</h3>
      <p><strong>Penjelasan:</strong> Memerinci alasan sebuah ponsel diprediksi ke rentang harga tertentu. Segmen <strong>merah</strong> menaikkan prediksi (mendorong ke kanan), sedangkan <strong>biru</strong> menurunkannya.</p>
      <ul>
        <li><strong>Contoh 1 – Harga Tinggi:</strong> Didominasi <code>ram</code> (3898) dan <code>px_height</code> (1247) yang besar.</li>
        <li><strong>Contoh 2 – Harga Rendah:</strong> Dipengaruhi <code>ram</code> (742), <code>battery_power</code> (602), dan <code>px_height</code> (338) yang rendah.</li>
      </ul>
    </td>
    <td width="50%" align="center">
      <img src="https://github.com/user-attachments/assets/2ef11767-a4f0-4473-90a6-6a83a9fbf89d" alt="SHAP Force Plot - High Price" width="95%" /><br>
      <em>Prediksi Harga Tinggi</em><br><br>
      <img src="https://github.com/user-attachments/assets/15011735-0ab0-4a65-abcd-33d4d0436b9f" alt="SHAP Force Plot - Low Price" width="95%" /><br>
      <em>Prediksi Harga Rendah</em>
    </td>
  </tr>
</table>

---

<div align="center">

## 📝 Kesimpulan & Rekomendasi
Berikut adalah rangkuman wawasan utama yang dapat ditindaklanjuti dari analisis ini.

</div>

<table align="center" width="95%">
  <tr valign="center">
    <td width="30%">
      <h4>🔎 Wawasan & Temuan</h4>
    </td>
    <td width="70%">
      <ul>
        <li><strong>RAM adalah Raja:</strong> <code>ram</code> secara konsisten menjadi prediktor paling dominan dalam menentukan kelas harga.</li>
        <li><strong>Baterai & Resolusi Penting:</strong> <code>battery_power</code> dan resolusi layar (<code>px_height</code>, <code>px_width</code>) adalah pendorong harga sekunder yang sangat kuat.</li>
        <li><strong>Memori Internal Krusial:</strong> Kapasitas <code>int_memory</code> juga merupakan faktor penentu yang signifikan.</li>
      </ul>
    </td>
  </tr>
  
  <tr><td colspan="2"><hr></td></tr>

  <tr valign="center">
    <td>
      <h4>💡 Rekomendasi Model</h4>
    </td>
    <td>
      <ul>
        <li><strong>Feature Scaling:</strong> Terapkan <code>StandardScaler</code> pada data, karena SVM sensitif terhadap skala fitur dan ini dapat meningkatkan akurasi.</li>
        <li><strong>Hyperparameter Tuning:</strong> Gunakan <code>GridSearchCV</code> untuk menemukan parameter <code>C</code> dan <code>gamma</code> terbaik untuk model SVM.</li>
        <li><strong>Eksperimen Kernel:</strong> Coba gunakan kernel SVM yang berbeda (misalnya <code>'rbf'</code>) untuk melihat apakah batas keputusan non-linear memberikan hasil lebih baik.</li>
      </ul>
    </td>
  </tr>

  <tr><td colspan="2"><hr></td></tr>

  <tr valign="center">
    <td>
       <h4>🎬 Aksi & Dampak Bisnis</h4>
    </td>
    <td>
      <ul>
        <li><strong>Aksi:</strong> Prioritaskan upgrade <strong>RAM</strong> dan kualitas <strong>baterai/layar</strong> pada pengembangan produk baru.</li>
        <li><strong>Dampak:</strong> Meningkatkan justifikasi harga premium, memperkuat daya saing pasar, dan menaikkan margin keuntungan.</li>
      </ul>
    </td>
  </tr>
</table>

---

<div align="center">

## 💡 Rekomendasi Lanjutan
Berikut adalah beberapa langkah yang disarankan untuk pengembangan dan peningkatan model di masa depan.

</div>

<table align="center" width="75%">
  <tr valign="center">
    <td>
      <h3 align="center">📏 Pra-pemrosesan (Preprocessing)</h3>
      <ul>
        <li>
          <strong>Feature Scaling:</strong> Sangat disarankan untuk menerapkan <code>StandardScaler</code> pada data sebelum melatih model. Algoritma SVM sangat sensitif terhadap skala fitur, dan langkah ini berpotensi meningkatkan akurasi secara signifikan.
        </li>
        <li>
          <strong>Analisis Outlier:</strong> Lakukan analisis lebih dalam untuk mendeteksi dan menangani data pencilan (<em>outlier</em>) yang mungkin dapat memengaruhi performa dan generalisasi model.
        </li>
      </ul>
    </td>
  </tr>
  
  <tr><td><hr></td></tr>

  <tr valign="center">
    <td>
      <h3 align="center">⚙️ Pemodelan (Modeling)</h3>
      <ul>
        <li>
          <strong>Hyperparameter Tuning:</strong> Gunakan <code>GridSearchCV</code> untuk secara sistematis menemukan kombinasi parameter <code>C</code> dan <code>gamma</code> terbaik untuk memaksimalkan performa SVM.
        </li>
        <li>
          <strong>Eksperimen Kernel:</strong> Cobalah kernel SVM yang berbeda (misalnya <code>'rbf'</code> atau <code>'poly'</code>) untuk mengeksplorasi apakah batas keputusan non-linear dapat menangkap pola data yang lebih kompleks dan memberikan hasil yang lebih baik.
        </li>
        <li>
          <strong>Perbandingan Model:</strong> Bandingkan performa SVM dengan model <em>ensemble</em> yang kuat seperti <code>Random Forest</code> atau <code>XGBoost</code> untuk mendapatkan <em>benchmark</em> dan menentukan model mana yang paling optimal untuk dataset ini.
        </li>
      </ul>
    </td>
  </tr>
</table>

---

## 📝 Kesimpulan

Wawasan dari data ini dapat diterjemahkan menjadi tindakan strategis yang nyata bagi produsen dan pemasar ponsel.

| Wawasan Kunci | Tindakan Konkret (Untuk Produsen) | Dampak Nyata (Untuk Bisnis) |
| :--- | :--- | :--- |
| **RAM adalah pendorong utama nilai dan harga.** | Prioritaskan upgrade RAM pada ponsel kelas menengah untuk menjustifikasi perpindahan ke kategori harga yang lebih tinggi. | Meningkatkan daya saing pasar dan margin keuntungan. |
| **Kualitas baterai dan layar sangat dihargai.** | Luncurkan kampanye pemasaran yang menonjolkan "daya tahan baterai seharian" dan "layar super jernih" untuk memperkuat citra premium. | Menarik segmen pengguna yang lebih luas dan memberikan proposisi nilai yang jelas. |
| **Beberapa fitur (misal: jumlah core) kurang berdampak.**| Optimalkan biaya dengan menggunakan komponen standar untuk fitur yang kurang berdampak, dan alihkan anggaran ke RAM atau baterai. | Alokasi sumber daya yang lebih efisien dan pengembangan produk yang lebih hemat biaya. |

---

## 🤖 Penjelasan Dukungan AI

Kami menerapkan AI & Analitik untuk:
- 📈 Melatih **model SVM** untuk mengklasifikasikan harga ponsel secara akurat.
- 🔍 Melakukan **analisis SHAP** untuk mengungkap logika model dan menemukan pendorong harga utama.
- 📝 Menghasilkan **wawasan berbasis data** untuk strategi produk dan pemasaran.

Ini memastikan bahwa semua kesimpulan yang ditarik bersifat **berbasis bukti** dan **dapat ditindaklanjuti**.

---

## 📁 Struktur File

```
.
├── notebooks/
│   └── mobile_price_classification.ipynb
├── data/
│   └── train.csv
└── README.md
```

---
<div align="center">
  <h3>Terhubung dengan Saya</h3>
  <p>
    <a href="https://github.com/shelviapramodita" target="_blank"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"></a>
    <a href="https://www.linkedin.com/in/shelviapramodita/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  </p>
</div>
