# HTTP Host header attacks

## Basic password reset poisoning
- Vulnerability berada di fitur "Forgot Password". Klik link **My account**

- Klik link **Forgot Password?**

- Buka tool Burp Suite dengan kondisi Intercept On

- Masukkan username `wiener` dan klik tombol **Submit**


- Setelah Burp Suite terbuka, klik kanan request dan pilih **Send to Repeater**

- Selanjutnya tekan tombol **Forward** lalu matikan Intercept 


- Buka exploit server di tab baru

- Pindah ke tab Exploit Server, scroll kebawah dan klik tombol **Email Client** untuk mengakses email

- Buka Burp Suite dan pindah ke tab Repeater

- Ubah nilai Host dengan nilai lain misalnya `abc123` kemudian klik Tombol **Send**

- Reload halaman **Email Client** di browser, maka akan didapat email dengan link seperti berikut ini
