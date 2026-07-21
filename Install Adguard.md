1. Buka Terminal atau masuk via SSH ke perangkat ubuntu server.
2. Unduh dan jalankan skrip instalasi otomatis resmi dari AdGuard Home dengan mengeksekusi perintah ini:

        curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
4. Tunggu beberapa detik. Skrip tersebut akan otomatis mengunduh file binary Golang AdGuard, mengekstraknya, dan menjalankannya sebagai service di latar belakang.
5. Ubuntu Server biasanya mengaktifkan layanan bernama systemd-resolved yang menggunakan Port 53 (port untuk DNS). Karena AdGuard Home juga membutuhkan Port 53, kita harus mematikan DNS bawaan Ubuntu tersebut agar tidak bentrok.
6. Jalankan perintah-perintah berikut di terminal Ubuntu Server kamu secara berurutan:

        sudo systemctl stop systemd-resolved
   Menghentikan layanan systemd-resolved yang sedang berjalan detik ini juga (secara real-time).
   Port 53 yang tadinya "dikunci" atau dipakai oleh sistem bawaan Ubuntu akan langsung terlepas dan    menjadi bebas. Dengan begitu, AdGuard Home bisa langsung mengambil alih port tersebut tanpa         tertahan error port already in use.
   
        sudo systemctl disable systemd-resolved
   Menonaktifkan layanan systemd-resolved agar tidak berjalan otomatis saat server dinyalakan ulang    (reboot/restart).
   Mencegah masalah bentrok terjadi lagi di masa depan. Tanpa perintah ini, setiap kali server         Ubuntu kamu mati atau di-restart, layanan bawaan tersebut akan otomatis menyala kembali dan         membajak Port 53 dari AdGuard Home.
8. Ganti konfigurasi DNS internal Ubuntu agar menggunakan DNS publik sementara (misal Cloudflare), supaya servermu tetap bisa mendownload file Docker nanti:
   
        sudo rm /etc/resolv.conf
        echo "nameserver 1.1.1.1" | sudo tee /etc/resolv.conf
9. Buat folder di Ubuntu Server untuk menyimpan konfigurasi dan data filter AdGuard Home. Tujuannya agar saat kontainer Docker diperbarui atau di-restart, pengaturan AdGuard kamu tidak hilang.

   Buat folder tersebut dengan perintah ini:

        mkdir -p ~/adguardhome/work ~/adguardhome/conf
10. Jalankan perintah Docker di bawah ini untuk mengunduh dan mengaktifkan AdGuard Home:

        docker run -d \
          --name adguardhome \
          --restart unless-stopped \
          -v "$HOME/adguardhome/work:/opt/adguardhome/work" \
          -v "$HOME/adguardhome/conf:/opt/adguardhome/conf" \
          -p 53:53/tcp -p 53:53/udp \
          -p 80:80/tcp -p 443:443/tcp -p 443:443/udp \
          -p 3030:3030/tcp \
          adguard/adguardhome
   
        keterangan:
        -p 53:53: Membuka jalur DNS untuk perangkat di jaringanmu.
        
        -p 3030:3000: Membuka port khusus untuk instalasi awal lewat web browser.
        
        -v ...: Menyambungkan folder yang kita buat tadi ke dalam Docker.
11. Buka Halaman Instalasi, setelah perintah di atas sukses berjalan, silakan buka laptop atau HP yang berada di jaringan yang sama dengan Ubuntu Server tersebut, lalu buka browser dan ketik:

        http://192.168.115.2:3030
12. Jika sudah berhasil dibuka, akan muncul halaman untuk masuk ke Adguard.
13. klik tombol hijau "Mari mulai"
14. Antarmuka Web (Web Interface): Pilih Semua antarmuka (All interfaces) dan biarkan port-nya tetap di angka 80.
15. Server DNS: Pilih Semua antarmuka dan pastikan port-nya di angka 53.
16. Klik Lanjut.
17. Buat Username dan Password yang aman.
18. Klik Lanjut.
19. Setelah itu akan muncul halaman yang menampilkan panduan cara mengarahkan DNS di berbagai perangkat. Karena nantinya kita akan mengarahkan DNS ini secara terpusat, bisa sekadar membacanya lalu klik Lanjut.
20. Selesai, Klik tombol Buka Dasbor (Open Dashboard).

Noted: Setelah semua proses di atas selesai, fungsi port 3030 sudah tidak dipakai lagi. Untuk login harian ke depannya, cukup mengetikkan (http://192.168.115.2) (tanpa port) di browser.
