# Access control vulnerabilities
Judul lab:
1. [URL-based access control can be circumvented](#url-based-access-control-can-be-circumvented)
2. [Method-based access control can be circumvented](#method-based-access-control-can-be-circumvented)
3. [Multi-step process with no access control on one step](#multi-step-process-with-no-access-control-on-one-step)
4. [Referer-based access control](#referer-based-access-control) 

## URL-based access control can be circumvented
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%201.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%202.JPG)

- Akses halaman **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%203.JPG)

- Saat diakses muncul pesan `Access denied`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%204.JPG)

- Pada Burp Suite terdeteksi request yang mengarah ke path `/admin`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%205.JPG)

- Klik kanan request tersebut kemudian pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%206.jpg)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%207.JPG)

- Ubah path dari `/admin` menjadi `/` kemudian tambahkan header `X-Original-URL: /invalid`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%208.JPG)

- Jika sudah klik tombol **Send**. Pada response terdapat keterangan `Not found` yang menandakan backend telah memproses URL `/invalid` namun halaman tidak ditemukan sehingga memunculkan pesan `Not found`. `X-Original-URL` adalah  jenis header HTTP yang digunakan untuk menyampaikan informasi tentang URL aslinya saat terjadi redirect. Saat terjadi redirect ke URL yang baru `X-Original-URL` akan mencatat URL sebelumnya sebelum terjadi proses redirect

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%209.JPG)

- Sekarang kita ubah nilai header `X-Original-URL` dari `/invalid` menjadi `/admin`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2010.JPG)

- Jika sudah klik tombol **Send**. Pada response kita berhasil mengakses halaman admin. Terlihat path `/admin/delete?username=carlos` untuk menghapus user carlos

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2011.JPG)

- Tambahkan query `?username=carlos` kemudian ubah nilai header `X-Original-URL` dari `/admin` menjadi `/admin/delete`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2012.JPG)

- Jika sudah klik tombol **Send**. Pada response terdapat HTTP Code 302 yang artinya redirect. Klik tombol **Follow redirection** untuk mengikuti redirect

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2013.JPG)

- Redirect mengarah ke halaman `/admin` dengan response `Access denied`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2014.JPG)

- Reload halaman `/` maka akan tampil pesan lab berhasil terselesaikan

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2016.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## Method-based access control can be circumvented
- Akses lab dan masuk ke menu **My Account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2017.JPG)

- Login sebagai `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2018.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2019.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2020.JPG)

- Promote user `carlos` menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2021.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2022.JPG)

- Pada Burp Suite terdeteksi yang mengarah ke path `/admin-roles` yang digunakan untuk mengupgrade user biasa menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2023.JPG)

- Klik kanan request tersebut kemudian pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2024.jpg)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2025.JPG)

- Logout dari user `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2026.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2027.JPG)

- Login sebagai `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2028.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2029.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2030.JPG)

- Cari request di Burp Suite yang memuat cookies user `wiener`. Copy cookies tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2031.JPG)

- Pindah ke tab Repeater, ubah cookies user `administrator` dengan cookies user `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2032.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2033.JPG)

- Jika sudah klik tombol **Send**. Pada response terdapat keterangan "Unauthorized"

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2034.JPG)

- Ubah request `POST` menjadi `POSTX` kemudian klik tombol **Send**. Pada response terdapat pesan "missing parameter"

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2035.JPG)

- Ubah request dengan cara klik kanan lalu pilih **Change request method**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2036.jpg)

- Setelah itu ubah username dari `carlos` menjadi `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2037.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2038.JPG)

- Jika sudah klik tombol **Send** setelah itu klik tombol **Follow redirection**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2039.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2040.JPG)

- Tantangan berhasil diselesaikan, jika halaman akun `wiener` di reload akan terdapat menu **Admin panel** yang menandakan bahwa user `wiener` telah menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2041.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2042.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## Multi-step process with no access control on one step
- Akses lab dan masuk ke menu **My Account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2043.JPG)

- Login sebagai `administrator`. Buka halaman **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2044.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2045.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2046.JPG)

- Promote user `carlos` menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2047.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2048.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2049.JPG)

- Pada Burp Suite terdeteksi yang mengarah ke path `/admin-roles` dengan parameter `confirmed=true` yang digunakan untuk mengupgrade user biasa menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2050.JPG)

- Klik kanan request tersebut kemudian pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2051.jpg)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2052.JPG)

- Logout dari user `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2053.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2054.JPG)

- Login sebagai `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2055.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2056.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2057.JPG)

- Cari request di Burp Suite yang memuat cookies user `wiener`. Copy cookies tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2058.JPG)

- Pindah ke tab **Repeater**. Ganti cookie `administrator` dengan cookie `wiener`. Kemudian ubah value parameter username dari `carlos` dengan `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2059.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2060.JPG)

- Jika sudah klik tombol **Send** setelah itu klik tombol **Follow redirection**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2061.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2062.JPG)

- Tantangan berhasil diselesaikan, jika halaman akun `wiener` di reload akan terdapat menu **Admin panel** yang menandakan bahwa user `wiener` telah menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2063.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2064.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## Referer-based access control
- Akses lab dan masuk ke menu **My Account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2065.JPG)

- Login sebagai `administrator`. Buka halaman **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2066.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2067.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2068.JPG)

- Promote user `carlos` menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2069.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2070.JPG)

- Pada Burp Suite terdeteksi yang mengarah ke path `/admin-roles` yang digunakan untuk mengupgrade user biasa menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2071.JPG)

- Klik kanan request tersebut kemudian pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2072.jpg)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2073.JPG)

- Logout dari user `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2074.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2075.JPG)

- Login sebagai `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2076.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2077.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2078.JPG)

- Cari request di Burp Suite yang memuat cookies user `wiener`. Copy cookies tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2079.JPG)

- Pindah ke tab **Repeater**. Ganti cookie `administrator` dengan cookie `wiener`. Kemudian ubah value parameter username dari `carlos` dengan `wiener`. Untuk percobaan pertama hilangkan header Referer

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2080.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2081.JPG)

- Jika sudah klik tombol **Send**. Maka muncul pesan "Unauthorized"

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2082.JPG)

- Kembalikan header Referer seperti semula

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2083.JPG)

- Jika sudah klik tombol **Send** setelah itu klik tombol **Follow redirection**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2084.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2085.JPG)

- Tantangan berhasil diselesaikan, jika halaman akun `wiener` di reload akan terdapat menu **Admin panel** yang menandakan bahwa user `wiener` telah menjadi admin

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2086.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2087.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)