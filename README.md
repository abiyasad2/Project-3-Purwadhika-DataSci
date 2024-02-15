# Saudi Used Car Sales Regression

### Business Problem Understanding

#### Context

syarah.com adalah sebuah platform penjualan mobil baru dan bekas yang berkantor pusat di Riyadh, Saudi Arabia. Melalui aplikasi syarah.com, pengguna dapat mencari, membeli mobil dan mendapatkan layanan purna jual seperti pengiriman mobil, garansi dan servis. Pengguna cukup mencari mobil yang diinginkan di web atau aplikasi dan memfilter berdasarkan harga, tahun dan berbagai kriteria lainnya. Harga yang ditampilkan di website dapat menjadi acuan, namun syarah.com juga menyediakan opsi untuk melakukan negosiasi harga

#### Problem Statement

Penentuan harga pada segmen Negotiable merupakan hak kedua belah pihak yang melakukan negosiasi, yaitu penjual dan pembeli. Di sisi lain, Syarah perlu menjaga harga mobil yang dijual agar tetap kompetitif.  Harga tersebut dipengaruhi berbagai faktor, di antaranya pasar penjualan, fasilitas tambahan yang diberikan, merek mobil, usia dan faktor-faktor lainnya. 

#### Goals

Tujuan dari pemodelan yang dilakukan adalah menentukan harga mobil yang tepat sesuai dengan karakteristik kendaraan serta tempat pemasaran mobil, serta mengetahui faktor yang mempengaruhi penentuan harga mobil

#### Analytic Approach

Model yang digunakan untuk memprediksi harga adalah model berbasis regresi, dengan Price sebagai variabel target dan kolom-kolom lain dalam dataset sebagai prediktor. Setiap variabel prediktor  akan memiliki kontribusi sendiri dalam menentukan harga yang sesuai, namun setelah mempertimbangkan keterkaitan dengan harga serta bias  yang terjadi dari korelasi sesama variabel prediktor.

Dataset akan terbagi menjadi Non Negotiable dan Negotiable, dengan Non Negotiable memiliki harga yang tetap. Model akan dilatih dan diuji terlebih dahulu pada data Non-Negotiable  sebelum memprediksi harga pada data Non Negotiable

#### Metric Evaluation

Evaluasi akan menggunakan MAE, MAPE serta MSE, dan  bila model terpilih adalah linear maka akan juga menggunakan R squared. Kesemua metrik ini dibandingkan untuk mendapatkan metrik yang terkecil


### Data Understanding


Dataset ini memiliki 5624 baris yang diperoleh dari syarah.com. Setiap  baris berisi informasitentang satu unit mobil bekas, yang mencakup tipe, region, merek, transmisi, asal negara, ketersediaan fasilitas, tahun, ukuran mesin, mil di odometer, status negosiasi serta harga. Adapun penjelasan masing-masing kolom yaitu sebagi berikut:

#### Features

* Type: Tipe mobil
* Region: Wilayah tempat mobil akan dipasarkan
* Make: Merek mobil
* Gear_Type: Tipe transmisi/gear yang digunakan (Auto/Matic)
* Origin: Asal negara mobil bekas 
* Options: Kelengkapan fasilitas terpasang pada mobil, seperti kamera, sunroof, power window dll.,  referensi: (link)
* Year: Tahun pembuatan
* Engine_Size: Ukuran mesin mobil bekas
* Mileage: Mil yang sudah ditempuh mobil bekas
* Negotiable: True jika Price 0, harga dapat dinegosiasikan
* Price: Used car price (dalam Saudi riyal)


### Conclusion

Model yang paling sesuai untuk melakukan prediksi harga mobil yaitu Random Forest Regression. Model ini masih jauh dari ideal, mengingat saat memprediksi  gugus data testing, Mean Absolute Error prediksi Price menjadi sebesar 12113 riyal. Mean Absolute Percentage Error juga lebih dari 50%, yaitu 60,8%, yang berarti prediksi yang dibuat model akan melesai maksimal hingga 60,8% dari nilai prediksi. Fitur yang paling berpengaruh dalam regresi ini yaitu Engine_Size (ukuran mesin), Age (usia mobil) serta Mileage (mil pada odometer).

### Recommendation

1. Melakukan improvisasi pada encoding sehingga dapat berkontribusi lebih pada model. Dalam eksplorasi data yang dilakukan, di sejumlah variabel prediktor kategorik terdapat perbedaan Price antara setiap value kategorik, namun tidak berpengaruh besar pada modl keseluruhan. Adanya variabel interaksi atau metode encoding ordinal mungkin akan menangkap lebih jelas keragaman ini.
2. Jumlah error yang besar pada hasil prediksi mengindikasikan adanya variabel yang belum terakomodasi, sehingga disarankan untuk isolasi prediksi yang paling melaeset dan temukan variabel mana saha yang dapat menjelaskan variasi ini. 
3. Melakukan augmentasi data dengan fitur-fitur baru. Pada kolom Options informasi yang didapatkan terlalu umum (opsi lengkap, sebagian atau minimum), namun bisa diperkaya dengan informasi spesifik fitur apa yang ditambahkan ke mobil (soundd system, alarm, power window dll.)


