# **System Recommendation : Anime Recommendation System Using Collaborative Filtering**
Anime Recommendation using My Anime List Database

## Domain Proyek

Domain proyek yang dijelaskan pada proyek machine learning kali ini yaitu tentang sistem rekomendasi dengan judul "Anime Recommendation System Using Collaborative Filtering". Sistem Rekomendasi Anime yang digunakan untuk merekomendasikan penonton dalam memilih anime berdasarkan minat mereka.

### Latar Belakang

![list of anime](https://user-images.githubusercontent.com/55022521/191886848-c129732b-33e3-4147-9469-c648bca75c13.jpg)

Keberadaan manga (komik Jepang) dan anime (film kartun animasi Jepang) sudah bukan hal yang asing di Indonesia. Keberadaan kedua media tersebut sudah cukup lama beredar di Indonesia. Beberapa stasiun televisi di Indonesia juga pernah menayangkan anime seperti Doraemon, Sailormoon, Dragonball ataupun Detective Conan dan Naruto. 

Anime adalah bagian dari budaya pop Jepang yang sudah menjadi bagian dari masyarakat secara dunia. Umumnya anime memiliki cerita yang sama dengan versi 
manga atau komiknya. anime dan manga menjadi media yang menjadi komoditas ekspor Jepang ke seluruh dunia selain video games. Anime sebenarnya merupakan versi bergerak dari manga yang umumnya terbit terlebih dahulu[7].

Genre anime didesain bagi penonton dengan preferensi tertentu, bukan sekedar ingin menikmati gambar lucu atau warna yang menarik tapi juga alur cerita yang dalam. Keberadaan alur cerita yang kompleks membuat tantangan yang lebih mendalam dalam menyusun cerita pada sebuah anime. Anime pada posisinya di dunia seni, merupakan bagian dari karya audio visual. Penggarapannya pun tidak lepas dari pakem yang ada pada saat penggarapan sebuah karya film pada umumnya.

Oleh karena itu penulis ingin membuat sebuah sistem rekomendasi yang dapat digunakan oleh penggemar anime maupun khalayak umum yang ingin menonton anime. Fungsi Rekomendasi sistem ini dapat membantu khalayak umum mendapatkan informasi anime yang mendapat rating tinggi dan membantu merekomendasikan anime sesuai yang diinginkan oleh pecinta anime.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang yang menjadi tercipta nya penelitian ini, adapun rincian masalah yang dapat diselesaikan pada proyek ini adalah sebagai berikut :

*   Bagaimana merancang sebuah model sistem rekomendasi anime yang sesuai dengan minat penggemar anime?
*   Apa model yang paling baik yang digunakan dalam merekomendasikan penggemar anime dalam memilih anime?
*   Bagaimana cara kerja sistem rekomendasi untuk merekomendasikan penggemar  anime dalam dalam memilih anime?

### **Goals**

Adapun tujuan dilakukan nya penelitian ini yaitu:

*   Menghasilkan sebuah sistem rekomendasi anime untuk memudahkan penggemar anime dalam mencari anime yang sesuai dengan minatnya.
*   Membandingkan performa model yang efektif dalam sistem rekomendasi anime.
*   Menejelaskan cara kerja model algoritma yang digunakan dalam sistem rekomendasi untuk merekomendasikan anime.

### **Solution Statements**

Dalam rangka mencapai tujuan penelitian yang ada, penulis akan membangun model rekomendasi dengan dua buah model yaitu *Content Based Filtering* dan *Collaborative Filtering*. Kedua model akan dibandingkan dan akan dipilih satu yang terbaik dengan performa serta accuracy terbaik yang digunakan :


*   **Content Based Filtering**

Metode *Content Based Filtering* bekerja dengan cara menyarankan produk yang serupa dengan yang disukai pengguna di masa lalu. Keserupaan item ditentukan tergantung pada sifat-sifat yang terkait dengan item yang dibandingkan. Misalnya, jika pengguna individu telah memberi peringkat yang baik untuk film yang terhubung ke kategori komedi, maka program dapat memahami untuk menyarankan film lain dari kategori ini. Selanjutnya, pemberi rekomendasi berbasis konten memperlakukan saran sebagai masalah kategori khusus pengguna dan mempelajari pengklasifikasi untuk preferensi pelanggan tergantung pada ciri-ciri produk. 

*Content-based recommender system* dapat digunakan dalam berbagai rentang domain yaitu, halaman web rekomendasi, artikel berita, pekerjaan, program televisi, dan produk untuk dijual.

*   **Collaborative Filtering**

Metode *Collaborative Filtering* memiliki kemampuan untuk memanfaatkan peringkat pengguna sebelumnya untuk memprediksi atau merekomendasikan konten baru yang akan disukai pengguna individu. Asumsi sebenarnya sangat didasarkan pada gagasan kesamaan antara pengguna atau antara produk, dengan kesamaan yang dinyatakan sebagai fungsi kesepakatan antara peringkat atau preferensi masa lalu.

## Data Understanding

![anime'](https://user-images.githubusercontent.com/55022521/191887001-1a4e2b58-eda6-4015-9748-910101bd264b.jpg)

Data yang digunakan untuk proyek ini diambil dari sini : [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database?select=rating.csv).

Dataset terdiri dari 2 file.

*   **Anime.csv**
1.   `anime_id`: myanimelist.net's unique id identifying an anime.
2.   `name`: full name of anime
3.   `genre`: comma separated list of genres for this anime.
4.   `type`: movie, TV, OVA, etc.
5.   `episodes`: how many episodes in this show. (1 if movie).
6.   `rating`: average rating out of 10 for this anime.
7.   `members`: number of community members that are in this anime's
"group"

*   **Rating.csv**

1.    `user_id`: non identifiable randomly generated user id.
2.   `anime_id`: the anime that this user has rated.
3.   `rating`: rating out of 10 this user has assigned (-1 if the user watched it but didn't assign a rating

## Data Preparation

Teknik yang penulis gunakan dalam tahap Data Preparation adalah sebagai berikut:

1. Handling missing value

Pada tahapan ini penulis melakukan membersihkan dataset dengan berbagai metode :
- Dropna
Pada tahap ini pada kolom tertentu yang memiliki data kosong(null/NaN) akan drop dengan axis = 0 yang berarti satu baris akan di drop.

- Fillna
Pada tahap ini pada kolom tertentu yang memiliki data kosong(null/NaN) akan di-isi dengan nilai tertentu.

2. Merging Dataset

Pada tahap ini penulis melakukan penggabungan dataset. Dataset anime.csv dan rating.csv digabungkan berdasarkan nilai 'anime_id' yang sama pada kedua dataset

3. Split Dataset into Data Train and Data Validation

Pada tahap ini, penulis melakukan pembagian dataset menjadi data latih dan data validasi secara manual. Pembagian dataset ini bertujuan agar nantinya dapat digunakan untuk melatih dan mengevaluasi kinerja model. Pada proyek ini, 80% dataset digunakan untuk melatih model, dan 20% sisanya digunakan untuk mengevaluasi kinerja model.

4. Standardization

Pada tahap ini, penulis melakukan standardisasi menggunakan metode MinMaxScaler secara manual. Standardisasi ini sangat berguna dalam menyeratakan skala pada data terutama data numerical. Standardisasi ini digunakan dalam mempersiapkan data untuk mengembangkan model dengan Collaborative Filtering.

`Min Max Scaler`

`y = (x — min) / (max-min)`

`y = df['rating'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values`

## Modeling and Result
### Model Development dengan Content Based Filtering
### Model Development dengan  Filtering

## Evaluation


### Conclusion


## Reference

