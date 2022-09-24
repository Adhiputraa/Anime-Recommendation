# **System Recommendation : Anime Recommendation System Using Collaborative Filtering**
Anime Recommendation using My Anime List Database

By : Aditya Yoga Adhiputra

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

Dataset yang penulis gunakan dalam proyek ini, yaitu Dataset dengan judul Anime Recommendations Database yang diambil pada laman Kaggle [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database?select=rating.csv). Dataset tersebut berisikan 2 file csv, yaitu file *Anime* dan *Rating*. File Anime.csv yang terdiri dari 7 kolom dan 12294 baris, Sedangkan file Rating.csv terdiri dari 3 kolom dan 7813737 baris. 

Berikut merupakan informasi lebih detail dari masing masing kolom dataset:

*   **Anime.csv**
1.   `anime_id`: Id unik myanimelist.net mengidentifikasi anime.
2.   `name`: nama lengkap anime
3.   `genre`: daftar genre untuk anime ini.
4.   `type`: film, TV, OVA, dll.
5.   `episodes`: seberapa banyak episode dalam acara ini, 1 jika film.
6.   `rating`: peringkat rata-rata dari 10 untuk anime ini.
7.   `members`: jumlah anggota komunitas yang ada di anime ini
"kelompok"

*   **Rating.csv**

1.    `user_id`: id pengguna yang dibuat secara acak yang tidak dapat diidentifikasi.
2.   `anime_id`: anime yang telah dinilai pengguna ini.
3.   `rating`: anime yang telah dinilai oleh pengguna ini.rating dari 10 pengguna ini telah ditetapkan (-1 jika pengguna menontonnya tetapi tidak menetapkan peringkat).

## Data Preparation

Teknik yang penulis gunakan dalam tahap Data Preparation adalah sebagai berikut:

- Data Cleaning

Pada tahapan ini penulis melakukan membersihkan dataset, dataset harus dalam keadaan clean agar memudahkan pemrosesan data dan pemodelan. pembersihan dataset dilakukan dengan berbagai metode. Metode Dropna digunakan pada kolom tertentu yang memiliki data kosong(null/NaN) akan drop dengan axis = 0 yang berarti satu baris akan di drop. Metode fillna digunakan pada kolom tertentu yang memiliki data kosong(null/NaN) akan di-isi dengan nilai tertentu. 

- Merging Dataset

Pada tahap ini penulis melakukan penggabungan dataset. Dataset anime.csv dan rating.csv digabungkan berdasarkan nilai 'anime_id' yang sama pada kedua dataset

- TfidfVectorizer for Feature extraction

Pada tahapan ini TfidfVectorizer digunakan untukmengonversi kumpulan dokumen mentah menjadi matriks fitur TF-IDF. Pada kasus ini yaitu mengubah value pada kolom tertentu menjadi sebuah vektor yang akan digunakan dalam proses perhitungan cossine_similarity.

- Split Dataset into Data Train and Data Validation

Pada tahap ini, penulis melakukan pembagian dataset menjadi data latih dan data validasi secara manual. Pembagian dataset ini bertujuan agar nantinya dapat digunakan untuk melatih dan mengevaluasi kinerja model. Pada proyek ini, 80% dataset digunakan untuk melatih model, dan 20% sisanya digunakan untuk mengevaluasi kinerja model.

- Standardization

Pada tahap ini, penulis melakukan standardisasi menggunakan metode MinMaxScaler secara manual. Standardisasi ini sangat berguna dalam menyeratakan skala pada data terutama data numerical. Standardisasi ini digunakan dalam mempersiapkan data untuk mengembangkan model dengan Collaborative Filtering.

`Min Max Scaler`

`y = (x — min) / (max-min)`

`y = df['rating'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values`


## Modeling and Result

### Model Development dengan Content Based Filtering
Pada proses model development dengan Content Based Filtering, model ini bekerja berdasarkan pencarian yang dilakukan oleh user. Dimana model tersebut akan membantu user dalam mencari secara spesifik anime yang memiliki alur cerita dan genre (content) yang mirip maupun hampir sama. Model ini bekerja dengan mencari kesamaan fitur dengan perhitungan cossine_similarity. Pada kasus ini kesamaan fitur genre menjadi perhitungan dalam merekomendasikan judul anime.

Langkah Langkah dalam membangun model:
1. Proses development nya diawali dengan extrasi fitur text menggunakan TfidfVectorizer dari library sklearn.feature_extraction.text.
2. Lalu mengubah vektor tf-idf ke dalam bentuk matriks menggunakan fungsi `todense()`.
3. Membuat dataframe untuk melihat matrix tf-idf dengan kolom diisi dengan genre dan baris diisi dengan title_name
4. Menghitung cosine similarity pada matrix tf-idf menggunakan fungsi `cosine_similarity()`.
5. Membuat dataframe dari variabel cosine_sim dengan baris dan kolom berupa title_name.
6. Membuat fungsi `anime_recommendations` dengan parameter berdasarkan kemiripan dataframe.

`def anime_recommendations(title, similarity_data=cosine_sim_df, items=data[['title_name', 'genre']], k=5)`

     Parameter:
     - `title`: tipe data string (str) judul anime (index kemiripan dataframe)
     - `similarity_data` : tipe data pd.DataFrame (object) kesamaan dataframe, simetrik, dengan anime sebagai indeks dan kolom
     - `items` : tipe data pd.DataFrame (object) mengandung kedua nama dan fitur lainnya yang digunakan untuk mendefinisikan kemiripan
     - `k` : tipe data integer (int) Banyaknya jumlah rekomendasi yang diberikan

Contoh seseorang yang telah menonton anime 'Kimi No Nawa.'. Ia suka dengan film anime tersebut. Lalu ia ingin mencari anime yang secara cerita dan alur mirip dengan 'Kimi No Nawa.'

|   |   id  |   title_name   |
|--:|:-----:|:--------------:|
| 0 | 32281 | Kimi no Na wa. |



Maka sistem ini akan merekomendasikan anime-anime yang memiliki kesamaan fitur dengan anime 'Kimi No Nawa.'

|   |               title_name              |                     genre                    |
|--:|:-------------------------------------:|:--------------------------------------------:|
| 0 |          Wind: A Breath of Heart (TV) |         Drama, Romance, School, Supernatural |
| 1 |           Wind: A Breath of Heart OVA |         Drama, Romance, School, Supernatural |
| 2 | Aura: Maryuuin Kouga Saigo no Tatakai | Comedy, Drama, Romance, School, Supernatural |
| 3 |                              Harmonie |                  Drama, School, Supernatural |
| 4 |        Angel Beats!: Another Epilogue |                  Drama, School, Supernatural |



Berikut merupakan kelebihan dan kekurangan pada model ini:

**Advantages**

- Pengguna akan direkomendasikan jenis barang yang mereka sukai.
- Pengguna puas dengan jenis rekomendasi.
- Item baru dapat direkomendasikan, hanya data untuk item itu yang diperlukan.
- Model ini dapat menangkap minat spesifik pengguna, dan dapat merekomendasikan item bagus yang sangat sedikit pengguna lain yang tertarik

**Disadvantages**

- Pengguna tidak akan pernah direkomendasikan untuk item yang berbeda.
- Dalam hal pengembangan bisnis tidak dapat diperluas karena pengguna tidak mencoba jenis produk yang berbeda.
- Jika matriks pengguna atau matriks item diubah, matriks kesamaan kosinus perlu dihitung lagi

### Model Development dengan Collaborative Filtering

Pada proses model development dengan Collaborative Filtering, model ini bekerja berdasarkan peringkat pengguna sebelumnya untuk memprediksi atau merekomendasikan konten baru. Dimana model tersebut akan membantu user, terutama user baru dalam menemukan anime terbaik berdasarkan rating dari user lainya. 

Langkah Langkah dalam membangun model:
1. Melakukan proses encoding angka ke user_id, anime_id.
2. Mapping user_id ke dataframe user dan Mapping anime_id ke dataframe anime.
3. Mendapatkan jumlah user dan jumlah anime.
4. Mencari nilai minimum rating dan nilai maksimum rating.
5. Mengacak dataset.
6. Membuat variabel x untuk mencocokkan data user dan anime menjadi satu value dan variabel y untuk membuat rating dari hasil.
7. Membagi menjadi 80% data train dan 20% data validasi.
8. Memanggil class RecommenderNet() dari library tf.keras.Model, pada class ini berisi fungsi-fungsi yang digunakan untuk memproses data.
```
class RecommenderNet(tf.keras.Model):
 
  # Insialisasi fungsi
  def __init__(self, num_users, num_anime, embedding_size, **kwargs):
    super(RecommenderNet, self).__init__(**kwargs)
    self.num_users = num_users
    self.num_resto = num_anime
    self.embedding_size = embedding_size
    self.user_embedding = layers.Embedding( # layer embedding user
        num_users,
        embedding_size,
        embeddings_initializer = 'he_normal',
        embeddings_regularizer = keras.regularizers.l2(1e-6)
    )
    self.user_bias = layers.Embedding(num_users, 1) # layer embedding user bias
    self.resto_embedding = layers.Embedding( # layer embeddings resto
        num_anime,
        embedding_size,
        embeddings_initializer = 'he_normal',
        embeddings_regularizer = keras.regularizers.l2(1e-6)
    )
    self.resto_bias = layers.Embedding(num_anime, 1) # layer embedding resto bias
 
  def call(self, inputs):
    user_vector = self.user_embedding(inputs[:,0]) # memanggil layer embedding 1
    user_bias = self.user_bias(inputs[:, 0]) # memanggil layer embedding 2
    anime_vector = self.resto_embedding(inputs[:, 1]) # memanggil layer embedding 3
    anime_bias = self.resto_bias(inputs[:, 1]) # memanggil layer embedding 4
 
    dot_user_anime = tf.tensordot(user_vector, anime_vector, 2) 
 
    x = dot_user_anime + user_bias + anime_bias
    
    return tf.nn.sigmoid(x) # activation sigmoid
```

9. Menginisiasi model RecommenderNet() yang memiliki parameter: num_users, num_anime, embedding_size=50.
10. Mengcompile model dengan loss_func = BinaryCrossentropy() dan menggunakan metrics evaluasi = RootMeanSquaredError.
11. Melakukan training data dan memvisualisasikan hasil dari metrics evaluasi = RootMeanSquaredError menggunakan matplotlib.
12. Lalu melakukan prediksi.

Contoh hasil dari sistem rekomendasi ini, pengguna baru disuguhkan list of anime yang mendapatkan penilaian tertinggi dari user lainya.

| Showing best anime recommendations for users: 1223                                                  |
|-----------------------------------------------------------------------------------------------------|
| ===========================                                                                         |
| Anime with high ratings from user                                                                   |
| --------------------------------                                                                    |
| To Heart 2 Adnext : Comedy, Harem, Romance                                                          |
| Kizuna Ichigeki : Comedy, Martial Arts                                                              |
| To Heart 2 Special : Drama, Romance, School                                                         |
| To Heart 2: Dungeon Travelers : Adventure, Comedy, Ecchi, Fantasy, Magic, Seinen                    |
| Tsuki wa Higashi ni Hi wa Nishi ni: Operation Sanctuary OVA : Comedy, Drama, Harem, Romance, Sci-Fi |



Sistem juga menampilkan beberapa anime terbaik yang direkomendasikan untuk user berdasarkan pilihan user lainya

| Top 10 Anime recommendation                                                                                           |
|-----------------------------------------------------------------------------------------------------------------------|
| --------------------------------------------------------------------------------------------------------------------- |
| Kimi no Na wa. : Drama, Romance, School, Supernatural                                                                 |
| Gintama° : Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen                                               |
| Steins;Gate : Sci-Fi, Thriller                                                                                        |
| Hunter x Hunter (2011) : Action, Adventure, Shounen, Super Power                                                      |
| Ginga Eiyuu Densetsu : Drama, Military, Sci-Fi, Space                                                                 |
| Gintama Movie: Kanketsu-hen - Yorozuya yo Eien Nare : Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen    |
| Clannad: After Story : Drama, Fantasy, Romance, Slice of Life, Supernatural                                           |
| Gintama : Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen                                                |
| Haikyuu!! Second Season : Comedy, Drama, School, Shounen, Sports                                                      |
| Suzumiya Haruhi no Shoushitsu : Comedy, Mystery, Romance, School, Sci-Fi, Supernatural                                |
|                                                                                                                       |



Berikut merupakan kelebihan dan kekurangan pada model ini:

**Advantages**
- Produk baru berupa anime yang baru rilis dapat diperkenalkan kepada pengguna.
- Dalam hal bisnis dapat diperluas dan dapat mempopulerkan produk anime terbaru.
- Model ini dapat membantu pengguna menemukan minat baru

**Disadvantages**
- Riwayat pengguna sebelumnya diperlukan atau data untuk produk diperlukan berdasarkan jenis metode kolaboratif yang digunakan.
- Item baru tidak dapat direkomendasikan jika tidak ada pengguna yang membeli atau menilainya.


## Evaluation
**Cosine similarity**

Cosine similarity adalah metriks yang membantu dalam menentukan seberapa mirip objek data terlepas dari ukurannya. Dalam Cosine similarity, objek data dalam kumpulan data diperlakukan sebagai vektor. Rumus untuk mencari persamaan cosinus antara dua vektor adalah:

![cossine](https://user-images.githubusercontent.com/55022521/192092471-8c4b2f08-fddd-4bd9-8398-f584657e91be.jpg)

`Cos(x, y) = x . y / ||x|| * ||y||`

Keterangan :
- `x . y = product (dot) of the vectors ‘x’ and ‘y’.`
- `||x|| and ||y|| = length of the two vectors ‘x’ and ‘y’.`
- `||x|| * ||y|| = cross product of the two vectors ‘x’ and ‘y’.`

Keuntungan Cosine similarity :

- Kesamaan kosinus bermanfaat karena bahkan jika dua objek data serupa terpisah jauh oleh jarak Euclidean karena ukurannya, mereka masih dapat memiliki sudut yang lebih kecil di antara mereka. Semakin kecil sudutnya, semakin tinggi kesamaannya.
- Ketika diplot pada ruang multidimensi, kesamaan kosinus menangkap orientasi (sudut) dari objek data dan bukan besarnya.

Matrix Cosine Similarity

| **title_name**                 | Soredemo Tsuma wo Aishiteru | Emi to Yobanaide | Hyakujuu-Ou GoLion | Yoshinaga-sanchi no Gargoyle | Attacker You! |
|--------------------------------|-----------------------------|------------------|--------------------|------------------------------|---------------|
| Strike Witches 2               | 0.0                         | 0.0              | 0.275165           | 0.000000                     | 0.102196      |
| Shikabane Hime: Aka            | 0.0                         | 0.0              | 0.000000           | 0.000000                     | 0.098475      |
| Tayutayu: Pure My Heart        | 0.0                         | 0.0              | 0.000000           | 0.295969                     | 0.000000      |
| Bikini Warriors Special        | 0.0                         | 0.0              | 0.000000           | 0.178267                     | 0.000000      |
| Pokemon: Pikachu no Fuyuyasumi | 0.0                         | 0.0              | 0.194750           | 0.301418                     | 0.000000      |
| Idol Project                   | 0.0                         | 0.0              | 0.219851           | 0.119199                     | 0.000000      |
| Ninja and Soldier              | 0.0                         | 0.0              | 0.000000           | 0.000000                     | 0.000000      |
| Redline Pilot                  | 0.0                         | 0.0              | 0.000000           | 0.000000                     | 0.338728      |
| Seijuuki Cyguard               | 0.0                         | 0.0              | 0.666296           | 0.000000                     | 0.000000      |
| Prima Donna Mai                | 1.0                         | 1.0              | 0.000000           | 0.000000                     | 0.000000      |

Pada perhitungan Cosine Similarity, skor kesamaan berkisar dari 0 hingga 1, dengan 0 sebagai yang terendah (paling tidak mirip) dan 1 sebagai yang tertinggi (paling mirip).


Contohnya anime dengan judul **'Prima Donna Mai'** memiliki nilai 1.0 dengan anime yang berjudul **'Soredemo Tsuma wo Aishiteru'** dan **'Emi to Yobanaide'**. Dengan nilai tersebut maka dikatakan bahwa anime tersebut memiliki kemiripan yang sangat kuat. Jika < 1 atau mendekati 0 maka anime tersebut berkurang kemiripan nya atau mungkin saja tidak mirip.



**Root Mean Squared Error**

Root Mean Squared Error (RMSE) adalah salah satu metrik evaluasi paling populer untuk masalah regresi. RMSE dihitung dengan mengambil akar kuadrat dari MSE:

![rmse](https://user-images.githubusercontent.com/55022521/192090047-110a1997-53b6-4e98-a42f-da844ec38e65.png)

Nilai yang dihasilkan dapat diinterpretasikan dalam unit yang sama dengan nilai prediksi. Root Mean Squared Error (RMSE) lebih mudah dipahami daripada beberapa metrik lainnya. Namun nilai RMSE hanya dapat dibandingkan antara model yang mengukur kesalahan menggunakan unit yang sama. Nilai RMSE yang lebih rendah menunjukkan performa model yang lebih baik. RMSE harus digunakan di atas MAE atau metrik evaluasi lainnya dalam situasi di mana data yang diamati memiliki distribusi kondisional asimetris.

Berikut merupakan hasil dari Root Mean Squared Error dari model Model Development dengan Collaborative Filtering.
Pada gambar dibawah terlihat bahwa pada nilai RMSE pada data test yaitu 0.16 lebih tinggi dibandingkan dengan RMSE pada data_train.

![hasil](https://user-images.githubusercontent.com/55022521/192092028-6bc1d932-5fea-4d13-affd-113d6f826979.png)

### Conclusion

Sistem Rekomendasi ini dibangun untuk memudahkan user dalam mencari anime sesuai minat mereka. Jika tergolong user baru yang belum pernah menonton anime, maka sistem rekomendasi dengan *collaborative filtering* dapat membantu karena dapat merekomendasikan anime berdasarkan rating pengguna lainya. Jika user yang sering menonton anime maka sistem rekomendasi dengan *Content Based filtering* dapat membantu user dalam memilih anime berdasarkan genre film atau yang jalan cerita nya mirip dengan anime yang telah user tonton. 

## Reference

[1] Ito, M., Okabe, D., & Tsuji, I. (2005). Fandom Unbound. London: Yale University Press.

[[2]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Schafer, J.B., F. Dan, H. Jon and S. Shilad, 2007b.

[[3]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Collaborative Filtering Recommender Systems. In:Brusilovsky, P., K. Alfred and N. Wolfgang(Eds.), The Adaptive Web of Lecture Notes inComputer Science. Springer-Verlag, Berlin,Germany, 4321: 291-324.

[[4]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Ziegler, C., 2004. Semantic web recommender systems.Proceedings of the EDBT Workshop, pp: 78-89.

[[5]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Ziegler, C.N., S.M. Mcnee, J.A. Konstan and L. Georg,2005. Improving recommendation lists throughtopic diversification. Proceeding of the 14thInternational World Wide Web Conference(WWW). ACM, Chiba, Japan, pp: 22-32.

[[6]](https://www.worldscientific.com/doi/abs/10.1142/S0218213009000378)
Sebastia, Let al. 2009. e-Tourism: A touristr recommendation and planning application. International Journal on Artificial Intelligence Tools18(5): 717-738

[[7]](https://www.worldscientific.com/doi/abs/10.1142/S0218213009000378)
Lutfi,E.T. & Kusrini. 2009. Algoritma Data Mining. Yogyakarta: CV AndiOffset

[[8]](https://doaj.org/article/6816ea622b08499597070a9073e28b7c)
Wijaya, A., & Alfian, D. 2018. Sistem Rekomendasi Laptop  Menggunakan  Collaborative  Filtering  dan Content-Based   Filtering.   Jurnal   Computech   dan Bisnis, 12(1),11-27

[9] Kurniawan S, Daniel, 2019. STUDI SEMIOTIKA KARAKTER MONOKUMA PADA ANIME FRANCHISE SERIES “DANGANRONPA”.
