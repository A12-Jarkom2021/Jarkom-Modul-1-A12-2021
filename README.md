# Jarkom-Modul-1-A12-2021
Jarkom_Modul1_Lapres_A12

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

Karena kosong, maka dilakukan percobaan filter lainnnya menggunakan wireshark filter expression yaitu, ```ftp.response.code==150 || ftp.response.code==226```

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





