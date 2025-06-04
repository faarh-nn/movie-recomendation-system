# Laporan Proyek Machine Learning - Muh Farhan

## Project Overview

Dalam era digital saat ini, industri hiburan mengalami lonjakan signifikan dalam produksi dan distribusi konten, khususnya film. Platform streaming seperti Netflix, Amazon Prime Video, dan Disney+ menawarkan ribuan judul film yang dapat diakses kapan saja. Namun, kelimpahan pilihan ini sering kali menyebabkan fenomena "information overload," di mana pengguna merasa kewalahan dalam memilih konten yang sesuai dengan preferensi mereka [1]. Untuk mengatasi tantangan ini, sistem rekomendasi film dikembangkan guna membantu pengguna menemukan konten yang relevan dan sesuai dengan selera mereka. Sistem ini memanfaatkan algoritma seperti collaborative filtering, content-based filtering, dan pendekatan hibrida untuk menganalisis data pengguna dan memberikan rekomendasi yang dipersonalisasi . Namun, implementasi sistem rekomendasi tidak lepas dari berbagai tantangan, seperti masalah "cold start" yang terjadi ketika sistem kesulitan memberikan rekomendasi kepada pengguna baru yang belum memiliki riwayat interaksi [2]. Selain itu, aspek kepercayaan dan transparansi dalam sistem rekomendasi menjadi perhatian utama. Pengguna cenderung lebih menerima rekomendasi yang disertai dengan penjelasan yang jelas dan mudah dipahami. Penelitian menunjukkan bahwa penjelasan yang sederhana dan positif dalam rekomendasi film dapat meningkatkan kepercayaan dan kepuasan pengguna . Di sisi lain, kurangnya transparansi dapat menyebabkan "algorithm aversion," di mana pengguna enggan mempercayai hasil rekomendasi yang diberikan oleh sistem [3].Dalam konteks ini, pengembangan sistem rekomendasi film yang efektif dan terpercaya menjadi penting untuk meningkatkan pengalaman pengguna dalam menjelajahi konten hiburan. Dengan mengintegrasikan pendekatan berbasis data dan mempertimbangkan aspek psikologis pengguna, sistem rekomendasi dapat memberikan nilai tambah yang signifikan dalam membantu pengguna menemukan film yang sesuai dengan preferensi mereka.

## Business Understanding

Berdasarkan latar belakang yang diuraikan di atas, problem statements dari projek ini adalah sebagai berikut:

### Problem Statements

- Pengguna kesulitan menemukan film yang sesuai dengan preferensi pribadi mereka di antara ribuan pilihan yang tersedia.
- Perlunya pengembangan sistem personalisasi yang mempertimbangkan kebiasaan menonton pengguna dan kesamaan konten antarfilm.

### Goals
Berdasarkan problem statements yang diuraikan di atas, goals dari pojek ini adalah sebagai berikut:
- Membangun sistem rekomendasi film yang mampu memahami preferensi pengguna berdasarkan riwayat penilaian mereka terhadap film.
- Menyediakan rekomendasi film berdasarkan kemiripan konten seperti genre dan karakteristik naratif film.
## Solution statements
- Menerapkan metode Content-Based Filtering dengan pendekatan TF-IDF dan cosine similarity untuk memberikan rekomendasi berdasarkan kemiripan konten antarfilm.
- Menerapkan metode Collaborative Filtering untuk menganalisis pola interaksi antara pengguna dan film guna mempersonalisasi rekomendasi.

## Data Understanding
Dataset yang digunakan pada projek ini dapat diakses pada tautan berikut:
[Kaggle](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset?select=ratings.csv)

Dari tautan di atas, data yang digunakan pada projek ini hanya dua, yaitu **movies_metadata.csv** dan **ratings_small.csv**.

Secara umum, dataset ini berisi metadata untuk semua 45.000 film yang tercantum dalam Dataset Full MovieLens. Dataset ini terdiri dari film yang dirilis pada atau sebelum Juli 2017. Poin data termasuk pemeran, kru, kata kunci plot, anggaran, pendapatan, poster, tanggal rilis, bahasa, perusahaan produksi, negara, jumlah suara TMDB, dan rata-rata suara. Dataset ini juga memiliki file yang berisi 26 juta peringkat dari 270.000 pengguna untuk 45.000 film. Peringkat berada pada skala 1-5 dan diperoleh dari situs web resmi GroupLens.

### Dataset Movies (movies_metadata.csv)
Dataset **movies_metadata.csv** terdiri dari 45466 obsrvasi dan 24 fitur dengan rincian sebagai berikut:

![dataset_movies](https://github.com/user-attachments/assets/f85994f0-6167-4c03-92d1-972dc5fd1a59)
#### Penjelasan dari masing-masing fitur dataset movies_metadata.csv di atas adalah sebagai berikut:
- **adult**: Mengindikasikan apakah film tersebut untuk orang dewasa (adult content). Nilainya biasanya True atau False.
- **belongs_to_collection**: Informasi tentang koleksi atau seri film tertentu yang mencakup film ini (misalnya, film dalam seri Harry Potter). Biasanya berupa JSON atau string deskriptif.
- **budget**: Anggaran produksi film dalam satuan mata uang (biasanya USD). Nilainya berupa angka.
- **genres**: Daftar genre film, seperti Action, Comedy, Drama. Biasanya berupa JSON atau daftar string.
- **homepage**: URL dari situs web resmi film tersebut.
- **id**: ID unik untuk film, biasanya merujuk pada database film tertentu seperti TMDb.
- **imdb_id**: ID unik dari film di IMDb (misalnya, tt1234567).
- **original_language**: Bahasa asli film tersebut dalam format kode bahasa ISO 639-1 (misalnya, en untuk bahasa Inggris).
- **original_title**: Judul asli film dalam bahasa produksinya.
- **overview**: Ringkasan atau deskripsi singkat mengenai plot film.
- **popularity**: Skor popularitas film berdasarkan sistem tertentu, sering dihitung menggunakan algoritma dari platform film.
- **poster_path**: Path atau tautan menuju gambar poster film. Biasanya berupa path yang dapat digabungkan dengan URL dasar untuk akses.
- **production_companies**: Informasi tentang perusahaan produksi film tersebut. Biasanya berupa JSON dengan nama dan ID perusahaan.
- **production_countries**: Negara tempat film tersebut diproduksi. Biasanya berupa JSON dengan nama negara dan kode negara.
- **release_date**: Tanggal rilis film (format: YYYY-MM-DD).
- **revenue**: Pendapatan kotor yang diperoleh film (biasanya dalam USD).
- **runtime**: Durasi film dalam menit.
- **spoken_languages**: Bahasa yang digunakan dalam dialog film. Biasanya berupa JSON dengan nama dan kode bahasa.
- **status**: Status rilis film (misalnya, Released, In Production).
- **tagline**: Slogan atau frasa singkat yang biasanya digunakan untuk promosi film.
- **title**: Judul utama film yang digunakan untuk promosi.
- **video**: Mengindikasikan apakah ada video terkait film. Nilainya biasanya berupa True atau False.
- **vote_average**: Nilai rata-rata yang diberikan oleh pengguna (misalnya dari IMDb atau TMDb) berdasarkan skala tertentu (biasanya 1-10).
- **vote_count**: Jumlah suara atau ulasan yang diberikan untuk film tersebut.
#### Inspeksi Distribusi Genre Film
Dalam proses data understanding ini, dilakukan inspeksi distribusi frekuensi genre film untuk mengetahui jenis-jenis film yang paling populer. Visualisasinya disajikan sebagai berikut:

![distribusi-genre-film](https://github.com/user-attachments/assets/2f6c7d4e-ba0d-4b7d-bb93-8a3f12115e01)

Berdasarkan visualisasi di atas, terlihat bahwa genre Drama mendominasi secara signifikan dengan lebih dari 20.000 kemunculan, diikuti oleh Comedy dan Thriller. Genre populer lainnya termasuk Romance, Action, dan Horror.
#### Identifikasi Film Top Berdasarkan Kombinasi Rating dan Jumlah Votes
Berikutnya dilakukan juga identifikasi film top berdasarkan kombinasi rating dan jumlah votes dengan output berupa tabel sebagai berikut:
| id     | genres                             | title                        | vote_average | vote_count | weighted_score |
|--------|------------------------------------|------------------------------|---------------|------------|----------------|
| 19404  | [Comedy, Drama, Romance]           | Dilwale Dulhania Le Jayenge | 9.1           | 661.0      | 8.929668       |
| 278    | [Drama, Crime]                     | The Shawshank Redemption     | 8.5           | 8358.0     | 8.488324       |
| 238    | [Drama, Crime]                     | The Godfather                | 8.5           | 6024.0     | 8.488326       |
| 372058 | [Romance, Animation, Drama]        | Your Name.                   | 8.5           | 1030.0     | 8.407913       |
| 155    | [Drama, Action, Crime, Thriller]   | The Dark Knight              | 8.3           | 12269.0    | 8.292589       |

Tabel di atas menampilkan lima film dengan skor tertimbang (weighted score) tertinggi yang menunjukkan kombinasi yang seimbang antara tingginya rating rata-rata dan jumlah vote yang signifikan. Film Dilwale Dulhania Le Jayenge menempati peringkat pertama meskipun jumlah votenya tidak sebanyak film lain, karena memiliki rating sangat tinggi (9.1). Di sisi lain, The Shawshank Redemption, The Godfather, dan The Dark Knight mempertahankan posisi tinggi karena memiliki jumlah vote yang sangat besar, yang memperkuat pengaruh rating mereka dalam perhitungan skor tertimbang. Hasil ini menegaskan bahwa sistem rekomendasi mempertimbangkan tidak hanya seberapa baik film dinilai, tetapi juga seberapa banyak orang yang menilai film tersebut, untuk menghasilkan rekomendasi yang lebih adil dan representatif.

### Dataset Ratings (ratings_small.csv)
Kemmudian untuk dataset **ratings_small.csv** terdiri dari 100004 observasi dan 4 fitur dengan rincian sebagai berikut:

![dataset_ratings](https://github.com/user-attachments/assets/840e534c-6bda-48d7-ac6e-7d1a87ccfe2f)
#### Penjelasan dari masing-masing fitur dataset ratings_small.csv di atas adalah sebagai berikut:
- **userId**: ID unik untuk pengguna yang memberikan penilaian (rating). Ini digunakan untuk mengidentifikasi pengguna secara anonim.
- **movieId**: ID unik untuk film yang dinilai oleh pengguna untuk mendapatkan informasi lebih detail tentang film tersebut.
- **rating**: Nilai yang diberikan oleh pengguna untuk film tertentu dengan skala 1 hingga 5, di mana angka yang lebih tinggi menunjukkan penilaian yang lebih positif.
- **timestamp**: Waktu ketika penilaian diberikan, direpresentasikan dalam format UNIX timestamp (jumlah detik sejak 1 Januari 1970).
#### Identifikasi Distribusi Ratings
Khsusus pada dataset ratings, dilakukan identifikasi distribusi ratings melalui visualisasi untuk mengetahui sebaran frekuensi dari setiap rating yang ada sebagai berikut:

![distirbusi_ratings](https://github.com/user-attachments/assets/08cb8c31-4fe2-44e4-9993-2adf1c083f22)

Berdasarkan visualisasi di atas, diketahui bahwa mayoritas pengguna memberikan rating tinggi, dengan nilai 4.0 menjadi yang paling dominan (28.7%), diikuti oleh 3.0 (20.1%) dan 5.0 (15.1%). Sementara itu, rating rendah seperti 0.5, 1.0, dan 1.5 memiliki persentase yang sangat kecil, masing-masing hanya sekitar 1.1% hingga 3.3%. Pola ini menunjukkan bahwa sebagian besar pengguna cenderung memberikan penilaian positif, mencerminkan kemungkinan bias positif atau persepsi umum yang baik terhadap film-film dalam dataset ini.
#### Analisis Film Berdasarkan Rating
Berikutnya dilakukan analisis film berdasarkan rating untuk mengidentifikasi film yang sering ditonton dan mendapatkan tanggapan positif dari pengguna sebagai berikut.
| title                            | mean_ratings | total_ratings |
|----------------------------------|--------------|----------------|
| Terminator 3: Rise of the Machines | 4.256173    | 324            |
| The Million Dollar Hotel         | 4.487138     | 311            |
| Solaris                          | 4.134426     | 305            |
| The 39 Steps                     | 4.221649     | 291            |
| Monsoon Wedding                  | 3.706204     | 274            |
| Once Were Warriors               | 4.303279     | 244            |
| Three Colors: Red                | 3.945175     | 228            |
| Men in Black II                  | 4.256696     | 224            |
| The Passion of Joan of Arc       | 3.483945     | 218            |
| Silent Hill                      | 3.674419     | 215            |

Berdasarkan output di atas, terlihat bahwa film *Terminator 3: Rise of the Machines* berada di urutan teratas dengan 324 rating dan rata-rata skor 4.25, diikuti oleh *The Million Dollar Hotel* yang memiliki rata-rata skor tertinggi sebesar 4.49 dari 311 pengguna. Meskipun bukan film yang paling dikenal luas, film-film ini mendapat perhatian signifikan dari pengguna dan memiliki **penilaian rata-rata yang tergolong tinggi**, menunjukkan bahwa film-film ini cukup **populer dan diapresiasi positif oleh penonton**.

### Dataset Movies dan Ratings
#### Identifikasi Missing Value
Proses identifikasi missing value dilakukan baik pada dataset movies maupun pada dataset ratings. Namun, setelah dilakukan identifikasi, ternyata missing value hanya terdapat dataset movies dengan rincian disajikan pada tabel berikut:
| Nama Fitur    | Jumlah Missing Value | Persentase Missing Value | Tipe Data |
|---------------|----------------------|---------------------------|-----------|
| id            | 0                    | 0.000000                  | object    |
| genres        | 0                    | 0.000000                  | object    |
| title         | 6                    | 0.013197                  | object    |
| vote_average  | 6                    | 0.013197                  | float64   |
| vote_count    | 6                    | 0.013197                  | float64   |

Berdasarkan output di atas, terlihat bahwa terdapat tiga fitur yang memiliki missing value pada dataset movies, yaitu `title`, `vote_average`, dan `vote_count`. Namun persentase missing value dari masing-masing fitur tersebut relatif kecil yaitu dibawah 1%.

## Data Preparation
### Penyesuaian Dataset Movies
Dalam proses pembangunan model rekomendasi pada project ini, tidak semua fitur dari dataset movies diguakan, fitur yang digunakan hanya `id`, `genres`, `title`, `vote_average`, dan `vote_count`. Untuk itu dilakukan penyederhanaan fitur pada dataset movies dengan hanya menyertakan fitur-fitur tersebut.
### Penanganan Missing Value
Berdasarkan identifikasi missing value pada proses data understanding sebelumnya, diketahui bahwa terdapat tiga fitur yang memiliki missing value pada dataset movies, yaitu `title`, `vote_average`, dan `vote_count`. Namun karena persentase missing value dari masing-masing fitur tersebut relatif kecil yaitu dibawah 1%, maka langkah penanganan yang diambil adalah penghapusan observasi missing karena penghapusan observasi dengan jumlah yang kecil (misalnya di bawah 1%) tidak akan menimbulkan kehilangan informasi yang signifikan pada dataset.
### Penanganan Duplikasi Data
Proses identifikasi duplikasi data juga dilakukan baik pada dataset movies maupun dataset ratings. Namun, setelah proses identifikasi dilakukan, didapati bahwa duplikasi data hanya terdapat pada dataset movies sebanyak 28 observasi. Untuk itu langkah yang diambil adalah melakukan penghapusan data duplikat tersebut agar tidak terdapat noise pada saat proses training dilakukan.
### Penyesuaian Lanjutan pada Dataset Movies dan Dataset Ratings
Beberapa langkah penyesuaian lanjutan yang dilakukan pada dataset movies dan dataset ratings diuraikan sebagai berikut:
1. **Mengurutkan Dataset Berdasarkan ID**. Langkah ini dilakukan baik pada dataset movies maupun dataset ratings untuk mendukung proses shuffle atau pengacakan yang akan dilakukan tepat sebelum proses splitting data dilakukan. Proses pengurutan tersebut dilakukan agar pengacakan yang dilakukan nantinya memberikan hasil yang lebih robust dan relevan.
2. **Mengubah Fitur Genres pada Dataset Movies ke Dalam Bentuk List**. Proses ini dilakukan untuk memudahkan proses pemodelan nantinya, khususnya pada fitur `genres`.
3. **Menggabungkan Data Movies dan Ratings**. Proses penggabungan ini dilakukan agar proses pemodelan yang akan dilakukan nantinya bisa dijalankan secara efisien terhadap satu dataset saja. Selain itu, penggabungan ini juga membuat informasi movies dan informasi ratings menjadi terintegrasi karena proses penggabungan dilakukan secara `inner join` berdasarkan `movieId`.
4. **Penyederhanaan Dataset**. Dari dataset hasil penggabungan sebelumnya, fitur-fitur yang akan digunakan dalam proses pembangunan model rekomendasi adalah `userId`,	`movieId`, `rating`, `genres`, dan `title`. Untuk itu, fitur-fitur di luar tersebut dieliminasi untuk mendukung efisiensi proses pembangunan model.
5. **Sampling Data**. Kemudian karena jumlah data atau observasi yang terdapat dalam dataset terlalu banyak (44989 observasi), akan dilakukan sampling secara acak dengan jumlah sebesar 20000 observasi. Langkah ini diambil untuk memastikan proses pemomdelan bisa berjalan dengan lancar dan efisien dan tidak crash akibat dari jumlah observasi yang terlalu tinggi. Proses sampling dialankan menggunakan fungsi `shuffle` dari library `sklearn.utils`
6. **Encoding moviesId dan userId**. Proses encoding pada fitur `userId` dan `movieId` dilakukan untuk menghindari bias pada model yang menganggap angka besar memiliki arti numerik lebih besar — padahal dalam konteks ID, tidak ada arti seperti itu. Encoding mengubah ID menjadi representasi numerik yang berurutan dan netral, sehingga dapat digunakan sebagai indeks dalam embedding layer untuk menangkap hubungan laten antara pengguna dan film. Selain itu, encoding membantu menghindari sparsity dan meningkatkan efisiensi komputasi, terutama saat bekerja dengan dataset berskala besar.

### Split Data Menjadi Training Set dan Validation Set
Sebelum proses splitting data dilakukan, terlebih dahulu diidentifikasi `total_user`, `total_movies`, `min_rating`, dan `max_rating`. Item `total_user` dan `total_movies` nantinya akan digunakan saat membangun model rekomendasi, khususnya dalam mendefinisikan ukuran input dan output dari embedding layer. Jumlah ini merepresentasikan dimensi maksimum dari user ID dan movie ID yang digunakan oleh model. Sedangkan `min_rating` dan `max_rating` nantinya digunakan untuk melakukan min-max normalization pada kolom rating agar nilai rating berada pada skala yang seragam (0 hingga 1). Hal ini dilakukan agar model dapat memproses data rating dengan stabil dan lebih cepat. **Dalam proses penentuan `min_rating` dan `max_rating` dilakukan juga proses konversi tipe data `ratings` yang awalnya berupa float64 menjadi float32. Hal ini dilakukan untuk meningkatkan efisiensi komputasi dan menghemat penggunaan memori.**

Berikutnya, dilakukan pengacakan pada dataset untuk menghindari bias urutan data sebelum proses split (pembagian) menjadi data pelatihan dan validasi. Jika data tidak diacak, urutannya bisa saja terstruktur (misalnya berdasarkan user tertentu atau film tertentu), yang bisa menyebabkan model belajar dari pola yang tidak mewakili keseluruhan data. Dengan pengacakan, data yang digunakan untuk pelatihan dan validasi menjadi lebih beragam dan acak, sehingga meningkatkan generalisasi model saat diterapkan ke data baru. **Setelah itu, barulah proses splitting data dengan proporsi 80% untuk training dan 20% untuk validasi**

### Data Preparation Khusus untuk Content Based Filtering
Terdapat beberapa penyesuaian khusus yang dilakukan pada dataset untuk mendukung pembangunan sistem rekomendasi dengan pendekatan **content based filtering**. Pertama-tama dilakukan ekstraksi tiga kolom penting dari dataframe `df_sample_final`, yaitu movieId, title, dan genres, lalu mengonversinya menjadi list terpisah. Ketiga list tersebut kemudian digunakan untuk membuat dataframe baru bernama cdbf_df yang menyusun ulang informasi film ke dalam format yang lebih ringkas, terdiri dari kolom id, movie_name, dan genres. Contoh output 5 data pertamanya adalah sebagai berikut:
| id    | movie_name                                | genres                          |
|-------|--------------------------------------------|----------------------------------|
| 2454  | The Chronicles of Narnia: Prince Caspian   | [Adventure, Family, Fantasy]    |
| 541   | The Man with the Golden Arm                | [Crime, Drama, Romance]         |
| 661   | The Marriage of Maria Braun                | [War, Drama]                    |
| 223   | Rebecca                                    | [Drama, Mystery]                |
| 74727 | Long Pigs                                  | [Crime, Horror]                 |

Berikutnya dilakukan proses ekstraksi fitur berbasis konten dari data genre film untuk keperluan sistem rekomendasi berbasis konten (content-based filtering). Pertama, kolom genres pada cbf_df diproses ulang agar setiap daftar genre diubah menjadi satu string yang dipisahkan koma. Hal ini dilakukan karena TfidfVectorizer hanya dapat memproses teks dalam bentuk string, bukan list. Setelah itu, TfidfVectorizer() digunakan untuk membangun representasi fitur berdasarkan teknik TF-IDF (Term Frequency–Inverse Document Frequency), yang mengukur pentingnya kata (dalam hal ini genre) dalam seluruh kumpulan data. Metode .fit() menyesuaikan vektorizer dengan data genre, lalu .get_feature_names_out() menampilkan daftar genre unik sebagai fitur. Kemudian, .fit_transform() digunakan untuk mengubah data genre menjadi matriks TF-IDF, di mana setiap baris merepresentasikan sebuah film dan setiap kolom merepresentasikan bobot kemunculan genre tertentu. Matriks ini akhirnya dikonversi ke bentuk dense (padat) menggunakan .todense() agar lebih mudah diamati dan dianalisis.

## Modeling
Pada projek ini model sisten rekomendasi dibuat dengan dua pendekatan, yaitu **Content Based Filtering** dan **Collaborative Filtering**. Rinciannya adalah sebagai berikut:
### Content Based Filtering
Pada pendekatan ini, metrik utama yang digunakan untuk menghasilkan rekomendasi film adalah **cosine-similarity**. Metrik ini mengukur kesamaan semantik dari genre film yang dipilih oleh pengguna sehingga dapat diperoleh rekomendasi film dengan genre yang mirip atau sesuai dengan film yang disukai oleh pengguna. Penghitungan metrik cosine similarity tersebut dilakukan pada representase vektor genre film yang diperoleh dengan menerapkan TF-IDF seperti yang telah dijelaskan pada bagian **data preparation** sebelumnya. Contoh ouput similarity genre untuk 10 film disajikan pada tabel berikut:
| movie_name                                      | Dollman vs. Demonic Toys | The Garden of the Finzi-Continis | A Chorus Line | Miller's Crossing | The Prize | Golden Door | The Life Aquatic with Steve Zissou | Forrest Gump | 20,000 Leagues Under the Sea | Blondie Has Servant Trouble |
|------------------------------------------------|---------------------------|----------------------------------|---------------|--------------------|-----------|--------------|------------------------------------|--------------|-----------------------------|------------------------------|
| The Life Aquatic with Steve Zissou             | 0.000000                  | 0.395119                         | 0.139037      | 0.158089           | 0.132946  | 0.125903     | 1.000000                           | 0.487409     | 0.506927                    | 0.550954                     |
| My Darling Clementine                          | 0.000000                  | 0.319990                         | 0.112571      | 0.127997           | 0.107640  | 0.101938     | 0.126402                           | 0.134030     | 0.092005                    | 0.000000                     |
| Dust Devil                                     | 0.411826                  | 0.000000                         | 0.000000      | 0.261894           | 0.480971  | 0.000000     | 0.000000                           | 0.000000     | 0.000000                    | 0.000000                     |
| Two Moon Junction                              | 0.000000                  | 0.516213                         | 0.181648      | 0.206539           | 0.173690  | 0.617275     | 0.203965                           | 0.811608     | 0.148461                    | 0.000000                     |
| Cool Runnings                                  | 0.000000                  | 0.000000                         | 0.000000      | 0.000000           | 0.000000  | 0.000000     | 0.550954                           | 0.584202     | 0.000000                    | 1.000000                     |
| In the Name of the King: A Dungeon Siege Tale  | 0.466723                  | 0.289522                         | 0.101879      | 0.115839           | 0.097416  | 0.092255     | 0.510321                           | 0.121299     | 0.371449                    | 0.000000                     |
| Moon 44                                        | 0.596158                  | 0.000000                         | 0.000000      | 0.000000           | 0.000000  | 0.000000     | 0.000000                           | 0.000000     | 0.794369                    | 0.000000                     |
| Bedevilled                                     | 0.425587                  | 0.309636                         | 0.108956      | 0.773889           | 0.423206  | 0.098664     | 0.122343                           | 0.129726     | 0.089050                    | 0.000000                     |
| Forbidden Planet                               | 0.597437                  | 0.000000                         | 0.000000      | 0.000000           | 0.000000  | 0.000000     | 0.369311                           | 0.100000     | 0.861358                    | 0.000000                     |
| The Treasure of the Sierra Madre               | 0.142084                  | 0.251154                         | 0.088378      | 0.100488           | 0.084506  | 0.080029     | 0.442693                           | 0.105224     | 0.322224                    | 0.000000                     |

Rekomendasi final yang dihasilkan pada pendekatan **Content Based Filtering** ini didasarkan pada tingkat kemiripan genre berdasarkan metrik cosine similarity tersebut. Misalnya, untuk film berjudul **Angel Face**, diperoleh output **top-10** rekomendasi sebagai berikut:
| movie_name                      | genres                                      |
|--------------------------------|---------------------------------------------|
| Made in Hong Kong              | Crime, Drama, Romance                       |
| 3-Iron                         | Drama, Romance, Crime                       |
| The Man with the Golden Arm    | Crime, Drama, Romance                       |
| The Thomas Crown Affair        | Romance, Crime, Thriller, Drama             |
| The Thomas Crown Affair        | Drama, Crime, Romance                       |
| Schizo                         | Crime, Drama, Romance                       |
| Prizzi's Honor                 | Romance, Comedy, Crime, Drama               |
| Tie Me Up! Tie Me Down!        | Comedy, Crime, Drama, Romance               |
| Match Point                    | Drama, Thriller, Crime, Romance             |
| Young Adam                     | Drama, Thriller, Crime, Romance             |

Berdasarkan output yang ditampilkan, fungsi `film_recommendations('Angel Face')` memberikan daftar film yang direkomendasikan berdasarkan kemiripan genre dengan film **Angel Face**. Seluruh film yang direkomendasikan memiliki kombinasi genre yang serupa, yaitu dominan pada genre **Crime**, **Drama**, dan **Romance**. Beberapa film bahkan memiliki kombinasi keempat genre seperti **Thriller** atau **Comedy** yang mungkin juga terdapat pada film *Angel Face*.

#### Kelebihan Pendekatan Content Based Filtering
Pendekatan Content-Based Filtering memiliki kelebihan utama dalam kemampuannya memberikan rekomendasi yang personal dan relevan berdasarkan preferensi spesifik pengguna. Sistem ini bekerja dengan menganalisis karakteristik item yang sebelumnya disukai atau diinteraksikan oleh pengguna, seperti genre film, kata kunci dalam deskripsi produk, atau kategori artikel, lalu mencocokkannya dengan item lain yang memiliki fitur serupa. Keunggulan lainnya adalah kemampuannya untuk tetap berfungsi dengan baik meskipun jumlah pengguna terbatas, karena tidak tergantung pada interaksi antar pengguna. Selain itu, content-based filtering cenderung lebih transparan dalam memberikan penjelasan mengapa suatu item direkomendasikan. 

#### Kekurangan Pendekatan Content Based Filtering
Kekurangan dari pendekatan Content-Based Filtering adalah adanya keterbatasan dalam mengeksplorasi item baru yang berbeda dari histori preferensi pengguna, sehingga potensi munculnya rekomendasi yang monoton atau terlalu sempit (overspecialization) menjadi tinggi. Selain itu, sistem ini bergantung pada kualitas dan kedalaman fitur konten yang tersedia, sehingga performanya bisa menurun jika deskripsi item tidak memadai atau tidak terstruktur dengan baik.

### Collaborative Filtering
Pada pendekatan ini digunakan arsitektur RecommenderNet yang menggunakan pendekatan embedding untuk merepresentasikan pengguna dan film ke dalam vektor berdimensi tetap (embedding_size). Di dalamnya, terdapat layer embedding untuk user dan movie serta bias masing-masing, yang bertujuan menangkap karakteristik unik dari setiap entitas. Fungsi call() mengalikan vektor user dan movie menggunakan dot product untuk menghitung skor kesesuaian, lalu menambahkan bias dari user dan movie. Hasil akhirnya dikembalikan dalam bentuk probabilitas melalui fungsi aktivasi sigmoid, yang memetakan skor ke rentang 0–1 untuk memprediksi seberapa besar kemungkinan seorang user akan menyukai suatu film, berdasarkan pola interaksi yang telah dipelajari.

Model dibuat dengan parameter total_user, total_movies, dan embedding_size sebesar 50. Setelah itu, model dikompilasi dengan menggunakan fungsi loss Mean Squared Error (MSE) sebagai pengukur kesalahan utama, serta optimizer Adam dengan learning rate 0.001 untuk proses pembelajaran yang efisien dan adaptif. Selain itu, dua metrik evaluasi digunakan, yaitu Mean Absolute Error (MAE) dan Root Mean Squared Error (RMSE), untuk memberikan gambaran seberapa akurat prediksi model terhadap data sebenarnya. Pelatihan dilakukan selama maksimal 50 epoch dengan ukuran batch sebesar 8, dan data diacak (shuffle) di setiap epoch untuk meningkatkan generalisasi model. Selain itu, digunakan callback EarlyStopping yang akan menghentikan pelatihan lebih awal jika tidak ada peningkatan performa validasi selama 7 epoch berturut-turut, dengan toleransi perubahan minimum sebesar 0.0001.

Untuk menguji model rekomendasi yang telah dibangun sebelumnya, akan digunakan data **ratings_small.csv** yang menyimpan data rating user pada beberapa film yang telah mereka tonton. Pertama-tama, dibuat movies_df, yaitu DataFrame yang berisi informasi unik mengenai movieId, title, dan genres dari dataset yang sudah dibersihkan. Selanjutnya, diambil secara acak satu userId dari dataset rating, dan diidentifikasi daftar film yang telah ditonton oleh pengguna tersebut (movie_watch_by_user). Lalu, difilter film yang belum pernah ditonton oleh pengguna tersebut dan yang juga terdapat dalam dictionary encoding (movie_to_movie_encoded). Setiap movieId yang valid diubah menjadi bentuk encoded dan disusun sebagai input prediksi. Input ini dikombinasikan dengan user ID (dalam bentuk encoded) untuk membentuk user_movie_array, yaitu array pasangan user–movie yang siap diberikan ke model untuk menghasilkan skor prediksi rekomendasi.

Pada projek ini rekomendasi dilakukan pada user dengan **id: 552** yang memberikan rating tinggi pada 5 filem berikut ini:
| movie_name                         | genres                                      |
|-----------------------------------|---------------------------------------------|
| To Be or Not to Be                | Comedy, War                                 |
| Terminator 3: Rise of the Machines| Action, Thriller, Science Fiction           |
| The Poseidon Adventure            | Action, Adventure                           |
| True Romance                      | Action, Thriller, Crime, Romance            |
| Tron                              | Science Fiction, Action, Adventure          |

Berdasarkan informasi di atas, model rekomendasi memberikan **top-10** rekomendasi film sebagai berikut:
| No | movie_name              | genres                                      |
|----|-------------------------|---------------------------------------------|
| 1  | The 39 Steps            | Action, Thriller, Mystery                   |
| 2  | The Million Dollar Hotel| Drama, Thriller                             |
| 3  | Sleepless in Seattle    | Comedy, Drama, Romance                      |
| 4  | Dawn of the Dead        | Horror                                      |
| 5  | Galaxy Quest            | Comedy, Family, Science Fiction             |
| 6  | The Thomas Crown Affair| Romance, Crime, Thriller, Drama             |
| 7  | Sunshine                | Science Fiction, Thriller                   |
| 8  | The Thomas Crown Affair| Drama, Crime, Romance                       |
| 9  | Lonely Hearts           | Drama, Thriller, Crime, Romance             |
| 10 | Bonnie and Clyde        | Crime, Drama                                |

Diketahui bahwa pengguna ini sebelumnya memberikan rating tinggi pada film-film bergenre Comedy, War, Action, Thriller, dan Adventure seperti To Be or Not to Be, Terminator 3, dan The Poseidon Adventure. Berdasarkan pola tersebut, sistem merekomendasikan 10 film dengan genre yang sebagian besar relevan, termasuk The 39 Steps, The Million Dollar Hotel, dan Sleepless in Seattle yang mengandung unsur action, dan thriller serta beberapa film dari genre lain seperti drama, romance, dan science fiction untuk memberikan variasi pilihan. Rekomendasi ini menunjukkan bahwa model berhasil menangkap preferensi pengguna dan menyarankan film yang sesuai dengan selera menonton sebelumnya.

#### Kelebihan Pendekatan Collaborative Filtering
Collaborative Filtering memiliki kelebihan dalam kemampuannya untuk menemukan pola tersembunyi dalam perilaku pengguna yang tidak dapat dideteksi melalui analisis konten semata. Dengan membandingkan pola interaksi antar pengguna (seperti penilaian, pembelian, atau klik), sistem ini dapat merekomendasikan item yang belum pernah dilihat atau dipertimbangkan oleh pengguna sebelumnya, yang memungkinkan munculnya rekomendasi yang lebih bervariasi dan sering kali lebih mengejutkan. Pendekatan ini juga tidak memerlukan informasi tentang fitur item, sehingga dapat diterapkan pada berbagai jenis data.

#### Kekurangan Pendekatan Collaborative Filtering
Pada pendekatan Collaborative Filtering terdapat permasalahan cold start, yaitu kesulitan merekomendasikan item baru (yang belum memiliki interaksi) atau kepada pengguna baru (yang belum memiliki histori). Selain itu, pendekatan ini sangat tergantung pada jumlah dan kualitas data interaksi pengguna. Jika data interaksi jarang atau tidak lengkap (data sparsity), sistem bisa gagal memberikan rekomendasi yang akurat. Dalam beberapa kasus, juga terdapat risiko bias terhadap item populer dan kesulitan dalam menjelaskan alasan di balik suatu rekomendasi kepada pengguna.

## Evaluation
### Evaluasi pada Pendekatan Content Based Filtering
Pada tahap evaluasi di pendekatan Content Based Filtering ini, metrik yang digunakan adalah precision, yang berfungsi untuk mengukur seberapa banyak item yang direkomendasikan oleh sistem dan benar-benar relevan bagi pengguna, dibandingkan dengan total item yang direkomendasikan. Dengan kata lain, precision memberikan gambaran tentang tingkat akurasi rekomendasi yang dihasilkan oleh sistem. Penggunaan metrik ini penting untuk mengetahui seberapa efektif sistem dalam menyaring item yang sesuai dengan preferensi pengguna, serta untuk meminimalkan jumlah rekomendasi yang tidak relevan. Formula dari metrik precision tersebut adalah sebagai berikut:

![formula-precision-sistem-rekomendasi](https://github.com/user-attachments/assets/984d609d-0675-44c7-a43e-712e49b6335f)

Dengan keterangan sebagai berikut:
- **Relevant Items**: Item-item yang sebenarnya relevan atau disukai oleh pengguna (biasanya diperoleh dari data ground truth, seperti histori pembelian, penilaian tinggi, atau interaksi eksplisit).
- **Recommended Items**: Item-item yang direkomendasikan oleh sistem.
- **∣⋅∣**: Menyatakan jumlah elemen (ukuran dari himpunan).

Berdasarkan evaluasi yang dilakukan pada pendekatan ini, diperoleh nilai **precison sebsar 100%** dengan rincian output sebagai berikut:
| movie_name                    | genres                                  | is_relevant |
|------------------------------|------------------------------------------|-------------|
| Made in Hong Kong            | Crime, Drama, Romance                    | True        |
| 3-Iron                       | Drama, Romance, Crime                    | True        |
| The Man with the Golden Arm  | Crime, Drama, Romance                    | True        |
| The Thomas Crown Affair      | Romance, Crime, Thriller, Drama         | True        |
| The Thomas Crown Affair      | Drama, Crime, Romance                    | True        |
| Schizo                       | Crime, Drama, Romance                    | True        |
| Prizzi's Honor               | Romance, Comedy, Crime, Drama           | True        |
| Tie Me Up! Tie Me Down!      | Comedy, Crime, Drama, Romance           | True        |
| Match Point                  | Drama, Thriller, Crime, Romance         | True        |
| Young Adam                   | Drama, Thriller, Crime, Romance         | True        |

Berdasarkan output yang ditampilkan, sistem rekomendasi berhasil menghasilkan 10 film yang seluruhnya memiliki genre **Crime**, **Drama**, dan **Romance**, sesuai dengan genre yang dianggap relevan oleh pengguna. Hal ini terlihat dari kolom `is_relevant` yang semuanya bernilai `True`, serta nilai **Precision** mencapai **100.00%**. Artinya, semua film yang direkomendasikan memang sesuai dengan kriteria genre yang diharapkan. Ini menunjukkan bahwa sistem rekomendasi memiliki performa yang sangat baik dalam menyesuaikan hasil rekomendasi dengan preferensi pengguna, setidaknya dari segi kecocokan genre.

### Evaluasi pada Pendekatan Collaborative Filtering
Pada tahap evaluasi di pendekatan  Collaborative Filtering ini, metrik yang digunakan adalah Mean Absolute Error (MAE) dan Root Mean Squared Error (RMSE). Kedua metrik ini digunakan untuk mengukur seberapa baik model dalam memprediksi nilai aktual dibandingkan dengan nilai yang diprediksi. Metrik MAE menghitung rata-rata selisih absolut antara nilai aktual dan nilai prediksi, yang mencerminkan tingkat kesalahan secara umum tanpa memperhatikan arah kesalahan. Sementara itu, RMSE memberikan penalti yang lebih besar terhadap kesalahan prediksi yang besar karena menghitung akar dari rata-rata kuadrat selisih antara nilai aktual dan prediksi. 

Formula untuk metrik MAE adalah sebagai berikut:

![mae-sistem-rekomendasi](https://github.com/user-attachments/assets/825df882-e6ee-46c1-8feb-57b899286aed)

Dengan keterangan komponen sebagai berikut:

![keterangan-mae](https://github.com/user-attachments/assets/455bdb7c-4860-4db7-ae7e-82fac71b71cd)

Kemudian formula untuk metrik RMSE adalah sebagai berikut:

![rmse-sistem-rekomendasi](https://github.com/user-attachments/assets/017a7389-e272-4640-9e45-3cc3854664a8)

Dengan keterangan komponen sebagai berikut:
- Komponen sama dengan MAE, namun selisih antara prediksi dan nilai aktual dikuadratkan sebelum dirata-rata, lalu diakarkan.

Berdasarkan evaluasi yang dilakukan pada pendekatan ini, diperoleh visualisasi metrik MAE sebagai berikut:

![visualisasi-mae](https://github.com/user-attachments/assets/5db4e97d-f4b5-4f0c-afe0-594290804d23)

Visualisasi di atas menunjukkan perkembangan metrik Mean Absolute Error (MAE) pada data latih dan data validasi selama proses pelatihan model sistem rekomendasi. Terlihat bahwa nilai MAE pada data pelatihan mengalami penurunan yang konsisten seiring bertambahnya jumlah epoch, yang menunjukkan bahwa model semakin baik dalam mempelajari pola dari data latih. Sementara itu, nilai MAE pada data validasi juga menurun di awal pelatihan, lalu cenderung stabil mulai dari epoch ke-5 hingga epoch ke-12. Pola ini mengindikasikan bahwa model tidak mengalami overfitting secara signifikan dan memiliki generalisasi yang baik terhadap data baru. Dengan kata lain, model mampu memberikan prediksi rating yang cukup akurat, baik pada data yang sudah dikenalnya maupun pada data yang belum pernah dilihat.

Kemudian diperoleh juga visualisasi metrik RMSE sebagai berikut:

![visualisasi-rmse](https://github.com/user-attachments/assets/e52d71e4-3b0f-49c3-b0dc-d40ef55bc36b)

Visualisasi di atas menunjukkan metrik **Root Mean Squared Error (RMSE)** selama proses pelatihan model sistem rekomendasi. Grafik menampilkan dua kurva: satu untuk RMSE pada data pelatihan (berwarna biru) dan satu lagi untuk RMSE pada data validasi (berwarna oranye). Terlihat bahwa RMSE pada data pelatihan secara konsisten menurun dari epoch ke-0 hingga epoch ke-12, menandakan bahwa model semakin akurat dalam memprediksi rating seiring pelatihan. Sementara itu, RMSE pada data validasi juga menunjukkan tren penurunan di awal, kemudian cenderung stabil mulai sekitar epoch ke-5. Pola ini mengindikasikan bahwa model tidak mengalami overfitting secara drastis dan memiliki performa yang stabil ketika diuji pada data yang tidak dilatih. Dengan RMSE yang relatif rendah dan stabil, model ini menunjukkan kemampuan prediksi yang cukup baik dan layak untuk digunakan dalam memberikan rekomendasi film.

## Daftar Pustaka
[1] Nanou, T., Lekakos, G. & Fouskas, K. The effects of recommendations’ presentation on persuasion and satisfaction in a movie recommender system. Multimedia Systems 16, 219–230 (2010). https://doi.org/10.1007/s00530-010-0190-0

[2] Jayalakshmi, S.; Ganesh, N.; Čep, R.; Senthil Murugan, J. Movie Recommender Systems: Concepts, Methods, Challenges, and Future Directions. Sensors 2022, 22, 4904. https://doi.org/10.3390/s22134904

[3] Ahmad, Juan, Jonas Hellgren, and Alan Said. "Tell Me the Good Stuff: User Preferences in Movie Recommendation Explanations." arXiv preprint arXiv:2505.03376 (2025).
