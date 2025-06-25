# Information disclosure
Judul lab:
1. [Information disclosure in error messages](#information-disclosure-in-error-messages)
2. [Information disclosure on debug page](#information-disclosure-on-debug-page)
3. [Source code disclosure via backup files](#source-code-disclosure-via-backup-files)
4. [Authentication bypass via information disclosure](#authentication-bypass-via-information-disclosure)

## Information disclosure in error messages
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%201.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%202.JPG)

- Klik tombol **View Details** pada salah satu produk

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%203.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%204.JPG)

- Pada tool Burp Suite terdeteksi request yang mengarah ke path `/product` dengan parameter `productId` bernilai 1

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%205.JPG)

- Klik kanan request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%206.jpg)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%207.JPG)

- Ubah nilai parameter `productId` dengan string

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%208.JPG)

- Jika sudah klik tombol **Send**. Scroll ke bawah pada bagian Response. Disana ditemukan informasi bahwa lab menggunakan Apache Struts versi `2 2.3.31`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%209.JPG)

- Klik tombol **Submit solution** kemudian masukkan versi Apache Struts diatas untuk menyelesaikan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2010.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2011.JPG)

- [Kembali ke judul](#information-disclosure)

## Information disclosure on debug page
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2012.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2013.JPG)

- Reload halaman lab di browser. Setelah buka menu Target > Site map di browser

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2014.JPG)

- Pada bagian Site map ditemukan endpoint `/cgi-bin/phpinfo.php`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2015.JPG)

- Klik kanan request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2016.jpg)

- Pindah ke tab Repeater dan klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2017.JPG)

- Cari `SECRET_KEY` pada bagian response. Copy secret key tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2018.JPG)

- Submit secret key untuk menyelesaikan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2019.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2020.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2021.JPG)

- [Kembali ke judul](#information-disclosure)

## Source code disclosure via backup files
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2022.JPG)

- Akses path `/robots.txt`. Disini ditemukan path `/backup`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2023.JPG)

- Buka path `/backup`. Disini ditemukan file `ProductTemplate.java.bak`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2024.JPG)

- Klik link `ProductTemplate.java.bak` untuk membuka file. Pada source code ditemukan sebuah password untuk mengakses database. Copy password tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2025.JPG)

- Kembali ke halaman awal lab. Input password database untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2026.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2027.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Information%20Disclosure/APPRENTICE/assets/disclosure%2028.JPG)

- [Kembali ke judul](#information-disclosure)

## Authentication bypass via information disclosure
- Akses lab



- [Kembali ke judul](#information-disclosure)