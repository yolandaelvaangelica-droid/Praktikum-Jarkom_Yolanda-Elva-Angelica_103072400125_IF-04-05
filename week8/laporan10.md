# Laporan10 Praktikum Jarkom IF

# modul 10 IP

1. apa itu ip address?
IP Address (Internet Protocol Address) adalah alamat unik yang diberikan kepada setiap perangkat yang terhubung ke jaringan komputer. IP Address berfungsi sebagai identitas perangkat di jaringan, seperti halnya alamat rumah yang digunakan untuk mengirim surat.
    Ada dua versi IP Address:

    a. IPv4:

    - Panjang 32 bit

    - Format desimal dipisah titik, contoh: 192.168.100.133

    - Maksimal sekitar 4 miliar alamat

    - Sudah hampir habis
    
    b. IPv6:

    - Panjang 128 bit
    
    - Format heksadesimal dipisah titik dua, contoh: 2001:db8:1::10
    
    - Jumlah alamat sangat besar, tidak akan habis dalam waktu dekat

2. Traceroute via CMD
    Tutorial:
    
    a. Buka Command Prompt (tekan Windows + R → ketik cmd → Enter)
    
    b. Ketik perintah berikut: tracert gaia.cs.umass.edu

    c. Tunggu sampai selesai

    ![Traceroute Modul 10](../assets/image/Traceroute%20Modul%2010.png)

    Analisis di Wireshark:

    a. Buka Wireshark → buka file abc.pcapng
    
    b. Ketik filter icmp
    
    c. Akan muncul paket Echo Request dan TTL Exceeded

    Paket Echo Request (paket 25):
    ![Paket Echo Request (paket 25) modul 10](../assets/image/Paket%20Echo%20Request%20(paket%2025)%20modul%2010.png)

    Paket TTL Exceeded (paket 26):
    ![Paket TTL Exceeded (paket 26) Modul 10](../assets/image/Paket%20TTL%20Exceeded%20(paket%2026)%20Modul%2010.png)

3. Apa itu ICMP, MTU, TTL?
ICMP (Internet Control Message Protocol)

ICMP adalah protokol yang digunakan untuk mengirim pesan error dan informasi kontrol dalam jaringan IP. ICMP tidak digunakan untuk mengirim data seperti TCP/UDP, melainkan untuk melaporkan kondisi jaringan.

    Contoh penggunaan ICMP:
    
    - Ping → mengirim ICMP Echo Request, menerima Echo Reply
    
    - Traceroute → memanfaatkan pesan ICMP TTL Exceeded
    
    - Destination Unreachable → memberitahu pengirim bahwa tujuan tidak bisa dicapai

    Type ICMP yang umum:

    - 0 : Echo Reply

    - 8 : Echo Request

    - 11 : Time-to-live Exceeded

    - 3 : Destination Unreachable

MTU (Maximum Transmission Unit)

MTU adalah ukuran maksimum paket data yang bisa dikirim dalam satu frame di jaringan. Untuk jaringan Ethernet standar, MTU adalah 1500 bytes. Jika paket lebih besar dari MTU, maka paket akan dipecah menjadi beberapa bagian kecil yang disebut fragmentasi.

    Contoh:

    Paket 3000 byte, MTU 1500 byte:
    
    - Fragment 1: 1480 bytes (MF=1, offset=0)
    
    - Fragment 2: 1480 bytes (MF=1, offset=185)
    
    - Fragment 3: 40 bytes   (MF=0, offset=370)

TTL (Time to Live)

TTL adalah nilai dalam header IP yang menentukan berapa banyak router yang boleh dilalui oleh sebuah paket sebelum dibuang. Setiap kali paket melewati satu router, nilai TTL dikurangi 1. Jika TTL mencapai 0, router akan membuang paket dan mengirim pesan ICMP TTL Exceeded ke pengirim.

    Fungsi TTL:
    
    - Mencegah paket berputar-putar selamanya di jaringan
    
    - Dimanfaatkan oleh traceroute untuk mengetahui jalur paket

    Contoh:
    
    - TTL=1 → dibuang di router hop 1
    
    - TTL=2 → dibuang di router hop 2
    
    - TTL=3 → dibuang di router hop 3

4. Contoh Fragmentasi di Wireshark

    Langkah:
    
    a. Buka Wireshark → buka file abc.pcapng
    
    b. Ketik filter: ip.flags.mf == 1 || ip.frag_offset > 0
    
    ![abc.pcapng modul 10](../assets/image/abc.pcapng%20modul%2010.png)

    Hasil:

    Pada file abc.pcapng tidak ditemukan fragmentasi karena traceroute Windows menggunakan paket ICMP berukuran kecil (32 bytes) yang tidak melebihi MTU 1500 bytes sehingga tidak memerlukan fragmentasi.
    Penjelasan teori fragmentasi:
    
    Fragmentasi terjadi ketika ukuran paket melebihi MTU jaringan. Tanda-tanda fragmentasi di Wireshark:
    
    - More Fragments (MF) flag = 1 → masih ada fragment lanjutan
    
    - Fragment Offset > 0 → ini bukan fragment pertama
    
    - Identification sama → semua fragment berasal dari paket yang sama

5. IPv6 di Wireshark

    Langkah:
    
    a. Buka Wireshark → File → Open → pilih ipv6_sample.pcap
    
    b. Ketik filter ipv6
    ![Wireshark IPv6 modul 10](../assets/image/Wireshark%20IPv6%20modul%2010.png)

    Info Umum:
    
    - Total paket: 35 paket (semua IPv6)
    
    - Source: 2001:db8:1::10
    
    - Destination: 2a00:1450:4009:80b::200e (Google)
    
    - Protocol: TCP/SSL
    
    - Port: 52344 → 443 (HTTPS)

    Perbedaan IPv6 vs IPv4:

    a. Fitur: Panjang alamat, IPv4: 32 bit, IPv6: 128 bit

    b. Fitur: Format, IPv4: 192.168.1.1, IPv6: 2001:db8:1::10

    c. Fitur: TTL, IPv4: Time To Live, IPv6: Hop Limit

    d. Fitur: Header size, IPv4: Variable, IPv6: Fixed 40 bytes

    e. Fitur: Checksum, IPv4: Ada, IPv6: Tidak ada

    d. Fitur: Jumlah alamat, IPv4: ~4 milliar, IPv6: ~340 undecillion

Kesimpulan:
IPv6 dikembangkan sebagai pengganti IPv4 karena keterbatasan jumlah alamat. Dengan format 128 bit, IPv6 mampu menyediakan alamat yang jauh lebih banyak sehingga cukup untuk seluruh perangkat di dunia dalam jangka panjang.