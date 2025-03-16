# HTTP Host header attacks

## Basic password reset poisoning
- Vulnerability berada di fitur "Forgot Password". Klik link **My account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%201.JPG)

- Klik link **Forgot Password?**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%202.JPG)

- Buka tool Burp Suite dengan kondisi Intercept On

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%203.JPG)

- Masukkan username `wiener` dan klik tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%204.JPG)

- Setelah Burp Suite terbuka, klik kanan request dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%205.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%206.JPG)

- Selanjutnya tekan tombol **Forward** lalu matikan Intercept 

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%207.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%208.JPG)

- Buka exploit server di tab baru

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%209.JPG)

- Pindah ke tab Exploit Server, scroll kebawah dan klik tombol **Email Client** untuk mengakses email

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2010.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2011.JPG)

- Buka Burp Suite dan pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2012.JPG)

- Ubah nilai Host dengan nilai lain misalnya `abc123` kemudian klik Tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2013.JPG)

- Reload halaman **Email Client** di browser, maka akan didapat email dengan link seperti berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2014.JPG)

- Sekarang kita ubah Host dengan domain exploit server yang terdapat pada URL exploit server dan ubah nilai username menjadi `carlos`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2016.JPG)

- Jika sudah klik tombol **Send**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2017.JPG)

- Sekarang akses Log Server untuk melihat hasil. Klik tombol **Back to exploit server** setelah itu scroll kebawah dan klik tombol **Access log**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2018.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2019.JPG)

- Pada log server akan terekam request ke path `/forgot-password`, copy value `temp-forgot-password-token`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2020.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2021.JPG)

- Buka kembali menu **Email client** pada exploit server

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2022.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2023.JPG)

- Akses link reset password yang diterima pada email sebelumnya

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2024.JPG)

- Ubah nilai parameter `temp-forgot-password-token` dengan nilai token yang didapat pada Log server sehingga akan tampil halaman reset password seperti berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2025.JPG)

- Isi password sesuai keinginan kemudian klik tombol **Submit**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2026.JPG)

- Akses link **My account**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2027.JPG)

- Login menggunakan username `carlos` dan password yang sudah diinput sebelumnya untuk menyelesaikan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2028.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/HTTP%20Host%20Header%20Attacks/assets/header%20attack%2029.JPG)