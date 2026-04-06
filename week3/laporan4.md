# Laporan4 Praktikum Jarkom IF

# modul 4 DNS

1. Perintah pertama yang dicoba adalah nslookup www.mit.edu. Perintah ini dipakai buat nyari alamat IP dari website www.mit.edu.
    # Lampiran
    nslookup www.mit.edu ![nslookup www.mit.edu](../assets/image/nslookup%20www.mit.edu.png)
Dari hasilnya, server DNS yang dipake adalah tusbind.ac.id dengan IP 10.217.7.77. Jawabannya bersifat non-authoritative, artinya datanya dari cache server DNS lokal, bukan langsung dari server MIT. Alamat IP yang balik ada dua IPv6 dan satu IPv4 yaitu 23.217.163.122, dengan alias www.mit.edu dan www.mit.edu.edgekey.net.
2. Perintah kedua adalah nslookup -type=NS mit.edu. Ini dipakai buat nyari nameserver yang bertanggung jawab atas domain mit.edu.
    # Lampiran
    nslookup -type=NS mit.edu (bagian 1) ![nslookup -type=NS mit.edu (bagian 1)](../assets/image/nslookup%20-type=NS%20mit.edu%20(bagian%201).png)
    nslookup -type=NS mit.edu (bagian 2) ![nslookup -type=NS mit.edu (bagian 2)](../assets/image/nslookup%20-type=NS%20mit.edu%20(bagian%202).png)
Hasilnya menunjukkan ada delapan nameserver untuk mit.edu, semuanya di bawah domain akam.net, yaitu usw2.akam.net, ns1-173.akam.net, eur5.akam.net, use2.akam.net, use5.akam.net, ns1-37.akam.net, asia1.akam.net, dan asia2.akam.net. Selain nama servernya, hasil juga langsung kasih alamat IP masing-masing nameserver tersebut secara otomatis.
3. Perintah ketiga mencoba ngirim permintaan DNS langsung ke server bitsy.mit.edu.
    # Lampiran
    nslookup www.aiit.or.kr bitsy.mit.edu - timeout ![nslookup www.aiit.or.kr bitsy.mit.edu - timeout](../assets/image/nslookup%20www.aiit.or.kr%20bitsy.mit.edu%20-%20timeout.png)
Hasilnya gagal karena DNS request timeout terus sampai 4 kali dengan pesan *** Request to UnKnown timed-out. Ini terjadi karena server bitsy.mit.edu tidak bisa diakses dari jaringan yang dipakai saat praktikum.
4. Perintah ipconfig /all dijalankan buat liat semua informasi konfigurasi jaringan di komputer secara lengkap.
    # Lampiran
    ipconfig /all ![ipconfig /all](../assets/image/ipconfig%20all.png)
Dari hasilnya, hostname komputer adalah DESKTOP-GARLJAI. Ada dua adapter yang aktif, yaitu VirtualBox Host-Only Network dengan IP 192.168.56.1 dan adapter Wi-Fi dengan IP 10.218.9.61, subnet mask 255.255.240.0, dan default gateway 10.218.0.253.
5. Perintah ipconfig /displaydns dipakai buat nampilin isi DNS cache yang tersimpan di komputer.
    # Lampiran
    ipconfig displaydns ![ipconfig displaydns](../assets/image/ipconfig%20displaydns.png)
Dari hasilnya terlihat beberapa domain yang udah pernah diakses tersimpan di cache, contohnya mc.corel.com yang tidak punya record A maupun AAAA, dan tas01.cwsapp.update.microsoft.com yang punya CNAME record dengan TTL 74 detik.
6. Setelah liat isi cache, cache DNS-nya dihapus pakai perintah ipconfig /flushdns.
    # Lampiran
    ipconfig flushdns ![ipconfig flushdns](../assets/image/ipconfig%20flushdns.png)
Muncul pesan Successfully flushed the DNS Resolver Cache yang artinya cache berhasil dikosongkan. Setelah ini, komputer bakal minta resolusi DNS ulang ke server setiap kali akses domain baru.
7. Wireshark dibuka dan dijalankan dengan filter ip.addr == 10.218.9.61 supaya hanya paket yang masuk/keluar dari komputer yang ditampilkan.
    # Lampiran
    Wireshark filter ip.addr ![Wireshark filter ip.addr](../assets/image/Wireshark%20filter%20ip.addr.png)
Di awal capture terlihat banyak paket ARP, lalu diikuti paket TCP dan TLSv1.2 saat koneksi ke server mulai terjadi.
8. Buat lihat paket DNS secara spesifik, filter diubah jadi ip.addr == 10.218.9.61 && dns.qry.name contains "ietf".
    # Lampiran
    Wireshark capture TLSTCP setelah DNS resolved ![Wireshark capture TLSTCP setelah DNS resolved](../assets/image/Wireshark%20capture%20TLSTCP%20setelah%20DNS%20resolved.png)
    Wireshark filter DNS ietf ![Wireshark filter DNS ietf](../assets/image/Wireshark%20filter%20DNS%20ietf.png)
Terlihat beberapa paket DNS query dan response untuk www.ietf.org. Permintaan DNS dikirim dari komputer ke server DNS 10.217.7.77 lewat port 53 pakai protokol UDP. Balasannya mengembalikan IP 104.16.45.99 dan 104.16.44.99 untuk www.ietf.org.
9. Filter diubah jadi ip.addr == 10.218.9.61 && dns.qry.name contains "mit" buat nangkep paket DNS waktu nslookup mit.edu dijalankan.
    # Lampiran
    Wireshark filter DNS mit - capture ![Wireshark filter DNS mit - capture](../assets/image/Wireshark%20filter%20DNS%20mit%20-%20capture.png)
    nslookup mit.edu hasil di CMD ![nslookup mit.edu hasil di CMD](../assets/image/nslookup%20mit.edu%20hasil%20di%20CMD.png)
Terlihat empat paket: dua query (record A dan AAAA) dan dua response. Balasan untuk query A ngasih IP 173.222.144.77, dan balasan AAAA ngasih dua alamat IPv6. Hasilnya sama persis dengan yang ditampilkan di Command Prompt waktu nslookup mit.edu dijalankan.
10. Untuk query NS record mit.edu, hasilnya menunjukkan delapan nameserver di bawah domain akam.net. Server DNS yang menjawab tetap tusbind.ac.id dengan IP 10.217.7.77. Jawaban bersifat non-authoritative karena datanya dari cache server DNS lokal, bukan langsung dari nameserver MIT.
    # Lampiran
    Wireshark filter DNS mit - capture ![Wireshark filter DNS mit - capture](../assets/image/Wireshark%20filter%20DNS%20mit%20-%20capture.png)
    nslookup -type=NS mit.edu hasil di CMD ![nslookup -type=NS mit.edu hasil di CMD](../assets/image/nslookup%20-type=NS%20mit.edu%20hasil%20di%20CMD.png)

Pertanyaan 4.2 nslookup
1. Jalankan nslookup untuk mendapatkan alamat IP dari server web di Asia. Berapa alamat IP 
server tersebut?
    # Lampiran
    nslookup www.nus.edu.sg ![nslookup www.nus.edu.sg](../assets/image/nslookup%20www.nus.edu.sg.png)
    Alamat IP dari server web www.nus.edu.sg adalah 45.60.35.225 (hasilnya bisa berbeda tergantung waktu dan jaringan yang digunakan).

2. Jalankan nslookup agar dapat mengetahui server DNS otoritatif untuk universitas di Eropa.
    # Lampiran
    nslookup -type=NS ox.ac.uk ![nslookup -type=NS ox.ac.uk](../assets/image/nslookup%20-type=NS%20ox.ac.uk.png)
    Server DNS otoritatif untuk University of Oxford antara lain dns0.ox.ac.uk, dns1.ox.ac.uk, dan dns2.ox.ac.uk.

3. Jalankan nslookup untuk mencari tahu informasi mengenai server email dari Yahoo! Mail 
melalui salah satu server yang didapatkan di pertanyaan nomor 2. Apa alamat IP-nya?
    # Lampiran
    nslookup -type=MX yahoo.com dns0.ox.ac.uk ![nslookup -type=MX yahoo.com dns0.ox.ac.uk](../assets/image/nslookup%20-type=MX%20yahoo.com%20dns0.ox.ac.uk.png)
    Alamat IP server email Yahoo! Mail salah satunya adalah 129.67.1.190

Pertanyaan 4.4 Tracing DNS dengan Wireshark
1. Cari pesan permintaan DNS dan balasannya. Apakah pesan tersebut dikirimkan melalui UDP 
atau TCP?
    # Lampiran
    nomor 1 modul 4 (4.4) ![nomor 1 modul 4 (4.4)](../assets/image/nomor%201%20modul%204%20(4.4).png)

2. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasannya? 
    # Lampiran
    nomor 2 modul 4 (4.4) ![nomor 2 modul 4 (4.4)](../assets/image/nomor%202%20modul%204%20(4.4).png)

3. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasan DNS? 
    # Lampiran
    nomor 3 modul 4 (4.4) ![nomor 3 modul 4 (4.4)](../assets/image/nomor%203%20modul%204%20(4.4).png)

