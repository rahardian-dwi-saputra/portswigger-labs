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

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%206.JPG)

- Masukkan payload berikut pada URL kemudian tekan enter
```sh
&storeId="></select><img%20src=1%20onerror=alert(1)>
```

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/XSS/PRACTITIONER/assets/xss%207.JPG)

- Payload diatas akan membentuk nilai sebagai berikut, sehingga menyebabkan kerentanan XSS
```sh
<select name="storeId"><option selected="">storeId="></option></select>
<img src="1" onerror="alert(1)">
```