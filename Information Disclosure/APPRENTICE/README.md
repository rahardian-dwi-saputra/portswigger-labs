# Information disclosure
Judul lab:
1. Information disclosure in error messages
2. Information disclosure on debug page
3. Source code disclosure via backup files
4. Authentication bypass via information disclosure

## Information disclosure in error messages
- Akses lab

- Buka tool Burp Suite dengan kondisi Intercept Off

- Klik tombol **View Details** pada salah satu produk

- Pada tool Burp Suite terdeteksi request yang mengarah ke path `/product` dengan parameter `productId` bernilai 1

- Klik kanan request tersebut dan pilih **Send to Repeater**

- Pindah ke tab Repeater

- Ubah nilai parameter `productId` dengan string

- Jika sudah klik tombol **Send**. Scroll ke bawah pada bagian Response. Disana ditemukan informasi bahwa lab menggunakan Apache Struts versi `2 2.3.31`

- Klik tombol **Submit solution** kemudian masukkan versi Apache Struts diatas untuk menyelesaikan lab

## Information disclosure on debug page
- Akses lab

- Buka tool Burp Suite dengan kondisi Intercept Off

- Reload halaman lab di browser. Setelah buka menu Target > Site map di browser

- Pada bagian Site map ditemukan endpoint `/cgi-bin/phpinfo.php`

- Klik kanan request tersebut dan pilih **Send to Repeater**

- Pindah ke tab Repeater dan klik tombol **Send**

- Cari `SECRET_KEY` pada bagian response. Copy secret key tersebut

- Submit secret key untuk menyelesaikan lab

## Source code disclosure via backup files
- Akses lab

- Akses path `/robots.txt`. Disini ditemukan path `/backup`

- Buka path `/backup`. Disini ditemukan file `ProductTemplate.java.bak`

- Klik link `ProductTemplate.java.bak` untuk membuka file

- Pada source code ditemukan sebuah password untuk mengakses database. Copy password tersebut


- Kembali ke halaman awal lab. Input password database untuk menyelesaikan tantangan lab



## Authentication bypass via information disclosure