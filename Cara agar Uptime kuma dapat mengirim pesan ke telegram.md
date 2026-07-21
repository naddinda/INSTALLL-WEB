Langkah 1: Buat Bot Telegram
1. Buka aplikasi Telegram Anda, lalu cari akun bernama @BotFather (pastikan ada centang birunya).
2. Klik Start, lalu ketik perintah:  /newbot
3. Masukkan Nama Bot bebas (contoh: Alarm Kuma Saya).
4. Masukkan Username Bot yang diakhiri kata bot (contoh:kaduskragon_kuma_bot).
5. @BotFather akan mengirimkan pesan berisi HTTP API Token. Berbentuk deretan angka dan huruf seperti ini:

        8864985665:AAEwCkE1hCAlhIk8G..... (Salin/Copy tokennya).
6. Klik link username bot Anda yang baru dibuat tadi, lalu klik Start / Mulai agar bot tersebut bisa mengirim pesan ke telegram.

Langkah 2: Dapatkan Chat ID Anda
1. Cari akun bernama @userinfobot di kolom pencarian Telegram.
2. Klik Start.
3. Bot tersebut akan langsung membalas dengan info profil Anda. Salin angka yang tertera di samping tulisan Id: (contoh: 6606438494).

Langkah 3: Setel di Uptime Kuma
Sekarang buka dashboard Uptime Kuma, masuk ke Pengaturan > Notifikasi > Setel Notifikasi, lalu isi seperti ini:

        Tipe Notifikasi: Pilih Telegram
        
        Nama yang Ramah: Telegram Bot
        
        Bot Token: Tempel token dari BotFather tadi
        
        Chat ID: Tempel angka ID dari userinfobot tadi

Langkah 4: Uji Coba
1. Klik tombol Uji Coba (Test) di paling bawah.
2. Bot Telegram Anda akan langsung berbunyi dan memunculkan pesan uji coba
3. Klik Simpan.

Langkah 5: Jika modem down, bisa otomatis mengirim pesan pemberitahuan
1. Kembali ke halaman uptime kuma
2. Pilih salah satu modem
3. Klik Ubah / edit
4. Cari menu notifikasi, lalu aktifkan Telegram bot yang sudah dibuat tadi.

Langkah 6: Cek apakah telegram dapat mengirim pesan saat ada modem yang down
1. Pada halaman uptime kuma, pilih salah satu modem
2. klik ubah / edit
3. Pada host name ganti dengan alamat palsu. (contoh: modem-ini-pasti-mati-total.com)
4. Klik simpan
5. Tunggu sekitar 3 menit (karena ada jeda Coba Lagi sebanyak 3 kali).
6. Setelah 3 menit, Begitu lingkaran indikatornya berubah warna dari Hijau > Kuning > Merah tua, telegram akan mengirimkan pesan otomatis seperti ini:

                [mgabdulsalam] [🔴 Down] ping: modem-ini-pasti-mati-total.com: Name or service not known
7. Jika sudah berhasil, ubah host name menjadi IP modem yang semula.
8. Setelah indikator berwarna hijau, bot telegram mengirimkan pesan seperti ini:

           [mgabdulsalam] [✅ Up]

