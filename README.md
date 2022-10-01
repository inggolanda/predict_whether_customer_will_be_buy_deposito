# predict_whether_customer_will_be_buy_deposito
## Tentang Data

Projek ini menggunakan dua dataset, yaitu:

- train.csv: teridiri dari 45.211 baris dan 17 kolom diurutkan berdasarkan tanggal (dari Mei 2008 hingga November 2010)
- test.csv: teridiri dari 4521 baris dan 17 kolom, dipilih secara acak dari train.csv

##  Deskripsi Kolom
**Data Klien Bank**
- age: usia (numerikal)
- job: jenis pekerjaan (kategorikal: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
- marital: status pernikahan (kategorikal: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
- education: tingkat pendidikan (kategorikal: primary, secondary, tertiary and unknown)
- default: memiliki kredit sebelumnya? (kategorikal: 'no','yes','unknown')
- housing: memiliki cicilan rumah? (kategorikal: 'no','yes','unknown')
- loan: memiliki pinjaman pribadi? (kategorikal: 'no','yes','unknown')
- balance: saldo individual.

**Terkait dengan kontak terakhir dari kampanye saat ini**
- contact: jenis komunikasi ketika dihubungi (kategorikal: "unknown","telephone","cellular")
- day: hari atau tanggal terakhir dihubungi (numerikal)
- month: bulan terakhir dihubungi (kategorikal: "jan", "feb", "mar", …, "nov", "dec")
- duration: durasi kontak terakhir, dalam detik (numeric)

**Kolom lainnya**
- campaign: jumlah kontak yang dilakukan selama kampanye ini dan untuk klien ini (numerikal)
- pdays: jumlah hari yang berlalu setelah klien terakhir dihubungi dari kampanye sebelumnya (numerikal, -1 berarti klien belum dihubungi sebelumnya)
- previous: jumlah kontak yang dilakukan sebelum kampanye ini dan untuk klien ini (numerikal)
- poutcome: hasil dari kampanye pemasaran sebelumnya (kategorikal: "unknown","other","failure","success")

**Variabel Ouput (Target yang akan diprediksi)**
- y: apakah klien berlangganan deposito berjangka? (biner: "yes","no")

## TIPE DATA NUMERIKAL
- Pada kelompok numerikal, hampir semua kolom memiliki banyak outlier.  
- Pada kolom age tidak terlalu bermasalah karena hanya sebagian kecil saja yang menjadi outlier.  
- Pada kolom balance, duration, campaign didominasi oleh nilai yang kecil. Variasi data yang banyak pada nilai tinggi membuat oulier menjadi semakin banyak.  
- Pada kolom day tidak ada masalah.  
- Pada kolom pdays memiliki nilai -1 (belum dihubungi sebelumnya) yang mendominasi yaitu 36954 dari 45211 baris atau sekitar 81% data sehingga kotak menjadi berpusat pada nilai -1 sehingga nilai-nilai diatas -1 menjadi oulier yang cukup banyak sekitar 19%.  
- Pada kolom previous memiliki 0 yang mendominasi yang sesuai dengan nilai -1 pada kolom pdays karena nilai ini memiliki korelasi yang kuat. Sehingga selain dari nilai 0 akan menjadi outlier. Namun ada satu nilai yang benar-benar sangat jauh yaitu 275 (outlier ini dapat dihapus karena hanya satu saja dan jaraknya sangat jauh)   
- Yang perlu di follow up saat data pre-processing dapat melakukan standarisasi ataupun normalisasi. Solusi lainnya menggunakan sebagian besar data saja (misalnya 90% data)
- Dari nilai skewness dan visualisasi dapat dikatakan bahwa tipe data numerikal memiliki pola persebaran data skew positif dimana nilai mean lebih besar dari pada median, kecuali data kolom 'day' yang hampir menyerupai distribusi normal.

## Multivariate Analysis
- Korelasi antar feature dan label lemah. Namun, semua feature dapat dimanfaatkan untuk melakukan analisis kecuali feature 'month' dan 'pdays'.
- Korelasi antar feature lemah. Melakukan pengubahan tipe data kategorikal menjadi numerikal dan membuang kolom 'pdays' dikarenakan redundant dengan kolom 'previous'.

## **Insight Bisnis**
1. Nasabah yang dihubungi pada durasi dibawah 540 detik lebih berpotensi untuk berlangganan deposito. Rekomendasi bisnis yaitu untuk menemukan pola penawaran yang tepat, agar pemasaran telepon bisa dilakukan lebih efektif dengan durasi 2-9 menit.
2. Nasabah yang dihubungi 1-3 kali lebih berpotensi untuk berlangganan deposito. Rekomendasi bisnis yaitu melakukan campaign cukup 1-3 kali saja.
3. Usia pada rentang 20-40 tahun lebih berpotensi untuk berlangganan deposito. Rekomendasi bisnis yaitu melakukan pemasaran pada rentang usia 25-40 tahun karena nasabah terbanyak yang berlangganan berada pada rentang tersebut.


Banking Marketing Targets Dataset
https://www.kaggle.com/datasets/prakharrathi25/banking-dataset-marketing-targets
