# Laporan Praktikum Jarkom IF

# Modul 12 ICMP dan Asistensi Tugas Besar

## 12.2 ICMP dan Ping

Langkah-langkah:

   a. Buka aplikasi Windows Command Prompt
   
   b. Jalankan Wireshark dan mulai capture paket dari interface Wi-Fi
   
   c. Masukkan perintah berikut di Command Prompt: ping -n 10 8.8.8.8

   Argumen "-n 10" berarti 10 paket ping akan dikirim ke host tujuan
   
   d. Tunggu hingga program Ping selesai berjalan
   
   e. Hentikan capture paket di Wireshark
   
   f. Masukkan filter "icmp" di kolom display filter Wireshark untuk menampilkan hanya paket ICMP
   
   Hasil pengamatan pada Wireshark menunjukkan bahwa paket ICMP tidak berhasil tertangkap meskipun perintah ping berhasil dijalankan dan mendapat reply dari 8.8.8.8. Hal ini disebabkan oleh keterbatasan driver Wi-Fi pada Windows yang tidak mendukung capture outbound traffic secara langsung. Wireshark hanya menampilkan paket dengan protokol IPv4 (0x0800) namun layer ICMP di dalamnya tidak ter-decode karena jaringan kampus menggunakan VLAN tagging yang membuat Wireshark tidak dapat mengidentifikasi protokol ICMP secara langsung. Berdasarkan teori, seharusnya akan tertangkap 20 paket ICMP — 10 paket Echo Request (Type: 8, Code: 0) yang dikirim dari komputer ke host tujuan, dan 10 paket Echo Reply (Type: 0, Code: 0) yang diterima sebagai balasan.

![modul 12.2](../assets/image/modul%2012.2.png)

## 12.3 ICMP dan Traceroute

Langkah-langkah:

    a. Buka aplikasi Windows Command Prompt

    b. Jalankan Wireshark dan mulai capture paket dari interface Wi-Fi

    c. Masukkan perintah berikut di Command Prompt:

   tracert www.inria.fr

   Atau gunakan path lengkap: c:\windows\system32\tracert www.inria.fr
   
   d. Tunggu hingga program Traceroute selesai berjalan
   
   e. Hentikan capture paket di Wireshark
   
   f. Masukkan filter "icmp" di kolom display filter Wireshark
   
   Hasil pengamatan pada Wireshark menunjukkan bahwa paket ICMP dari traceroute juga tidak berhasil tertangkap, dengan alasan yang sama seperti pada percobaan 12.2 yaitu keterbatasan driver Wi-Fi dan VLAN tagging pada jaringan kampus. Berdasarkan teori, seharusnya akan terlihat paket ICMP yang dikirim dengan TTL = 1, 2, 3, dan seterusnya, serta paket ICMP Time Exceeded (Type: 11, Code: 0) yang dikembalikan oleh setiap router perantara ketika TTL habis. Paket TTL-exceeded tersebut berisi header IP asli dan 8 byte pertama dari paket yang menyebabkan error, sehingga strukturnya lebih kompleks dibanding paket Echo Request/Reply biasa.

![modul 12.2](../assets/image/modul%2012.2.png)
