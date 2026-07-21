Untuk menyeting DNS laptop agar bisa terkoneksi dengan Adguard yaitu memasukkan IP ubuntu server ke preferrend DNS server.

Berikut langkah - langkah menyeting DNS laptop
1. Buka Control Panel > Network and Internet > Network and Sharing Center
2. Jika menggunakan wifi klik wifi yang terkoneksi dengan laptop
3. Uncek pada menu  Internet Protocol Version 6 (TCP/IPv6)
4. Kemudian pilih properties > ceklis pada Internet Protocol Version 4 (TCP/IPv4)
5. Klik dua kali pada Internet Protocol Version 4 (TCP/IPv4)
6. Pada bagian preferrend DNS server isi dengan IP ubuntu anda. (contoh: 192.168.115.2) > ok
7. Matikan secure DNS di browser:

        Buka chrome://settings/security di bilah alamat browser.
        Gulir ke bawah dan cari Gunakan DNS aman (Use secure DNS).
        Nonaktifkan "Use secure DNS"
8. Setelah menonaktifkan fitur tersebut, Bersihkan cache DNS di laptop Anda dengan membuka Command Prompt (CMD) dan mengetik perintah:

        ipconfig /flushdns > enter
9. Buka kembali Adguard dengan mengetikkan IP ubuntu (conroh: http://192.168.115.2 > enter)
10. Akan muncul angka pada kueri DNS. Itu artinya laptop sudah terhubung ke Adguard.
