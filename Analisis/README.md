# Analisis 

Analisis Problem Beecrowd Hopscotch Marathon
problem ini mengharuskan kita untuk menghitung pada ronde ke berapa peserta mencapai urutan/kursi ke nol.
Terdapat 5 elemen utama pada problem ini:
1.	N = Jumlah peserta
2.	Ai = Posisi peserta 
3.	Q = banyaknya ronde
4.	cq = number yang menentukan peserta yang dipilih
5.	dq = number yang menentuka peserta yang dipilih cq untuk mundur sejumlah dq langkah
setiap ronde akan ada perubahan tertentu posisi peserta. 

Format input berupa :
1.	baris pertama N dan Q, dimana N adalah banyaknya peserta dan Q adalah banyaknya Ronde.
2.	Baris kedua berisi Ai dimana menyatakan posisi tiap peserta.
3.	Baris selanjutnya sebanyak Q baris menyatakan cq dan dq, dimana peserta yang dipilih cq akan mundur sebanyak dq
Cara menentukan peserta mana yang bergerak setiap ronde adalah dengan mencocokkan antara cq dan urutan peserta. Kecocokan ini berdasarkan dari faktor yang sama. Jadi jika kedua variabel tersebut memiliki faktor yang sama (kecuali 1) maka peserta pada urutan tersebut akan bergerak.

Misal contoh input :


``` 
7 6
10 20 30 40 50 60 70
2 25
3 36
100 42
5 10
7 70
1 1000 
```





Maka perhitungannya akan seperti berikut :

Peserta awal :

| peserta |	letak |	Ronde |
|----------|--------|--------|
| 1 | 10 | -1 |
| 2 | 20 | -1 |
| 3 | 30 | -1 |
| 4 | 40 | -1 |
| 5 | 50 | -1 |
| 6 | 60 | -1 |
| 7 | 70 | -1 |


-	Ronde 1 : c1 = 2

kita cari urutan peserta yang memiliki faktor sama dengan 2. Jumlah peserta ada 7, dari ke-7 angka tersebut yang memiliki faktor 2 adalah : 2,4,6. Maka peserta dengan nomor urut 2,4,6 akan mundur sebanyak 25 langkah.

| peserta |	letak |	ronde |
|----------|--------|--------|
| 1 | 10 |  -1 |
| 2 | 0	 |   1 |
| 3 | 30 |	-1 |
| 4 | 15 |	-1 |
| 5 | 50 |	-1 |
| 6 | 35 | 	-1 |
| 7 | 70 | 	-1 |


-	Ronde 2 : c2 = 3

Yang memiliki faktor sama dengan 3 adalah 3 dan 6. Maka peserta dengan nomor urut 3 dan 6 mundur sebanyak 36 langkah

| peserta |	letak |	ronde |
|----------|--------|--------|
| 1 |	10 | -1 |
| 2 |	0 | 1 |
| 3 |	0 | 2 |
| 4 |	15 | -1 |
| 5 |	50 | -1 |
| 6 |	0 | 2 |
| 7 |	70 | -1 |


-	Ronde 3 : c3 = 100

Faktor dari 100 adalah 2 dan 5, angka yang memiliki faktor sama dengan 100 adalah 2,4,5,6. Maka mundur sebanyak 42 langkah

| peserta |	letak |	ronde |
|----------|--------|--------|
| 1 |	10 |	-1 |
| 2 |	0 |	1 |
| 3 |	0 |	2 |
| 4 |	0 |	3 |
| 5 |	8 |	-1 |
| 6 |	0 |	2 |
| 7 |	70 |	-1 |


-	Ronde 4 : c4 = 5

Yang memiliki faktor sama dengan 5 adalah nomor urut 5. Maka mundur 10 langkah

| peserta |	letak |	ronde |
|----------|--------|--------|
| 1 |	10	 | -1 |
| 2 |	0 | 	1 |
| 3 |	0 | 	2 |
| 4 |	0 | 	3 |
| 5 |	0 | 	4 |
| 6 |	0 | 	2 |
| 7 |	70	 | -1 |


-	Ronde 5 : c5 = 7

Yang memiliki faktor sama dengan 7 dalah nomor urut 7, mundur 70 langkah.

| peserta |	letak |	ronde |
|----------|--------|--------|
| 1 |	10 | 	-1 |
| 2 |	0	 | 1 |
| 3 |	0	 | 2 |
| 4 |	0	 | 3 |
| 5 |	0	 | 4 |
| 6 |	0	 | 2 |
| 7 |	0	 | 5 |


-	Ronde 6 : c6 = 1

Faktor yang dicari 1 sedangkan 1 ini tidak termasuk dalam constraint faktor yang diminta. Kalaupun c6 > 1 tidak akan ada perubahan pada tabel karena semua tabel sudah terisi kecuali untuk baris ke-1, baris ini sepertinya akan selalu tidak berubah karena dibutuhkan faktor dari 1 dimana kondisi faktor 1 tidak memenuhi, sehingga tidak akan pernah mencapai angka 0

Dengan ini hasil adalah -1,1,2,3,4,2,5

Secara sekilas soal ini terlihat mudah untuk diselesaikan. Kita hanya perlu mengecek urutan peserta disetiap ronde jika cocok maka dilakukan pengurangan dan menyimpan data nya menggunakan array vector ataupun map, terus dilakukan sampai ronde selesai. Namun, yang jadi permasalahannya adalah ketika input nya terlalu besar, hal ini dapat menyebabkan time limit karena harus selalu mengecek semua urutan secara terus menerus. 


Maka dari itu perlu dilakukan optimasi untuk mengurangi prosess khususnya saat pengecekan salah satunya menggunakan binary search. Saya masih belum melakukan riset lebih lanjut mengenai tekni optimasi pada permasalahan ini. Untuk progress selanjutnya saya akan mencari referensi terkait teknik optimasi ini.

