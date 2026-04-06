# Laporan4 Praktikum Jarkom IF

# modul 4 DNS

4.2 Nslookup
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