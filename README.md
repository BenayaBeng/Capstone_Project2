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

### Menentukan produk yang perlu difokuskan

Dari 6 produk kita perlu melihat jumlah sales tiap produk lalu di uji statistik
