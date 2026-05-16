# Laporan11 Praktikum Jarkom IF

# modul 11 DCHP

1. Apa itu DHCP?

    DHCP (Dynamic Host Configuration Protocol) adalah protokol jaringan yang digunakan untuk memberikan konfigurasi jaringan secara otomatis kepada perangkat yang terhubung ke jaringan, seperti alamat IP, subnet mask, default gateway, dan DNS server.

    Tanpa DHCP, setiap perangkat harus dikonfigurasi secara manual (static IP), yang tentu sangat tidak efisien terutama di jaringan besar. Dengan DHCP, perangkat cukup "meminta" konfigurasi ke server dan server akan memberikannya secara otomatis.

    DHCP bekerja menggunakan protokol UDP dengan:

    - Port 67 untuk DHCP Server

    - Port 68 untuk DHCP Client

2. Kelebihan dan Kekurangan DHCP

    Kelebihan:
    
    - Konfigurasi IP otomatis, tidak perlu setting manual satu per satu
    
    - Menghindari konflik IP address karena dikelola terpusat oleh server
    
    - Memudahkan manajemen jaringan besar dengan banyak perangkat
    
    - Hemat waktu dan mengurangi kemungkinan human error
    
    Kekurangan:
    
    - Jika DHCP server mati, perangkat baru tidak bisa mendapat IP otomatis
    
    - Alamat IP bersifat dinamis sehingga bisa berubah-ubah, kurang cocok untuk server
    
    - Rentan terhadap serangan DHCP Spoofing (server palsu)
    
    - Membutuhkan server tambahan dalam jaringan

3. Proses DORA

    DORA adalah singkatan dari empat tahap utama dalam proses DHCP:

    a. Discover
    
    - Client yang baru terhubung belum punya IP, sehingga mengirim broadcast ke seluruh jaringan
    
    - Source IP: 0.0.0.0 → Destination: 255.255.255.255
    
    - Pesan ini berisi Transaction ID untuk mengidentifikasi sesi DHCP

    b. Offer
    
    - DHCP Server menerima Discover dan membalas dengan menawarkan alamat IP
    
    - Server mengirim IP yang tersedia beserta informasi subnet mask, gateway, dan durasi lease
    
    - Source: 192.168.1.1 → Destination: 255.255.255.255
    
    c. Request
    
    - Client menerima Offer dan membalas dengan meminta IP yang ditawarkan secara resmi
    
    - Masih menggunakan broadcast karena client belum resmi memiliki IP
    
    - Source: 0.0.0.0 → Destination: 255.255.255.255

    d. ACK (Acknowledge)
    
    - Server mengkonfirmasi bahwa IP sudah resmi diberikan ke client
    
    - Client sekarang resmi menggunakan IP tersebut
    
    - Source: 192.168.1.1 → Destination: 255.255.255.255

Langkah capture DHCP di Wireshark:

    a. Buka Command Prompt sebagai Administrator
    
    b. Ketik perintah berikut untuk melepas IP lama: ipconfig /release

![ipconfig release modul 11](../assets/image/ipconfig%20release%20modul%2011.png)

    c. Buka Wireshark → pilih interface jaringan aktif → klik Start Capture
    
    d. Kembali ke CMD, ketik: 
    
![ipconfig renew modul 11](../assets/image/ipconfig%20renew%20modul%2011.png)





