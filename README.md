# Capstone_Project2


# Data Analysis procedure:
### 1. Defining the problem
### 2. Reading, understanding and cleaning data
### 3. Visualizing data
### 4. Solving the problem


# 1. Defining the problem

Sebagai data analysis di perusahaan ini saya diminta untuk menganalisa data untuk membuat strategi menaikkan sales penjualan dan membuat report dari data yang disediakan.

Untuk mengetahui strategi menaikkan sales penjualan saya perlu:
- Menentukan customer segment yang tepat
- Menentukan produk apa yang perlu kita fokuskan
- Menentukan cara kita berjualan
- Menentukan campaign yang tepat

Untuk report data juga akan dilakukan menggunakan tableau.

# 2. Reading, understanding and cleaning data

Membaca file marketing campaign

file yang dibaca tidak sempurna karena tiap kolom ada \t nya
maka saya menggunakan delimiter='\t'

menggunakan df info untuk memahami data. yang saya dapatkan dari data ini adalah:
1. Memiliki 26 numerical variables dan 3 categorical variables
2. Terdapat 24 missing values dari variable Income

Berikut penjelasan dari tiap kolom nya
ID: nomor identifikasi unik untuk setiap customer

Year_Birth: tahun kelahiran customer

Education: tingkat pendidikan customer

Marital_Status: status pernikahan customer

Income: pendapatan tahunan customer

Kidhome: jumlah anak kecil yang tinggal bersama customer

Teenhome: jumlah anak remaja yang  tinggal bersama customer

Dt_Customer: tanggal saat customer pertama kali datang

Recency: jumlah hari sejak customer terakhir kali melakukan pembelian

MntWines: jumlah uang yang dihabiskan customer untuk membeli wine

MntFruits: jumlah uang yang dihabiskan customer untuk membeli buah-buahan

MntMeatProducts: jumlah uang yang dihabiskan customer untuk membeli produk daging

MntFishProducts: jumlah uang yang dihabiskan customer untuk membeli produk ikan

MntSweetProducts: jumlah uang yang dihabiskan customer untuk membeli produk kudapan manis

MntGoldProds: jumlah uang yang dihabiskan customer untuk membeli produk emas

NumDealsPurchases: jumlah pembelian yang dilakukan customer melalui program diskon

NumWebPurchases: jumlah pembelian yang dilakukan customer melalui website

NumCatalogPurchases: jumlah pembelian yang dilakukan customer melalui katalog

NumStorePurchases: jumlah pembelian yang dilakukan customer di toko fisik

NumWebVisitsMonth: jumlah kunjungan customer ke website per bulan

AcceptedCmp3: apakah customer pernah menerima tawaran promosi Campaign 3 atau tidak

AcceptedCmp4: apakah customer pernah menerima tawaran promosi Campaign 4 atau tidak

AcceptedCmp5: apakah customer pernah menerima tawaran promosi Campaign 5 atau tidak

AcceptedCmp1: apakah customer pernah menerima tawaran promosi Campaign 1 atau tidak

AcceptedCmp2: apakah customer pernah menerima tawaran promosi Campaign 2 atau tidak

Complain: apakah customer pernah mengajukan keluhan atau tidak

Z_CostContact: biaya untuk setiap kontak yang dilakukan dengan customer

Z_Revenue: pendapatan yang dihasilkan dari setiap kontak yang dilakukan dengan customer

Response: apakah customer memberikan respon positif terhadap tawaran promosi atau tidak

Setelah memahami data, saya mencoba untuk menambahkan beberapa variabel agar dapat memahami data dan mengungkapkan informasi lebih baik
1. Variabel Age sebagai usia dari variabel Year_Birth
2. Variabel Spending sebagai jumlah dari 6 kategori produk yang di belanjakan oleh customer
3. Variabel Marital untuk mengelompokkan status perkawinan langsung 2 kategori yaitu: 'Couple' atau 'Alone'

Karena ada nya 24 missing values di variabel Income, saya memutuskan untuk mengisi nilai dengan mean atau median.

Untuk memutuskan antara mean atau median saya harus mengecek outlier data dan distribusi data nya terlebih dahulu
Memutuskan untuk meng drop data outlier dari Age dan Income, Spending tidak di drop
Setelah melihat histplot dan boxplot dan melihat distribusi nya right skewed saya memutuskan mengisi missing value dengan median

# 3. Data Visualisation

### Menentukan Customer Segment
Menggunakan histplot untuk melihat perbandingan jumlah customer dari Age
Bin 10: 43 sampai 45 tahun, jumlah customer: 130
Bin 11: 45 sampai 47 tahun, jumlah customer: 140
Bin 12: 47 sampai 49 tahun, jumlah customer: 152
Bin 13: 49 sampai 51 tahun, jumlah customer: 153
Bin 14: 51 sampai 53 tahun, jumlah customer: 164
*Dapat fokus ke customer yang rentang age nya dari umur 43 sampai 53*

Menggunakan barplot untuk melihat perbandingan education customer dari Income
dan melakukan uji One-way ANOVA.
Dari hasil visualisasi dapat dilihat bahwa Income dari pendidikan Basic sangat jauh berbeda dengan 4 variable lain nya.
Begitu pula uji statistik nya menunjukan hasil terdapat perbedaan yang signifikan.
*Dapat fokus ke customer yang memiliki Education: Graduation, PhD, Master dan 2n Cycle*

Menggunakan boxplot untuk membandingkan Marital dan Spending
dan melakukan uji T-statistik.
Dari hasil visualisasi dapat dilihat bahwa Spending dari variable ini tidak terlalu berbeda.
Begitu pula uji statistik nya menunjukan p-value yang lebih besar dari 0.05 maka tidak ada perbedaan yang signifikan.
*Kita tidak perlu memperhatikan Marital Status untuk masalah Customer Segment*

Menguji Spending dan Income menggunakan uji spearman.
Dari hasil uji spearman, variabel Spending dan Income memiliki hubungan. Dan karena Correlation coefficient nya lebih besar dari 0.7 maka hubungan nya sangat kuat.
*Maka betul bila saya menggunakan Income atau Spending sebagai acuan untuk perilaku Customer*

### Menganalisa produk
Dari 6 produk kita perlu melihat jumlah sales tiap produk lalu di uji statistik
- Nilai F-statistic sebesar 990.783 menunjukkan bahwa ada perbedaan yang signifikan antara produk.
- P-value yang kurang dari 0.05 juga menunjukkan adanya perbedaan yang signifikan antara setidaknya dua kelompok dalam sampel.
Dapat disimpulkan bahwa betul ada perbedaan yang signifikan antara total penjualan produk antara Wines, Fruits, Meat Products, Fish Products, Sweet Products, dan Gold Products.
Dilihat dari bar plot pun sudah jelas bahwa Wines dan Meat Products adalah 2 produk yang memiliki sales tertinggi.
Maka kita bisa fokus kepada 2 produk ini

### Menganalisa Purchases
Memvisualkan 4 purchases lalu di uji statistik
- Nilai F-statistic sebesar 731.221 menunjukkan bahwa ada perbedaan yang signifikan antara produk.
- P-value yang kurang dari 0.05 juga menunjukkan adanya perbedaan yang signifikan antara setidaknya dua kelompok dalam sampel.
Berdasarkan gambar barplot dan pie chart yang telah dihasilkan, terlihat bahwa channel pembelian yang paling banyak dilakukan oleh pelanggan adalah melalui toko fisik (store) dengan persentase sebesar 39%. Kemudian diikuti oleh pembelian melalui website (web purchases) sebesar 27.5%. Sedangkan pembelian melalui penawaran khusus (deals) memiliki persentase sebesar 15.6% dan pembelian melalui katalog (catalog) memiliki persentase sebesar 17.9%. Oleh karena itu, strategi pemasaran yang efektif dapat berfokus pada meningkatkan penjualan melalui Store dan Web purchases.


### Menganalisa Campaign

Memvisualkan accepted campaign percentage dan accepted campaign dengan response
Berdasarkan hasil uji statistik Chi-Square, dapat disimpulkan bahwa ada hubungan yang signifikan antara setiap Campaign dengan Response. Hal ini dapat dilihat dari nilai p-value yang sangat kecil (kurang dari 0.05) pada setiap uji statistik, sehingga dapat menolak hipotesis nol yang menyatakan bahwa tidak ada hubungan antara variabel tersebut.
Oleh karena itu, dapat dikatakan bahwa Campaign berpotensi mempengaruhi Response, perusahaan dapat mempertimbangkan campaign yang efektif untuk meningkatkan respons pelanggan.

# 4. Solving the problem

Setelah melakukan visualisasi data saya menyimpulkan:
1. Customer Segment: Fokus pada customer segment yang paling banyak jumlahnya yaitu customer dengan usia 43-53 tahun dan pendidikan PhD, Master, 2n Cycle, dan Graduation karena memiliki pendapatan yang tinggi.
2. Produk Unggulan: Fokus pada produk Wines dan Meat yang memiliki persentase pembelian yang tinggi.
3. Cara Jualan: Fokus pada Store Purchases dan Web Purchases yang memiliki jumlah pembelian yang tinggi.
4. Analisis Campaign: Menemukan bahwa campaign dapat meningkatkan jumlah response, tetapi tidak ada perbedaan yang signifikan antara Campaign 1, 3, 4, dan 5.

Maka *Insight* untuk perusahaan:
1. Personalization: Menggunakan customer segment untuk membuat pesan dan tawaran yang lebih relevan dan personal untuk segmen pelanggan perusahaan.
2. Marketing Channel: Pilih channel marketing yang paling efektif untuk mencapai Customer contoh seperti email, media sosial, atau iklan online
3. Developing product and services: Upaya mengembangkan produk dan layanan kita sesuai dengan kebutuhan dan preferensi Customer Segment
4. Loyalty Program: Buat program loyalitas sesuai Customer Segment untuk meningkatkan Retency atau repeat order dari Customer
5. Influencer: Cari influencer yang terkait dengan produk Wine dan Meat, dan gunakan mereka untuk mempromosikan produk kita. Pastikan mereka memiliki audiens yang relevan dengan 2 produk kita
6. Event or Expo: Ikuti acara expo atau event yang terkait dengan produk kita bukan hanya untuk jualan tapi untuk memperkenalkan produk kita (Brand Awareness) kepada lebih banyak orang atau bisa juga membangun jaringan bisnis
7. Branding: Fokus branding terhadap 2 produk kita ini untuk membangun Brand Awareness
8. Offline Promotion: Lakukan promosi offline atau langsung di toko fisik seperti pemasangan brosur atau iklan di tempat umum seperti stasiun atau pusat perbelanjaan untuk meningkatkan visibilitas toko fisik kita
9. Digital Marketing: Lakukan Marketing online secara teratur kepada pelanggan Anda untuk memberi tahu mereka tentang produk unggulan, Deals khusus, Catalog kita dan informasi terbaru tentang toko Anda.
10. Campaign: Menginvestigasi Campaign 2 karena angkanya sangat rendah dibandingkan dengan campaign lainnya. Tetap melakukan campaign 1, 3, 4, dan 5 karena persentasenya mirip dan menunjukkan konsistensi.
