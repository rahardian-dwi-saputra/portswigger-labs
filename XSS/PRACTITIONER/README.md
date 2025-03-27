# Cross-site scripting (XSS)

## DOM XSS in document.write sink using source location.search inside a select element
- Celah keamanan berada di halaman detail produk
- Klik tombol **View details**

- Klik kanan halaman kemudian pilih **Lihat Kode Sumber Halaman**

- Akan ditemukan function javascript sebagai berikut

- Sekarang kita coba tambahkan parameter `storeId` pada URL kemudian tekan enter

- Akan muncul list sebagai berikut

- Masukkan payload berikut pada URL kemudian tekan enter
```sh
&storeId="></select><img%20src=1%20onerror=alert(1)>
```

- Payload diatas akan membentuk nilai sebagai berikut, sehingga menyebabkan kerentanan XSS
```sh
<select name="storeId"><option selected="">storeId="></option></select>
<img src="1" onerror="alert(1)">
```

