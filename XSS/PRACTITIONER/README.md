# Cross-site scripting (XSS)

## DOM XSS in document.write sink using source location.search inside a select element
- Celah keamanan berada di halaman detail produk
- Klik tombol **View details**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%201.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%202.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%203.jpg)

- Akan ditemukan function javascript sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%204.JPG)

- Sekarang kita coba tambahkan parameter `storeId` pada URL kemudian tekan enter

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%205.JPG)

- Akan muncul list sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%206.jpg)

- Masukkan payload berikut pada URL kemudian tekan enter
```sh
&storeId="></select><img%20src=1%20onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%207.JPG)

- Selain payload diatas, anda juga bisa menggunakan payload dibawah ini
```sh
&storeId=</option></select><img%20src=1%20onerror=alert(1)>
```
- Payload diatas akan membentuk nilai sebagai berikut, sehingga menyebabkan kerentanan XSS
```sh
<select name="storeId"><option selected="">storeId="></option></select>
<img src="1" onerror="alert(1)">
```

## DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%208.JPG)

- Ketik 'test' pada field pencarian lalu tekan tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%209.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2010.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2011.jpg)

- Terdapat informasi bahwa halaman menggunakan AngularJS versi 1.7.7 dan hasil pencarian terdapat dalam elemen body dengan atribut `ng-app` yang merupakan direktif AngularJs. Dengan direktif AngularJs kita bisa menjalankan javascript dalam kurung kurawal ganda

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2012.JPG)

- Jika kita klik link src nya akan tampil library angular js versi 1.7.7

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2013.JPG)

- Untuk memastikan bahwa kita berada di elemen ng-app Directive kita bisa memasukkan string sebagai berikut
```sh
{{2 + 3}}
```
![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2014.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2015.JPG)

- Sekarang kita masukkan payload XSS menggunakan object default pada angularJS
```sh
{{$eval.constructor('alert(1)')()}}
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2016.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2017.JPG)

- Selain payload diatas anda juga bisa menggunakan payload berikut ini
```sh
{{$on.constructor('alert(1)')()}}
{{$watch.constructor('alert(1)')()}}
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2018.JPG)

- Fungsi `$on.constructor('alert(1)')()` mirip dengan javascript sebagai berikut
```sh
function (){
   alert(1);
}
```

## Reflected DOM XSS
- Celah keamanan XSS berada di fitur pencarian (Search)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2019.JPG)

- Jalankan tool Burp Suite dengan Intercept off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2020.JPG)

- Ketik 'test' pada field pencarian lalu tekan tombol **Search**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2021.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2022.JPG)

- Pada Burp Suite terdapat request yang mengarah ke path `/search-results`. Klik kanan request tersebut dan pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2023.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2024.jpg)

- Buka halaman web, klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2025.jpg)

- Terdapat lampiran source code `searchResults.js`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2026.JPG)

- Jika dibuka, disana terdapat fungsi `eval()`. Fungsi `eval()` ini akan mengeksekusi ekspresi javascript apapun yang tertulis di dalamnya termasuk fungsi `alert()`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2027.JPG)

- Kembali ke Burp Suite, pindah ke tab **Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2028.JPG)

- Ubah nilai parameter `search` menjadi seperti ini. Jika sudah tekan tombol **Send**
```sh
xss\"-alert(1)}//
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2029.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2030.JPG)

- Tanda `\"` digunakan untuk menambahkan tanda kutip 2 pada string `xss` sehingga fungsi `alert()` berada di luar string. Tanda `}` digunakan untuk menutup hasil encode JSON. Kemudian tanda `//` digunakan untuk mengomentari tanda `"}` yang tersisa dibagian akhir. Untuk lebih jelaskan bisa amati perubahan berikut ini

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2031.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2032.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2033.JPG)

- Sekarang masukkan payload diatas pada field **Search**
```sh
xss\"-alert(1)}//
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2034.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2035.JPG)

## Stored DOM XSS
- Celah keamanan XSS berada di fitur komentar. Pilih salah satu postingan lalu tekan tombol **View post**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2036.JPG)

- Scroll kebawah untuk menemukan form untuk menulis komentar. Kemudian lakukan pengujian dengan menulis komentar seperti ini lalu klik tombol **Post Comment**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2037.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2038.JPG)

- Hasil komentar akan tampak seperti ini. Terlihat bahwa karakter `<>` dihilangkan

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2039.JPG)

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2040.jpg)

- Terdapat lampiran source code `loadCommentsWithVulnerableEscapeHtml.js`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2041.JPG)

- Di dalam source code `loadCommentsWithVulnerableEscapeHtml.js` terdapat fungsi `escapeHTML(html)`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2042.JPG)

- Untuk mengeksploitasi kerentanan XSS kita memasukkan payload berikut ini ke dalam komentar
```sh
<><img src=x onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2043.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2044.JPG)

- Hasilnya adalah sebagai berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2045.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2046.JPG)

## Reflected XSS into HTML context with most tags and attributes blocked
- Lab ini mengandung web application firewall (WAF) untuk memproteksi serangan XSS. Sebelum melakukan pengujian jalankan tool Burp Suite dengan Intercept off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2047.JPG)

- Masukkan payload berikut ini pada field **Search**
```sh
<img src=1 onerror=print()>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2048.JPG)

- Akan muncul respon bahwa tag tersebut tidak diizinkan

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2049.JPG)

- Pada Burp Suite akan terekam request ke path `/search`. Klik kanan request tersebut lalu pilih **Send to Intruder**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2050.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2051.jpg)

- Pindah ke tab Intruder

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2052.JPG)

- Ubah value parameter search menjadi `<>` tambahkan tanda payload tepat diantara tanda `<` dan `>`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2053.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2054.JPG)

- Buka link halaman https://portswigger.net/web-security/cross-site-scripting/cheat-sheet lalu copy semua tag

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2055.JPG)

- Paste payload di Burp Suite kemudian klik tombol **Start attack**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2056.JPG)

- Tunggu hingga proses selesai, urutkan hasil berdasarkan **Status code**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2057.JPG)

- Disini terlihat jika WAF mengizinkan tag `body`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2058.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2059.JPG)

- Sekarang kita coba masukkan payload berikut ini pada field **Search**
```sh
<body onload="alert(1)">
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2060.JPG)

- Muncul pesan bahwa atribut tidak diizinkan

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2061.JPG)

- Kembali ke Burp Suite, ubah value parameter `search` menjadi seperti berikut

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2062.JPG)

- Pada halaman https://portswigger.net/web-security/cross-site-scripting/cheat-sheet klik tombol **Copy events to clipboard**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2063.JPG)

- Klik tombol **Clear** untuk membersihkan daftar payload sebelumnya lalu tekan tombol **Paste** untuk menempel payload yang baru. Jika sudah, klik tombol **Start attack**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2064.JPG)

- Tunggu hingga proses selesai, urutkan hasil berdasarkan **Status code**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2065.JPG)

- Disini kita bisa menggunakan atribut `onresize` untuk menjalankan function javascript

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2066.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%2067.JPG)