# UTS Computer Vision – Ekstraksi Fitur (SIFT & ORB)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/UTS-Computer-Vision/blob/main/notebooks/UTS_Kelompok.ipynb)

Tugas UTS mata kuliah Computer Vision, Semester Ganjil 2026/2027.
Pipeline: peningkatan kualitas citra low-light, filtering, evaluasi MSE/PSNR, lalu ekstraksi fitur SIFT dan ORB beserta feature matching.

## Anggota Kelompok

| Nama | Peran | Bagian |
| --- | --- | --- |
| Maulana Ferdiansyah Eka Putra | Koordinator & integrasi | Section 0-1 (setup, dataset), integrasi, paket final |
| Ahmad Mirza Rafiq Azmi | Bagian A1 | Section 2: grayscale, Histogram Equalization, Contrast Stretching, CLAHE |
| Datok Radja Mulya | Bagian A2 | Section 3: filtering, MSE, PSNR, tabel rata-rata |
| Dezilva Zafiaska Setyano | Bagian B | Section 4: SIFT, ORB, feature matching, perbandingan |
| Thalita Putri Kaylaluna | Laporan | Section 5 dan laporan |

## Dataset

- **Sumber:** [LOL Dataset (Kaggle)](https://www.kaggle.com/datasets/soumikrakshit/lol-dataset), folder `our485/low` (citra gelap) dengan pasangan `our485/high` sebagai citra referensi.
- **Subset:** 25 citra dipilih acak dari 485 citra.
- **Seed acak:** `12` (`random.seed(12)`), sehingga subset dapat direproduksi.
- **Ukuran:** semua citra di-resize seragam ke 600x400 piksel (`INTER_AREA`).
- **Format internal:** BGR, `uint8` (bawaan OpenCV).
- Dataset diunduh otomatis di notebook lewat `kagglehub`, tanpa unduhan manual dan tanpa API key. Salinan 25 citra yang dipakai ada di folder `data/`.


## Struktur Notebook

| Section | Isi |
| --- | --- |
| 0-1 | Setup, seed, unduh dataset, pilih subset, resize |
| 2 | Grayscale, Histogram Equalization, Contrast Stretching, CLAHE |
| 3 | Filtering, MSE, PSNR, tabel rata-rata |
| 4 | SIFT, ORB, feature matching, jumlah keypoint dan waktu |
| 5 | Ringkasan hasil dan kesimpulan |

Fungsi utama (semua menerima dan mengembalikan array NumPy `uint8`):

- Section 2: `to_gray`, `hist_eq`, `contrast_stretch`, `clahe`
- Section 3: `apply_filter`, `mse`, `psnr`
- Section 4: `extract_sift`, `extract_orb`, `match`

## Parameter

| Parameter | Nilai |
| --- | --- |
| Seed | 12 |
| Jumlah citra | 25 |
| Ukuran citra | 600x400 |
| Filter | median, ukuran kernel 3 (`FILTER_METHOD`, `KSIZE` di Section 3) |

## Cara Menjalankan

1. Klik badge **Open in Colab** di atas.
2. Pilih **Runtime > Run all** (atau **Restart session and run all** untuk uji dari nol).
3. Cell pertama mengunduh dataset dari Kaggle secara otomatis, jadi tunggu beberapa menit saat pertama kali dijalankan.

Library yang dipakai (sudah tersedia di Colab): `opencv-python`, `numpy`, `pandas`, `matplotlib`, dan `kagglehub` (`pip install kagglehub` jika belum ada).

Catatan: tampilan gambar memakai `matplotlib`, bukan `cv2.imshow`, karena `imshow` tidak berjalan di Colab.
