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

3.TF-IDF for Feature extraction

Pada tahapan ini TF-IDF digunakan untuk feature (text) extraction yaitu mengubah value pada kolom tertentu menjadi sebuah vektor yang akan digunakan dalam proses perhitungan cossine_similarity

4. Split Dataset into Data Train and Data Validation

Pada tahap ini, penulis melakukan pembagian dataset menjadi data latih dan data validasi secara manual. Pembagian dataset ini bertujuan agar nantinya dapat digunakan untuk melatih dan mengevaluasi kinerja model. Pada proyek ini, 80% dataset digunakan untuk melatih model, dan 20% sisanya digunakan untuk mengevaluasi kinerja model.

5. Standardization

Pada tahap ini, penulis melakukan standardisasi menggunakan metode MinMaxScaler secara manual. Standardisasi ini sangat berguna dalam menyeratakan skala pada data terutama data numerical. Standardisasi ini digunakan dalam mempersiapkan data untuk mengembangkan model dengan Collaborative Filtering.

`Min Max Scaler`

`y = (x — min) / (max-min)`

`y = df['rating'].apply(lambda x: (x - min_rating) / (max_rating - min_rating)).values`


## Modeling and Result

### Model Development dengan Content Based Filtering

![kimi](https://user-images.githubusercontent.com/55022521/192094678-fe5ad24b-678c-42f1-98d8-19936f4f5524.jpg)

![kimmiii](https://user-images.githubusercontent.com/55022521/192094682-7bedd570-437a-4cf3-991f-6fad4edc60d3.jpg)

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

![best anime](https://user-images.githubusercontent.com/55022521/192094766-3a55e57f-5b58-442b-8251-eecc13006847.jpg)

![top10](https://user-images.githubusercontent.com/55022521/192094769-f5b639fe-7943-4fec-a407-b36cc68c3083.jpg)

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

[[1]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Schafer, J.B., F. Dan, H. Jon and S. Shilad, 2007b.

[[2]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Collaborative Filtering Recommender Systems. In:Brusilovsky, P., K. Alfred and N. Wolfgang(Eds.), The Adaptive Web of Lecture Notes inComputer Science. Springer-Verlag, Berlin,Germany, 4321: 291-324.

[[3]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Ziegler, C., 2004. Semantic web recommender systems.Proceedings of the EDBT Workshop, pp: 78-89.

[[3]](https://www.researchgate.net/publication/287952023_Collaborative_Filtering_Recommender_Systems)
Ziegler, C.N., S.M. Mcnee, J.A. Konstan and L. Georg,2005. Improving recommendation lists throughtopic diversification. Proceeding of the 14thInternational World Wide Web Conference(WWW). ACM, Chiba, Japan, pp: 22-32.

[[4]](https://www.worldscientific.com/doi/abs/10.1142/S0218213009000378)
Sebastia, Let al. 2009. e-Tourism: A touristr recommendation and planning application. International Journal on Artificial Intelligence Tools18(5): 717-738

[[5]](https://www.worldscientific.com/doi/abs/10.1142/S0218213009000378)
Lutfi,E.T. & Kusrini. 2009. Algoritma Data Mining. Yogyakarta: CV AndiOffset

[[6]](https://doaj.org/article/6816ea622b08499597070a9073e28b7c)
Wijaya, A., & Alfian, D. 2018. Sistem Rekomendasi Laptop  Menggunakan  Collaborative  Filtering  dan Content-Based   Filtering.   Jurnal   Computech   dan Bisnis, 12(1),11-27

[7] Ito, M., Okabe, D., & Tsuji, I. (2005). Fandom Unbound. London: Yale University Press.

[8] Kurniawan S, Daniel, 2019. STUDI SEMIOTIKA KARAKTER MONOKUMA PADA ANIME FRANCHISE SERIES “DANGANRONPA”.
