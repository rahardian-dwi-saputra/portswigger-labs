# Access control vulnerabilities
Judul lab
1. [Unprotected admin functionality](#unprotected-admin-functionality)
2. [Unprotected admin functionality with unpredictable URL](#unprotected-admin-functionality-with-unpredictable-url)
3. [User role controlled by request parameter](#user-role-controlled-by-request-parameter)
4. [User role can be modified in user profile](#user-role-can-be-modified-in-user-profile)
5. [User ID controlled by request parameter](#user-id-controlled-by-request-parameter)
6. [User ID controlled by request parameter, with unpredictable user IDs](#user-id-controlled-by-request-parameter-with-unpredictable-user-ids)
7. [User ID controlled by request parameter with data leakage in redirect](#user-id-controlled-by-request-parameter-with-data-leakage-in-redirect)
8. [User ID controlled by request parameter with password disclosure](#user-id-controlled-by-request-parameter-with-password-disclosure)
9. [Insecure direct object references](#insecure-direct-object-references)

## Unprotected admin functionality
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%201.JPG)

- Buka file `robots.txt` dengan menambahkan path `/robots.txt` pada URL. Disana terdapat halaman `administrator-panel` yang Disallow. `robots.txt` adalah file teks sederhana yang berisi instruksi untuk bot perayap web, seperti Googlebot, tentang bagian mana dari situs web yang boleh atau tidak boleh di-crawl dan diindeks

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%202.JPG)

- Buka halaman `administrator-panel`. Halaman `administrator-panel` bisa langsung diakses tanpa harus login sebagai `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%203.JPG)

- Hapus user `carlos` dengan klik link **Delete** untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%204.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%205.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## Unprotected admin functionality with unpredictable URL
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%206.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%207.jpg)

- Akan ditemukan script javascript yang didalamnya terdapat informasi path halaman admin yang merupakan bagian dari menu **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%208.JPG)

- Coba buka halaman `/admin-iw6e4b`. Path `/admin-iw6e4b` mengarah ke halaman **Admin panel** yang bisa langsung diakses tanpa harus login sebagai `administrator` 

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%209.JPG)

- Hapus user `carlos` untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2010.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2011.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## User role controlled by request parameter
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2012.JPG)

- Jika buka halaman `/admin` akan muncul pesan sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2013.JPG)

- Akses halaman login

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2014.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2015.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2016.JPG)

- Login menggunakan akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2017.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2018.JPG)

- Pada Burp Suite terdeteksi request yang mengarah ke path `/login` dan pada hasil responsenya terdapat informasi Cookie `Admin=false`. Kita bisa mengubahnya menjadi `Admin=true` sehingga user `wiener` akan dianggap sebagai role user `Administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2019.JPG)

- Kita akan mengubahnya melalui web browser. Klik kanan halaman dan pilih **Inspect**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2020.jpg)

- Pindah ke tab Penyimpanan kemudian ubah nilai Cookie Admin dari `false` menjadi `true`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2021.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2022.JPG)

- Reload halaman, maka akan tampil menu **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2023.JPG)

- Buka menu **Admin panel** kemudian hapus user **carlos** untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2024.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2025.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## User role can be modified in user profile
- Akses lab dan masuk ke menu **My Account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2026.JPG)

- Login menggunakan akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2027.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2028.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2029.JPG)

- Lakukan update email

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2030.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2031.JPG)

- Pada Burp Suite terekam request yang mengarah ke path `/my-account/change-email` untuk melakukan update email

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2032.JPG)

- Klik kanan request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2033.jpg)

- Pindah ke tab Repeater dan klik tombol **Send**. Pada response terdapat field `roleid:1`. Kita bisa menambahkan parameter `roleid` dengan nilai `2` dengan harapan bisa mengedit role user `wiener` menjadi `administrator` 

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2034.JPG)

- Tambahkan parameter `roleid` dengan value `2` pada bagian request. Jika sudah tekan tombol **Send**. Pada response, kita berhasil mengubah role user `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2035.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2036.JPG)

- Reload halaman **My Account** maka akan terdapat menu **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2037.JPG)

- Masuk ke halaman **Admin panel** kemudian delete user **carlos** untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2038.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2039.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## User ID controlled by request parameter
- Akses lab dan masuk ke menu **My Account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2040.JPG)

- Login menggunakan akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2041.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2042.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2043.JPG)

- Pada Burp Suite terekam request yang mengarah ke path `/my-account`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2044.JPG)

- Klik kanan request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2045.jpg)

- Pindah ke tab Repeater. Path `/my-account` diakses menggunakan parameter `id` dengan value berupa username dari suatu user. Hal ini memungkinkan attacker untuk mengubahnya dengan username orang lain untuk mengakses informasi user tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2046.JPG)

- Ubah nilai parameter `id` dari `wiener` menjadi `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2047.JPG)

- Jika sudah klik tombol **Send**. Pada response kita berhasil mengakses informasi user lain yaitu `carlos` yang di dalamnya terdapat informasi API key. Copy API key tersebut untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2048.JPG)

- Submit API key user `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2049.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2050.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2051.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## User ID controlled by request parameter, with unpredictable user IDs
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2052.JPG)

- Cari salah satu postingan, yang mana postingan tersebut diposting oleh user `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2053.JPG)

- Klik link user `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2054.JPG)

- Pada URL terdapat parameter `userId` yang merupakan `userId` user `carlos`. Copy nilai parameter tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2055.JPG)

- Klik menu **My Account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2056.JPG)

- Login menggunakan akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2057.JPG)

- Setelah berhasil login, amati URL pada halaman tersebut. Pada URL halaman **My Account** terdapat parameter id yang berisi id dari user `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2058.JPG)

- Ubah nilai parameter id tersebut dengan userId `carlos` yang sudah didapatkan pada langkah sebelumnya. Selanjutnya reload halaman tersebut sehingga didapat informasi akun user `carlos`. Copy API key user `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2059.JPG)

- Submit API key user `carlos` untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2060.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2061.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2062.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## User ID controlled by request parameter with data leakage in redirect
- Akses lab dan masuk ke menu **My account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2063.JPG)

- Login menggunakan akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2064.JPG)

- Setelah berhasil login, pada URL akan terdapat parameter `id` dengan value `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2065.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2066.JPG)

- Ubah nilai parameter id dari `wiener` menjadi `carlos` kemudian tekan enter

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2067.JPG)

- Halaman akan otomatis di redirect ke halaman login. Meskipun halaman telah di redirect ke halaman login, semua riwayat URL akan terekam otomatis pada tool Burp Suite

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2068.JPG)

- Pada Burp Suite terdeteksi halaman akun `carlos` yang di dalamnya memuat API key user `carlos`. Copy API key tersebut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2069.JPG)

- Submit API key user `carlos` untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2070.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2071.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2072.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## User ID controlled by request parameter with password disclosure
- Akses lab dan masuk ke menu **My account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2073.JPG)

- Login menggunakan akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2074.JPG)

- Setelah berhasil login, pada URL akan terdapat parameter `id` dengan value `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2075.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2076.JPG)

- Ubah nilai parameter `id` menjadi `administrator` kemudian tekan enter

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2077.JPG)

- Disini kita berhasil mengakses halaman update password `administrator`. Field password dalam kondisi terisi sehingga bisa digunakan untuk login sebagai `administrator`. Untuk isi field password bisa dilihat melalui inspect element di web browser atau pada response request di Burp Suite

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2078.JPG)

- Pada Burp Suite, kita berhasil menemukan password dari user `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2079.JPG)

- Logout dari akun `wiener`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2080.JPG)

- Login kembali menggunakan akun `administrator`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2081.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2082.JPG)

- Masuk ke halaman **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2083.JPG)

- Hapus user `carlos` untuk menyelesaikan tantangan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2084.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2085.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)

## Insecure direct object references
- Akses lab dan pergi ke menu **Live chat**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2086.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2087.JPG)

- Tulis sebuah pesan kemudian klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2088.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2089.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2090.JPG)

- Tekan tombol **View transcript**, maka web akan otomatis mendownload file dengan nama `2.txt`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2091.JPG)

- Pada Burp Suite terdeteksi request untuk mendownload file `2.txt`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2092.JPG)

- Klik kanan request tersebut kemudian pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2093.jpg)

- Pindah ke tab Repeater dan klik tombol **Send**. Pada response akan memuat isi dari file `2.txt`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2094.JPG)

- Karena nama file hanya menggunakan angka integer, kita bisa mengurutkannya ke belakang atau kedepan untuk membaca isi file lain dengan memanfaatkan request yang berhasil direkam oleh tool Burp Suite. Ubah nama file dari `2.txt` menjadi `1.txt` kemudian klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2095.JPG)

- Pada response ditemukan sebuah password. Berdasarkan arahan lab, password tersebut dapat digunakan untuk login dengan username `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2096.JPG)

- Masuk ke menu **My account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2097.JPG)

- Login dengan menggunakan username `carlos` dan password yang sudah ditemukan pada langkah sebelumnya

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2098.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/APPRENTICE/assets/access%20control%2099.JPG)

- [Kembali ke judul](#access-control-vulnerabilities)