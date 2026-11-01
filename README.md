# HR Analytics: Data Scientist Job Change Factors

Repository ini berisi proyek tugas mata kuliah Machine Learning mengenai analisis dan prediksi kemungkinan seorang Data Scientist untuk mencari atau berpindah pekerjaan berdasarkan faktor-faktor yang terdapat dalam data HR menggunakan Python.

---

## Informasi Mahasiswa

1. **Nama**: Inaya Salsabila
2. **Universitas**: Universitas Pamulang
3. **Kelas**: 05TPLP022

---

## Tentang Proyek

Proyek ini bertujuan untuk menganalisis data HR dan membangun model Machine Learning yang dapat memprediksi kemungkinan seorang kandidat Data Scientist untuk mencari atau berpindah pekerjaan (*job change*).

Dataset yang digunakan terdiri dari data training dan testing:
- `aug_train.csv` → Dataset untuk proses training
- `aug_test.csv` → Dataset untuk pengujian

Proses proyek meliputi:
1. Data Preprocessing & Handling Missing Values
2. Exploratory Data Analysis (EDA)
3. Feature Encoding (Label Encoding) & Correlation Analysis
4. Pemodelan Machine Learning (Lars, Linear Regression, Gradient Boosting Regressor)
5. Evaluasi Model (MAE, MSE, $R^2$)
6. Penyimpanan Model (`.joblib` & `.pkl`)
7. Deployment Model Menggunakan Flask REST API

---

## Dataset

Dataset berisi informasi mengenai kandidat Data Scientist, antara lain:
- `enrollee_id`: ID unik kandidat
- `city`: Kode kota kandidat
- `city_development_index`: Indeks pembangunan kota tempat tinggal kandidat
- `gender`: Jenis kelamin kandidat
- `relevant_experience`: Pengalaman kerja yang relevan di bidang data
- `enrolled_university`: Jenis program kuliah/pendidikan yang sedang ditempuh (jika ada)
- `education_level`: Jenjang pendidikan tertinggi (Graduate, Masters, Phd, dll.)
- `major_discipline`: Jurusan pendidikan
- `experience`: Total tahun pengalaman kerja
- `company_size`: Jumlah karyawan pada perusahaan tempat kandidat bekerja saat ini
- `company_type`: Jenis perusahaan/organisasi
- `last_new_job`: Jarak tahun antara pekerjaan saat ini dengan pekerjaan sebelumnya
- `training_hours`: Jumlah jam pelatihan yang telah diselesaikan
- `target`: `0` = Tidak mencari pekerjaan baru, `1` = Mencari pekerjaan baru / berniat pindah kerja

### Sumber Dataset
Dataset yang digunakan dalam proyek ini berasal dari Kaggle:
- **Nama Dataset**: *HR Analytics: Data Scientist Job Change Factors*
- **Platform**: Kaggle
- **Link Dataset**: [https://www.kaggle.com/datasets/obaidhere/hr-analytics-data-scientist-job-change-factors](https://www.kaggle.com/datasets/obaidhere/hr-analytics-data-scientist-job-change-factors)

---

## Teknologi yang Digunakan

1. Python 3
2. Jupyter Notebook
3. Pandas & NumPy (Manipulasi Data)
4. Matplotlib & Seaborn (Visualisasi Data)
5. Scikit-learn (Machine Learning & Evaluasi Metrik)
6. Flask (Framework REST API)
7. Joblib & Pickle (Model Serialization)

---

## 📌 Evaluasi Model: Apakah MAE, MSE, dan R² Harus Mendekati 1?

> ###  Ringkasan Jawaban:
> - **MAE** : **TIDAK**, nilai MAE harus **mendekati 0** (semakin kecil, semakin baik).
> - **MSE** : **TIDAK**, nilai MSE harus **mendekati 0** (semakin kecil, semakin baik).
> - **R² (R-Squared)** : ✔️ **YA**, nilai R² harus **mendekati 1** (semakin mendekati 1, semakin baik).

### Perbandingan Ringkas Metrik Evaluasi

| Metrik Evaluasi | Nama Panjang | Definisi & Karakteristik | Nilai Ideal | Alasan |
| :--- | :--- | :--- | :---: | :--- |
| **MAE** | *Mean Absolute Error* | Rata-rata selisih absolut antara nilai aktual dan nilai prediksi. | **Mendekati 0** | Mengukur besarnya error/kesalahan. Nilai 0 berarti tebakan model sempurna tanpa kesalahan sama sekali. |
| **MSE** | *Mean Squared Error* | Rata-rata kuadrat selisih antara nilai aktual dan nilai prediksi. | **Mendekati 0** | Merupakan fungsi kerugian (*loss metric*). Selisih dikuadratkan sehingga penalti pada kesalahan besar makin tinggi. Makin kecil nilainya, makin minim error ekstrem. |
| **R²** | *Coefficient of Determination* | Proporsi varians variabel dependen (target) yang berhasil dijelaskan oleh fitur independen. | **Mendekati 1** | Mengukur kecocokan garis regresi (*goodness of fit*). Nilai 1 (atau 100%) berarti model menjelaskan variasi data secara sempurna. |

---


### 📚 Referensi Bacaan — Teori Evaluasi Model

Berikut adalah referensi artikel ilmiah dan sumber teoritis yang mendasari penggunaan metrik evaluasi **MAE**, **MSE**, dan **R²** dalam proyek ini:

1. **Willmott, C. J., & Matsuura, K. (2005)**. *Advantages of the mean absolute error (MAE) over the root mean square error (RMSE) in assessing average model performance.* **Climate Research**, 30(1), 79–82.
   - 🔗 [https://doi.org/10.3354/cr030079](https://doi.org/10.3354/cr030079)
   - **Relevansi:** Artikel ini membahas kelebihan MAE dibandingkan RMSE sebagai metrik evaluasi rata-rata kesalahan prediksi model, dan mengapa MAE yang semakin kecil (mendekati 0) mencerminkan model yang lebih akurat.

2. **Chai, T., & Draxler, R. R. (2014)**. *Root mean square error (RMSE) or mean absolute error (MAE)? – Arguments against avoiding RMSE in the literature.* **Geoscientific Model Development**, 7(3), 1247–1250.
   - 🔗 [https://doi.org/10.5194/gmd-7-1247-2014](https://doi.org/10.5194/gmd-7-1247-2014)
   - **Relevansi:** Mengkaji perbedaan antara MAE dan MSE/RMSE, termasuk penjelasan mengapa MSE memberikan penalti lebih besar pada kesalahan ekstrem (outlier) akibat operasi kuadrat, serta kapan masing-masing metrik paling tepat digunakan.

3. **Cameron, A. C., & Windmeijer, F. A. G. (1997)**. *An R-squared measure of goodness of fit for some common nonlinear regression models.* **Journal of Econometrics**, 77(2), 329–342.
   - 🔗 [https://doi.org/10.1016/S0304-4076(96)01818-0](https://doi.org/10.1016/S0304-4076(96)01818-0)
   - **Relevansi:** Artikel ini membahas koefisien determinasi ($R^2$) sebagai ukuran *goodness of fit* model regresi — termasuk interpretasi nilai $R^2$ yang semakin mendekati 1 sebagai indikator kemampuan model dalam menjelaskan variasi data target.

4. **Friedman, J. H. (2001)**. *Greedy function approximation: A gradient boosting machine.* **The Annals of Statistics**, 29(5), 1189–1232.
   - 🔗 [https://doi.org/10.1214/aos/1013203451](https://doi.org/10.1214/aos/1013203451)
   - **Relevansi:** Paper seminal yang memperkenalkan algoritma **Gradient Boosting**, landasan teoritis dari model **Gradient Boosting Regressor (GBR)** yang dipilih sebagai model terbaik dalam proyek ini berdasarkan nilai MAE, MSE, dan R² yang optimal.

---

## 📊 Hasil Evaluasi Model pada Notebook

Pada notebook praktikum [`Praktikum_dataset_HR_Analytic.ipynb`](./Praktikum_dataset_HR_Analytic.ipynb), dilakukan pengujian terhadap 3 algoritma regresi:
1. **Least Angle Regression (Lars)**
2. **Linear Regression (LR)**
3. **Gradient Boosting Regressor (GBR)**

Berikut adalah tabel hasil evaluasinya pada test set:

| Model | MAE | MSE | R² Score | Evaluasi |
| :--- | :---: | :---: | :---: | :---: |
| **Least Angle Regression (Lars)** | 0.372417 | 0.185469 | 0.003864 | Performa terendah ($R^2$ mendekati 0) |
| **Linear Regression** | 0.312582 | 0.155192 | 0.166479 | Cukup baik |
| **Gradient Boosting Regressor (GBR)** | **0.281609** | **0.139597** | **0.250236** | 🏆 **Model Terbaik** |

### 🏆 Mengapa Gradient Boosting Regressor (GBR) Dipilih?
Dari tabel di atas terlihat jelas bahwa **Gradient Boosting Regressor** adalah algoritma terbaik:
1. **MAE paling rendah (0.281609)** $\rightarrow$ paling mendekati 0, artinya rata-rata kesalahan prediksi paling minim.
2. **MSE paling rendah (0.139597)** $\rightarrow$ paling mendekati 0, artinya kesalahan kuadrat paling kecil dan minim outlier error.
3. **$R^2$ paling tinggi (0.250236)** $\rightarrow$ paling mendekati 1, mampu menjelaskan sekitar 25% variasi data target, mengungguli model linear lainnya secara signifikan.

> **Catatan:** Nilai MAE dan MSE berada di kisaran 0.14 - 0.28 karena variabel target adalah biner (0 dan 1) yang dimodelkan secara kontinu untuk menghasilkan skor probabilitas kemungkinan berpindah kerja.

---

## 💾 Penyimpanan Model

Model Gradient Boosting Regressor yang telah dilatih disimpan menggunakan library `joblib` dan `pickle`:
- `gbr_model.joblib`
- `gbr_model.pkl`

---

## 🚀 Deployment dan Pengujian REST API

Model Machine Learning di-deploy menggunakan framework **Flask** agar dapat diakses melalui HTTP request.

### 1. Struktur File API
File aplikasi API: [`python app.py`](./python%20app.py)

```python
from flask import Flask, request, jsonify
import joblib

app = Flask(__name__)
joblib_model = joblib.load('gbr_model.joblib')

@app.route('/predict', methods=['POST'])
def predict():
    data = request.json['data']
    prediction = joblib_model.predict(data)
    return jsonify({'prediction': prediction.tolist()})

@app.route('/')
def home():
    return 'API Machine Learning Berhasil Berjalan!'

if __name__ == '__main__':
    app.run(debug=False, use_reloader=False)
```

### 2. Menjalankan Server Flask
```bash
python "python app.py"
```

### 3. Menguji Endpoint Prediksi
Kirim HTTP POST request ke `http://127.0.0.1:5000/predict` dengan 13 fitur input:

**Body Request (`request.json`):**
```json
{
  "data": [[
    0.025, -0.917, 0.798, 0.004, -0.190, -0.523, 0.123, -0.456, 0.789,
    0.101, -0.112, 0.131, -0.415
  ]]
}
```

**Respon API:**
```json
{
  "prediction": [
    0.2874136612702758
  ]
}
```
*(Nilai prediksi kontinu menunjukkan estimasi kecenderungan/probabilitas kandidat berpindah pekerjaan).*
