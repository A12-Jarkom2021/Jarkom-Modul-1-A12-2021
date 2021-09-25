# Jarkom-Modul-1-A12-2021
Jarkom_Modul1_Lapres_A12

**Praktikum Modul 1 - Jaringan Komputer 2021**
**A12**
-   Fiqey Indriati Eka Sari (05111940000015)
-   Dyah Putri Nariswari (05111940000047)
-   Muhammad Farrel Abhinaya (05111940000173)

### Soal 1
Sebutkan web server yang digunakan pada \"[[ichimarumaru.tech]{.ul}](http://ichimarumaru.tech/)\"!

**wireshark filter expression:** http.host contains "ichimarumaru.tech"

> Untuk mengetahui web server yang digunakan dapat menuliskan expression
> http.host contains "ichimarumaru.tech"

<img src="./media/image8.png" width="720">

**wireshark filter expression:** tcp.stream eq 43

Lalu, lakukan Follow -\> TCP stream dan ditemukan hasil seperti berikut.
Web server yang digunakan ialah ECS (frv/669E)

<img src="./media/image18.png" width="720">

### Soal 2
Temukan paket dari **web-web** yang menggunakan **basic authentication** method!

> **wireshark filter expression:** http.authbasic
>
> <img src="./media/image2.png" width="720">

### Soal 3

Ikuti perintah di [[basic.ichimarumaru.tech]{.ul}](http://basic.ichimarumaru.tech/)! Username dan password bisa didapatkan dari file .*pcapng*!

**wireshark filter expression:** http.host contains "basic.ichimarumaru.tech"

> Pertama kita mengisi filter dengan expression http.host contains
> "basic.ichimarumaru.tech"
>
> <img src="./media/image3.png" width="720">
>
> Setelah itu, kita temukan credentials yang berisi username dan
> password untuk menuju ke web basic.ichimarumaru.tech

**wireshark filter expression:** http.host contains
basic.ichimarumaru.tech

> <img src="./media/image22.png" width="720">
>
> <img src="./media/image26.png" width="720">
>
> Web berhasil terbuka, dan diminta untuk mengisi jawaban dari soal yang
> tertera
>
> <img src="./media/image13.png" width="720">

### Soal 4
Temukan paket **mysql** yang mengandung **perintah** **query select**!

> **wireshark filter expression:** mysql.query contains "select" \|\|
> mysql.query contains "SELECT"
>
> <img src="./media/image23.png" width="720">
>
> <img src="./media/image19.png" width="720">

### Soal 5
Login ke [[portal.ichimarumaru.tech]{.ul}](http://portal.ichimarumaru.tech/) kemudian ikuti perintahnya! Username dan password bisa didapat dari **query insert** pada table **users** dari file .pcap!

> **wireshark filter expression:** mysql.query contains "INSERT"
>
> <img src="./media/image27.png" width="720">
>
> INSERT INTO users (username,password) VALUES
> (\"akakanomi\",md5(\"pemisah4lautan\"))
>
> <img src="./media/image30.png" width="720">

### Soal 6
Cari username dan password ketika melakukan login ke FTP Server!

Untuk mencari username dan password dapat menggunakan wireshark filter expression yaitu, ```ftp.request.command contains USER || ftp.request.command contains PASS```. Didaptkan username: secretuser dan pass: aku.pengen.pw.aja

![Screenshot (1710)](https://user-images.githubusercontent.com/71380876/134739947-95c5b875-9ae6-4017-bf39-022ed46de7af.png)

### Soal 7
Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Mengisi display filter dengan wiresshark filter expression yaitu, ```frame contains “Real.pdf”```. 

![Screenshot (1707)](https://user-images.githubusercontent.com/71380876/134758461-f44938e5-a0be-401d-bc6c-2a6eaf05678e.png)

Lalu, Follow --> TCP Stream dan mengubah data menjadi Raw. Setelah itu simpan file dengan nama Real.pdf. Wireshark filter expression nya yaitu, ```tcp.stream eq 128```

![Screenshot (1708)](https://user-images.githubusercontent.com/71380876/134758513-4fa03887-2ee2-4627-aaf9-d759c6c085a6.png)

File, Real.pdf berhasil dibuka

![Screenshot (1709)](https://user-images.githubusercontent.com/71380876/134758815-3479d416-45f2-46c4-b170-e85d45f9c943.png)

### Soal 8
Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Gunakan wireshark filter expression ```ftp.request.command == RETR```

![Picture1](https://user-images.githubusercontent.com/71380876/134761965-e527936b-d79c-48b2-a945-56c293aaa1a5.png)

Karena kosong, maka dilakukan percobaan filter lainnnya menggunakan wireshark filter expression yaitu, ```ftp.response.code==150 || ftp.response.code==226```

![Picture2](https://user-images.githubusercontent.com/71380876/134761976-8c6698e8-e441-4f41-91f4-efde2453d537.png)

### Soal 9
Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Mengisikan display filter dengan wireshark filter expression yaitu, ```ftp-data```

![Screenshot (1711)](https://user-images.githubusercontent.com/71380876/134759171-1b8d21c3-7064-4168-a792-27926dc10e30.png)

Lalu, Follow --> TCP Stream dan mengubah data menjadi Raw. Setelah itu simpan file dengan nama secret.zip. Wireshark filter expression nya yaitu, ```tcp.stream eq 10```.

![Screenshot (1713)](https://user-images.githubusercontent.com/71380876/134759351-a3bd9e9e-6cf1-4964-80cf-12783854085b.png)

![Screenshot (1714)](https://user-images.githubusercontent.com/71380876/134759362-cd7eb686-26fd-45ce-97fc-df7bfd7e5eae.png)

### Soal 10
Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!

Mengisikan display filter dengan wireshark filter expression yaitu, ```ftp-data```

![Screenshot (1711)](https://user-images.githubusercontent.com/71380876/134759398-e63f03f3-e43d-463e-8dd3-dbe609f7bd65.png)

Lalu, Follow --> TCP stream dan ditemukan hasil seperti berikut. Wireshark filter expression nya yaitu, ```tcp.stream eq 9```

![Screenshot (1715)](https://user-images.githubusercontent.com/71380876/134759415-5cb919ba-fd31-43dd-b675-6aed92e44ef7.png)

Selanjutnya, masukan lagi wireshark filter expression, ``ftp-data``. Lalu, kita mencari paket yang mengandung file bukanapaapa.txt

![Screenshot (1718)](https://user-images.githubusercontent.com/71380876/134759605-9ea19175-bf62-44f5-b259-2006ea6ec443.png)

Lalu, lakukan Follow --> TCP stream dan didapat password untuk membuka file secret.zip. Wireshark filter expression nya yaitu, ```tcp.stream eq 11```

![Screenshot (1716)](https://user-images.githubusercontent.com/71380876/134759620-0be10198-3c8f-4ca5-957a-3080885556c2.png)

Masukan password untuk membuka file secret.zip. File berhasil dibuka

![Screenshot (1717)](https://user-images.githubusercontent.com/71380876/134759639-ff3fbd4a-db3b-4f6a-a7b0-4e3fff5d9397.png)

### soal 11
Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80

__Wireshark filter expression__ : ```udp.srcport == 80 || tcp.srcport == 80```

![image](https://user-images.githubusercontent.com/81466736/134759894-e9c61a46-5f63-42e0-b541-d6eaecd4672a.png)

### soal 12
Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

__Wireshark filter expression__ : ```port 21```

![image](https://user-images.githubusercontent.com/81466736/134760177-c96017bd-c658-46b8-9960-734c2fc52750.png)

### soal 13
Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

__Wireshark filter expression :__ ```dst port 443```

![image](https://user-images.githubusercontent.com/81466736/134760164-42805a4d-29a1-4f1a-8249-010f9a62ab42.png)

### soal 14
Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

pertama, buka kemenag.go.id

![image](https://user-images.githubusercontent.com/81466736/134760065-8c7039de-bc04-4257-bb48-a35c48859591.png)

kemudian isi __Wireshark filter expression__ dengan ```dst host kemenag.go.id``` lalu lakukan refresh pada page kemenag.go.id

![image](https://user-images.githubusercontent.com/81466736/134760126-ace0614c-c398-4b96-9b6f-b73b5e3d203b.png)

### soal 15
Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Ip yang digunakan :

Untuk mengetahui ip, dapat menggunakan perintah ```ipconfig``` pada terminal

![image](https://user-images.githubusercontent.com/81466736/134760138-8613795b-7f79-406e-aeb7-3a7cd7482fa1.png)

__Wireshark filter expression :__ ```src host 192.168.1.6```

![image](https://user-images.githubusercontent.com/81466736/134760147-22aa72c9-ab88-45be-9d83-bf7aa7cb483f.png)

## Kendala
- Pada soal nomor 1, sempat terjadi kesalahan karena host yang dipilih ternyata bukan ichimarumaru.tech
