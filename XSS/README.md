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