1. Buat Direktori Kerja Uptime Kuma

   Masuk ke Ubuntu Server Anda via SSH, lalu buat folder khusus agar seluruh data Uptime Kuma terisolasi dengan rapi:

        mkdir -p ~/uptime-kuma
        cd ~/uptime-kuma
2. Buat File docker-compose.yml

   Buat file konfigurasi menggunakan editor teks nano:

        nano docker-compose.yml
isi: 
        
        version: '3.8'
        
        services:
          uptime-kuma:
            image: louislam/uptime-kuma:1
            container_name: uptime-kuma
            restart: always
            ports:
              - '3001:3001'  # Port luar 3001 dipetakan ke port dalam 3001 (Aman dari port 3000 GenieACS)
            volumes:
              - ./data:/app/data
            security_opt:
              - no-new-privileges:true

3. Jalankan Container Uptime Kuma

   Jalankan perintah berikut untuk mengunduh image resmi Uptime Kuma dan menjalankannya di latar belakang (detached mode):

        docker compose up -d > enter

   Proses ini akan mengunduh data sekitar 100-200 MB. Setelah selesai, pastikan status container-nya sudah berjalan lancar dengan perintah:

        docker ps > enter

4. Akses Dashboard Uptime Kuma

   Buka browser di laptop atau HP Anda yang berada di jaringan yang sama, lalu akses alamat berikut:

        http://192.168.115.2:3001 > enter
