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

## Soal No. 2
Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!

Pertama, digunakan display filter ```http.request.uri contains "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"``` untuk memastikan bahwa gambar dengan nama tersebut terdapat pada salah satu paket dalam file soal_jarkom_modul1_no1-5,10.pcapng.

![Soal2-1](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-2-Wireshark-1.JPG)

Lalu, untuk menyimpan gambar tersebut, klik File > Export Objects > Pilih HTTP. Lalu masukkan nama file yang diminta pada text filter, dalam hal ini **Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg**, lalu klik Save dan jangan lupa tambahkan ekstensi **jpg**.

![Soal2-2](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-2-Wireshark-2.JPG)

Adapun hasilnya adalah seperti ini.

![Soal2-3](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-2-Hasil.JPG)

## Soal No. 3
Cari username dan password ketika login di "ppid.dpr.go.id"!

Untuk mendapatkan username dan password, dapat menggunakan display filter ```http.request.method == POST``` karena login biasanya menggunakan method POST. Kebetulan, karena hasilnya cuma ada satu paket saja yang menggunakan method POST jadi hampir bisa dipastikan kalau username dan password yang diminta soal yaitu 10pemuda dan guncangdunia secara berurutan.

Untuk memastikannya, disini kami coba untuk melihat host dari paket tersebut. Dapat terlihat pada screenshot dibawah kalau host dari paket tersebut yaitu ppid.dpr.go.id sehingga dapat dipastikan username **10pemuda** dan password **guncangdunia** merupakan username dan password yang kita cari.

![Soal3](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-3.JPG)

## Soal No. 4
Temukan paket dari web-web yang menggunakan basic authentication method!

Menemukan paket dari web yang menggunakan basic authentication method cukup dengan menggunakan display filter ```http.authbasic```.

![Soal4](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-4.JPG)

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

# Capture Filter

## Soal No. 11
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Karena kita hanya diminta untuk mengambil paket yang mengandung port 21 tidak peduli paket itu berasal dari atau menuju port tersebut maka capture filter yang digunakan cukup ```port 21```.

![Soal11](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-11.JPG)

## Soal No. 12
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Karena diminta untuk mengambil paket yang berasal dari port 80 maka capture filter yang digunakan untuk mendapatkan paket tersebut yaitu ```src port 80```.

![Soal12](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-12.JPG)

## Soal No. 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Karena diminta untuk mengambil paket yang menuju ke port 443 maka capture filter yang digunakan untuk mendapatkan paket tersebut yaitu ```dst port 443```.

![Soal13](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-13.JPG)

## Soal No. 14
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Karena diminta untuk mengambil paket yang berasal dari ip kami maka capture filter yang digunakan untuk mendapatkan paket tersebut yaitu ```src host 192.168.100.7``` setelah sebelumnya kami mencari alamat dari ip kami.

![Soal14](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-14.JPG)

## Soal No. 15
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!

Karena diminta untuk mengambil paket yang menuju ke monta.if.its.ac.id maka capture filter yang digunakan untuk mendapatkan paket tersebut yaitu ```dst host monta.if.its.ac.id```.

![Soal15](https://github.com/djtyranix/Jarkom_Modul1_Lapres_E04/blob/master/img/Soal-15.JPG)
