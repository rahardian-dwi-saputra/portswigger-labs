# Access control vulnerabilities
Judul lab:
- [URL-based access control can be circumvented](#url-based-access-control-can-be-circumvented)


## URL-based access control can be circumvented
- Akses lab

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%201.JPG)

- Buka tool Burp Suite dengan kondisi Intercept Off

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%202.JPG)

- Akses halaman **Admin panel**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%203.JPG)

- Saat diakses muncul pesan `Access denied`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%204.JPG)

- Pada Burp Suite terdeteksi request yang mengarah ke path `/admin`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%205.JPG)

- Klik kanan request tersebut kemudian pilih **Send to Repeater**

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%206.JPG)

- Pindah ke tab Repeater

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%207.JPG)

- Ubah path dari `/admin` menjadi `/` kemudian tambahkan header `X-Original-URL: /invalid`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%208.JPG)

- Jika sudah klik tombol **Send**. Pada response terdapat keterangan `Not found` yang menandakan backend telah memproses URL `/invalid` namun halaman tidak ditemukan sehingga memunculkan pesan `Not found`. `X-Original-URL` adalah  jenis header HTTP yang digunakan untuk menyampaikan informasi tentang URL aslinya saat terjadi redirect. Saat terjadi redirect ke URL yang baru `X-Original-URL` akan mencatat URL sebelumnya sebelum terjadi proses redirect

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%209.JPG)

- Sekarang kita ubah nilai header `X-Original-URL` dari `/invalid` menjadi `/admin`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2010.JPG)

- Jika sudah klik tombol **Send**. Pada response kita berhasil mengakses halaman admin. Terlihat path `/admin/delete?username=carlos` untuk menghapus user carlos

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2011.JPG)

- Tambahkan query `?username=carlos` kemudian ubah nilai header `X-Original-URL` dari `/admin` menjadi `/admin/delete`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2012.JPG)

- Jika sudah klik tombol **Send**. Pada response terdapat HTTP Code 302 yang artinya redirect. Klik tombol **Follow redirection** untuk mengikuti redirect

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2013.JPG)

- Redirect mengarah ke halaman `/admin` dengan response `Access denied`

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2014.JPG)

- Reload halaman `/` maka akan tampil pesan lab berhasil terselesaikan

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2015.JPG)

![alt text](https://github.com/rahardian-dwi-saputra/portswigger-labs/blob/main/Access%20Control%20Vulnerabilities/PRACTITIONER/assets/access%20control%2016.JPG)