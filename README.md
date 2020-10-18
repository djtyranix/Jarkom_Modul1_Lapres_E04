# Jarkom_Modul1_Lapres_E04
Repository untuk laporan resmi praktikum Jarkom 2020 - E04

* Michael Ricky
  0511184000078
  
* Qatrunada Qori Darwati
  05111840000059
  
# Display Filter

## Soal No. 1
Sebutkan web server yang digunakan pada "testing.mekanis.me"!

Pada soal ini, dapat langsung digunakan display filter ```http.host == testing.mekanis.me``` untuk melakukan filter
website ```testing.mekanis.me```. Lalu, klik salah satu dari packet yang ada, lalu klik kanan > follow > HTTP Stream.
Akan muncul sebuah windows baru yang isinya informasi tentang website tersebut. Akan terlihat juga web server yang
digunakan adalah **nginx/1.14.0 (Ubuntu)**.

![Nginx](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal1.png)

## Soal No. 5
Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!

Pada soal ini, mirip dengan soal no. 1, dapat digunakan display filter ```http.host == aku.pengen.pw``` untuk melakukan
filter website ```aku.pengen.pw```. Namun, ada display filter tambahan, yaitu ```http.authbasic``` karena website tesebut
menggunakan basic authentication. Klik packet paling atas, lalu extend bagian HTTP, lalu extend bagian Authorization. Akan
terlihat credentials, dimana usernamenya adalah **kakakgamtenk** dan passwordnya adalah **hartatahtabermuda**.

Setelah masuk websitenya, ada soal tentang urutan kabel T-568B. Jawabannya ada dalam screenshot dibawah ini :

![hartatahtabermuda](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal5.png)

## Soal No. 6
Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut).

Pada soal ini, dapat digunakan display filter ```ftp-data``` karena akan dicari file yang di transfer lewat protokol FTP. Setelah itu, dapat
dilakukan search string menggunakan search (Ctrl + F) lalu mengetikkan "Answer.zip" pada kolom pencarian string. Akan ditemukan packetnya. Lalu,
klik kanan > follow > TCP Stream. Di windows baru, ganti modenya menjadi RAW, lalu save as "Answer.zip". Saat dibuka, ada file PDF yang terkunci.

Untuk mencari passwordnya, dilakukan hal yang sama, yaitu ```ftp-data``` dan search string "zipkey.txt". Lalu, Follow TCP Streamnya, kemudian akan
langsung muncul passwordnya dalam format ASCII (tidak perlu dirubah ke RAW karena berbentuk .txt). Password untuk file .pdf tersebut adalah
**hey997400323051**. Berikut adalah isi dari file .pdf tersebut:

![passwordno6](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal6.png)

## Soal No. 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut.
Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"

Pada soal ini, dapat digunakan display filter ```ftp-data and frame contains "Yes.pdf"```. Hal ini membuat filter menyisakan file 473.zip yang dimana
file tersebut lah yang berisikan "Yes.pdf". Follow TCP Stream, ganti ke RAW, lalu save as 473.zip. Lalu buka filenya. Berikut adalah screenshot dari
file Yes.pdf:

![Yes.pdf](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal7.png)

## Soal No. 8
Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!

Pertama-tama, harus diketahui yang mana yang berasal dari Microsoft FTP Service. Gunakan display filter ```ftp contains "Microsoft FTP Service"```.
Ternyata, IP dari Microsoft FTP Service adalah ```198.246.117.106```.

Setelah diketahui IP asal microsoft, barulah digunakan display filter ```ftp.request.command ==  RETR and ip.dst_host == 198.246.117.106```.
Akan didapat file Readme. Jika di follow TCP streamnya, akan terlihat seperti ini:

![soal8](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal8.png)

## Soal No. 9
Cari username dan password ketika login FTP pada localhost!

FTP menggunakan command "USER" ketika ingin memasukkan username, dan "PASS" ketika ingin memasukkan password, sehingga dapat digunakan display filter
```ftp.request.command == USER or ftp.request.command == PASS```.

![soal9](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal9.png)

## Soal No. 10
Cari file .pdf di wireshark lalu download dan buka file tersebut! Clue = "25 50 44 46"

Clue yang diberikan adalah suatu rangkaian **HEX VALUE**, sehingga dapat dicari menggunakan HEX Search. Ctrl + F, lalu ganti modenya menjadi
hex value, lalu ketikkan angka angka tersebut beserta spasinya. Akan didapatkan satu packet. Kemudian, Follow TCP Stream, ganti menjadi RAW,
save as .pdf, lalu buka filenya. Akan ditampilkan sebagai berikut:

![soal10](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/soal10.png)
