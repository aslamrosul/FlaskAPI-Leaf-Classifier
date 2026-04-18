# FlaskAPI-Leaf-Classifier

Aplikasi Flask sederhana untuk klasifikasi bentuk daun menggunakan model SVM dan ekstraksi fitur gambar. API ini menerima unggahan gambar daun, memprosesnya dengan fitur HOG dan HSV, lalu mengembalikan prediksi salah satu kelas bentuk daun.

## Fitur

- Endpoint `POST /predict` untuk prediksi bentuk daun dari gambar
- Pra-pemrosesan gambar menggunakan filter homomorfik, deteksi tepi, dan koreksi gamma
- Ekstraksi fitur campuran HOG + HSV
- Model SVM yang dilatih dengan `joblib`

## Kelas Prediksi

- `melengkung`
- `menjari`
- `menyirip`
- `sejajar`

## Instalasi

1. Buat virtual environment:

   ```bash
   python -m venv venv
   ```

2. Aktifkan virtual environment:

   - Linux / macOS:
     ```bash
     source venv/bin/activate
     ```

   - Windows:
     ```powershell
     .\venv\Scripts\Activate
     ```

3. Install dependensi:

   ```bash
   pip install -r requirements.txt
   ```

## Menjalankan Aplikasi

```bash
python app.py
```

Aplikasi akan berjalan pada `http://0.0.0.0:5000`.

## Contoh Penggunaan API

Endpoint:

```http
POST /predict
```

Kirim file gambar menggunakan form-data dengan key `image`.

Contoh CURL:

```bash
curl -X POST http://localhost:5000/predict \
  -F "image=@/path/to/leaf.jpg"
```

Respon JSON:

```json
{
  "prediction": "menyirip"
}
```

## Catatan

- Pastikan file `svm_daun_model.pkl` tersedia di direktori yang sama dengan `app.py`.
- API ini dirancang untuk pengenalan bentuk daun, bukan untuk klasifikasi spesies.

## Dependensi

- Flask
- Flask-CORS
- numpy
- opencv-python-headless
- scikit-image
- scikit-learn
- joblib
