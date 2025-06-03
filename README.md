# Laporan Proyek Machine Learning - Nama Anda

## Project Overview

Dalam era digital saat ini, industri hiburan mengalami lonjakan signifikan dalam produksi dan distribusi konten, khususnya film. Platform streaming seperti Netflix, Amazon Prime Video, dan Disney+ menawarkan ribuan judul film yang dapat diakses kapan saja. Namun, kelimpahan pilihan ini sering kali menyebabkan fenomena "information overload," di mana pengguna merasa kewalahan dalam memilih konten yang sesuai dengan preferensi mereka [1]. Untuk mengatasi tantangan ini, sistem rekomendasi film dikembangkan guna membantu pengguna menemukan konten yang relevan dan sesuai dengan selera mereka. Sistem ini memanfaatkan algoritma seperti collaborative filtering, content-based filtering, dan pendekatan hibrida untuk menganalisis data pengguna dan memberikan rekomendasi yang dipersonalisasi . Namun, implementasi sistem rekomendasi tidak lepas dari berbagai tantangan, seperti masalah "cold start" yang terjadi ketika sistem kesulitan memberikan rekomendasi kepada pengguna baru yang belum memiliki riwayat interaksi [2]. Selain itu, aspek kepercayaan dan transparansi dalam sistem rekomendasi menjadi perhatian utama. Pengguna cenderung lebih menerima rekomendasi yang disertai dengan penjelasan yang jelas dan mudah dipahami. Penelitian menunjukkan bahwa penjelasan yang sederhana dan positif dalam rekomendasi film dapat meningkatkan kepercayaan dan kepuasan pengguna . Di sisi lain, kurangnya transparansi dapat menyebabkan "algorithm aversion," di mana pengguna enggan mempercayai hasil rekomendasi yang diberikan oleh sistem [3].Dalam konteks ini, pengembangan sistem rekomendasi film yang efektif dan terpercaya menjadi penting untuk meningkatkan pengalaman pengguna dalam menjelajahi konten hiburan. Dengan mengintegrasikan pendekatan berbasis data dan mempertimbangkan aspek psikologis pengguna, sistem rekomendasi dapat memberikan nilai tambah yang signifikan dalam membantu pengguna menemukan film yang sesuai dengan preferensi mereka.

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.
## Daftar Pustaka
[1] Nanou, T., Lekakos, G. & Fouskas, K. The effects of recommendations’ presentation on persuasion and satisfaction in a movie recommender system. Multimedia Systems 16, 219–230 (2010). https://doi.org/10.1007/s00530-010-0190-0

[2] Jayalakshmi, S.; Ganesh, N.; Čep, R.; Senthil Murugan, J. Movie Recommender Systems: Concepts, Methods, Challenges, and Future Directions. Sensors 2022, 22, 4904. https://doi.org/10.3390/s22134904

[3] Ahmad, Juan, Jonas Hellgren, and Alan Said. "Tell Me the Good Stuff: User Preferences in Movie Recommendation Explanations." arXiv preprint arXiv:2505.03376 (2025).
