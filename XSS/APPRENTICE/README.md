# Cross-site scripting (XSS)

Judul lab:
1. [Reflected XSS into HTML context with nothing encoded](#reflected-xss-into-html-context-with-nothing-encoded)
2. [Stored XSS into HTML context with nothing encoded](#stored-xss-into-html-context-with-nothing-encoded)
3. [DOM XSS in innerHTML sink using source location.search](#dom-xss-in-innerhtml-sink-using-source-locationsearch)
4. [DOM XSS in innerHTML sink using source location.search](#dom-xss-in-innerhtml-sink-using-source-locationsearch-1)
5. [DOM XSS in jQuery anchor href attribute sink using location.search source](#dom-xss-in-jquery-anchor-href-attribute-sink-using-locationsearch-source)
6. [DOM XSS in jQuery selector sink using a hashchange event](#dom-xss-in-jquery-selector-sink-using-a-hashchange-event)
7. [Reflected XSS into attribute with angle brackets HTML-encoded](#reflected-xss-into-attribute-with-angle-brackets-html-encoded)
8. [Stored XSS into anchor href attribute with double quotes HTML-encoded](#stored-xss-into-anchor-href-attribute-with-double-quotes-html-encoded)
9. [Reflected XSS into a JavaScript string with angle brackets HTML encoded](#reflected-xss-into-a-javascript-string-with-angle-brackets-html-encoded)


## Reflected XSS into HTML context with nothing encoded
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%201.JPG)

- Masukkan payload berikut pada field pencarian lalu tekan tombol **Search**
```sh
<script>alert(1)</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%202.JPG)

- Muncul pop up yang menjadi penanda kerentanan XSS

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%203.JPG)

- Selain payload diatas kita juga bisa menggunakan payload lain seperti dibawah ini
```sh
<img src=x onerror="alert(1)">
```
- [Kembali ke judul](#cross-site-scripting-xss)

## Stored XSS into HTML context with nothing encoded
- Celah keamanan XSS berada di fitur komentar. Pilih salah satu postingan lalu tekan tombol **View post**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%204.JPG)

- Scroll kebawah, lalu masukkan payload XSS pada field **Comment** kemudian lengkapi data pada field lainnya seperti berikut ini, Jika sudah tekan tombol **Post Comment**
```sh
<script>alert(1)</script>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%205.JPG)

- Lalu klik link **Back to blog**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%206.JPG)

- Muncul pop up yang menjadi penanda kerentanan XSS

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%207.JPG)

- [Kembali ke judul](#cross-site-scripting-xss)

## DOM XSS in innerHTML sink using source location.search
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%208.JPG)

- Ketik 'test' pada field pencarian lalu tekan tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%209.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2010.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2011.jpg)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2012.JPG)

- Masukkan payload berikut ini pada filed pencarian, untuk memunculkan popup alert
```sh
"><svg onload=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2013.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2014.JPG)

- Selain payload diatas anda juga bisa menggunakan payload sebagai berikut
```sh
"><img src/onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2015.JPG)

- Payload diatas akan membentuk nilai sebagai berikut, sehingga menyebabkan kerentanan XSS
```sh
document.write('<img src="/resources/images/tracker.gif?searchTerms="><svg onload=alert(1)>">');
```
- [Kembali ke judul](#cross-site-scripting-xss)

## DOM XSS in innerHTML sink using source location.search
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2016.JPG)

- Ketik 'test' pada field pencarian lalu tekan tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2017.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2018.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2019.JPG)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2020.JPG)

- Masukkan payload berikut ini pada filed pencarian, untuk memunculkan popup alert
```sh
<img src=1 onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2021.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2022.JPG)

- Selain payload diatas anda juga bisa menggunakan payload sebagai berikut
```sh
<iframe src="javascript:alert('xss')">
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2023.JPG)

- Payload diatas akan menambahkan HTML pada element `span` seperti berikut
```sh
<span id="searchMessage"><img src="1" onerror="alert(1)"></span>
```
- [Kembali ke judul](#cross-site-scripting-xss)

## DOM XSS in jQuery anchor href attribute sink using location.search source
- Celah keamanan berada di halaman **Feedback**. Tekan tombol **View Post**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2024.JPG)

- Klik link **Submit feedback**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2025.JPG)

- Pada URL akan tampak parameter **returnPath**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2026.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2027.jpg)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2028.JPG)

- Masukkan payload berikut ini pada nilai parameter **returnPath** kemudian tekan enter
```sh
javascript:alert(document.cookie)
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2029.JPG)

- Jika kita melakukan inspeksi pada Back link akan tampak HTML sebagai berikut
```sh
<a id="backLink" href="javascript:alert(document.cookie)">Back</a>
```
- Jika kita klik link tersebut akan muncul popup

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2030.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2031.JPG)

- [Kembali ke judul](#cross-site-scripting-xss)

## DOM XSS in jQuery selector sink using a hashchange event
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2032.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2033.JPG)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2034.JPG)

- Untuk men trigger event `hashchange` kita bisa menambahkan path `/#judul artikel` seperti ini pada URL kemudian tekan enter

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2035.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2036.JPG)

- Halaman akan secara otomatis men scroll ke judul yang dituju

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2037.JPG)

- Untuk mengecek kerentanan XSS, kita bisa menambahkan payload sebagai berikut pada URL
```sh
/#<img src=x onerror=prompt(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2038.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2039.JPG)

- Buka Exploit Server

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2040.JPG)

- Pada bagian Body masukkan payload sebagai berikut kemudian klik tombol **Store**
```sh
<iframe src="https://lab_id.web-security-academy.net/#abc" onload="this.src=this.src+'<img src=x onerror=print()>'"></iframe>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2041.JPG)

- Klik tombol **View exploit** untuk melihat hasil

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2042.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2043.JPG)

- Klik tombol **Batal** kemudian **Back** untuk kembali ke halaman Exploit server

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2044.JPG)

- Klik tombol **Deliver exploit to victim** untuk menyelesaikan lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2045.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2046.JPG)

- Payload diatas akan mentrigger event `hashchange` kemudian mengeksekusi payload XSS
- [Kembali ke judul](#cross-site-scripting-xss)

## Reflected XSS into attribute with angle brackets HTML-encoded
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2047.JPG)

- Ketik `test` pada field pencarian lalu klik tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2048.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2049.JPG)

- Klik kanan field **pencarian** lalu pilih **Inspeksi**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2050.JPG)

- HTML input yang tampak seperti berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2051.JPG)

- Untuk mendapatkan kerentanan XSS kita bisa menyisipkan attribut melalui inputan string seperti berikut ini
```sh
"onmouseover="alert(1)
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2052.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2053.JPG)

- Anda juga bisa menggunakan payload berikut ini
```sh
"onfocus="alert(1)
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2054.JPG)

- Payload diatas akan membentuk HTML sebagai berikut
```sh
<input type=text placeholder='Search the blog...' name=search value=""onmouseover="alert(1)">
```
- [Kembali ke judul](#cross-site-scripting-xss)

## Stored XSS into anchor href attribute with double quotes HTML-encoded
- Celah kerentanan berda di fitur Post Komentar. Klik tombol **View post**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2055.JPG)

- Scroll kebawah untuk menemukan form untuk menulis komentar

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2056.JPG)

- Isi form seperti berikut ini kemudian klik tombol **Post Comment**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2057.JPG)

- Lalu klik link **Back to blog**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2058.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2059.JPG)

- Hasil inputan field **Website** akan dimasukkan ke dalam seperti berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2060.JPG)

- Isi form dengan memasukkan payload berikut pada field **Website** kemudian klik tombol **Post Comment**
```sh
javascript:alert(1)
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2061.JPG)

- Lalu klik link **Back to blog**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2062.JPG)

- Klik link pada nama user di komentar untuk memunculkan popup

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2063.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2064.JPG)

- Payload diatas akan menghasilkan link sebagai berikut
```sh
<a id="author" href="javascript:alert(1)">Testing</a>
```
- [Kembali ke judul](#cross-site-scripting-xss)

## Reflected XSS into a JavaScript string with angle brackets HTML encoded
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2065.JPG)

- Ketik `test` pada field pencarian lalu klik tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2066.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2067.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2068.jpg)

- Akan ditemukan script javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2069.JPG)

- Masukkan payload berikut pada field pencarian lalu tekan tombol **Search**
```sh
'-alert(1)-'
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2070.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/APPRENTICE/assets/xss%2071.JPG)

- Payload diatas akan menghasilkan nilai variabel sebagai berikut
```sh
var searchTerms = ''-alert(1)-'';
```
- [Kembali ke judul](#cross-site-scripting-xss)