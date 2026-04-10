# Laporan6 Praktikum Jarkom IF

# modul 6 TCP

1. Buka browser, Masuk ke URL: http://gaia.cs.umass.edu/wireshark-labs/alice.txt
    # Lampiran
    ![Tampilan file alice.txt](../assets/image/Tampilan%20file%20alice.txt.png)
2. Buka URL: http://gaia.cs.umass.edu/wireshark-labs/TCP-wireshark-file1.html. Klik tombol Browse dan pilih file alice.txt yang tadi disimpan
    # Lampiran
    ![TCP-wireshark-file1.html](../assets/image/TCP-wireshark-file1.html.png)
sebelum klik upload, siapkan wireshark terlebih dahulu
3. Buka Wireshark, Pilih interface yang aktif
    # Lampiran
    ![Tampilan wireshark sebelum upload alice.txt](../assets/image/Tampilan%20wireshark%20sebelum%20upload%20alice.txt.png)
4. Kembali ke browser, klik tombol "Upload alice.txt file". Tunggu sampai muncul pesan "Success! You've uploaded..."
    # Lampiran
    ![Halaman browser yang menampilkan pesan sukses upload](../assets/image/Halaman%20browser%20yang%20menampilkan%20pesan%20sukses%20upload.png)
5. Setelah berhasil, kembali ke Wireshark dan STOP capture. Di kolom filter atas Wireshark, ketik tcp. Lalu tekan Enter
    # Lampiran
    ![Tampilan Wireshark setelah difilter tcp](../assets/image/Tampilan%20Wireshark%20setelah%20difilter%20tcp.png)
6. Di menu atas Wireshark, klik Analyze -> Enabled Protocols. Cari HTTP di daftar, uncheck/Hilangkan centang HTTP lalu klik OK. Sekarang tampilan berubah, semua paket tampil sebagai TCP murni
    # Lampiran
    ![Tampilan Wireshark setelah HTTP dinonaktifkan ](../assets/image/Tampilan%20Wireshark%20setelah%20HTTP%20dinonaktifkan.png)
7. Klik paket yang di kolom Info tertulis (SYN) Lihat di bagian tengah (detail): expand Transmission Control Protocol
    # Lampiran
    ![Paket SYN dipilih, dengan detail TCP di-expand](../assets/image/Paket%20SYN%20dipilih,%20dengan%20detail%20TCP%20di-expand.png)
8. Filter kembali dengan tcp, Cari 6 segmen pertama yang dikirim dari komputer ke gaia.cs.umass.edu. Klik satu per satu: Sequence Number, waktu dikirim, waktu ACK diterima.
    # Lampiran
    ![Segmen yang Dikirim ke Gaia](../assets/image/Segmen%20yang%20Dikirim%20ke%20Gaia.png)
    ![ACK Balasan dari Gaia](../assets/image/ACK%20Balasan%20dari%20Gaia.png)
9. Pilih salah satu segmen TCP yang dikirim dari komputer ke server. Klik menu Statistics -> TCP Stream Graph -> Time-Sequence Graph (Stevens). Akan muncul grafik
    # Lampiran
    ![Grafik RTT](../assets/image/Grafik%20RTT.png)

Kalau koneksi bermasalah, download file trace resmi:
1. Download dari: http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
2. Ekstrak, cari file bernama tcp-ethereal-trace-1
3. Buka Wireshark → File → Open → pilih file tersebut
4. Langkah analisis sama seperti di atas

Pertanyaan Bagian 6.3 — Tampilan Awal Captured Trace
1. Berapa alamat IP dan nomor port TCP yang digunakan oleh komputer klien (sumber) untuk 
mentransfer file ke gaia.cs.umass.edu? Cara paling mudah menjawab pertanyaan ini adalah 
dengan memilih sebuah pesan HTTP dan meneliti detail paket TCP yang digunakan untuk 
membawa pesan HTTP tersebut. 
    # Lampiran
    ![paket HTTP POST](../assets/image/paket%20HTTP%20POST.png)
- Alamat IP klien: 192.168.18.24
- Nomor Port TCP klien: 54049
- Alamat IP tujuan (gaia): 128.119.245.12
- Port tujuan: 80

2. Apa alamat IP dari gaia.cs.umass.edu? Pada nomor port berapa ia mengirim dan menerima 
segmen TCP untuk koneksi ini?
    # Lampiran
    ![Destination port](../assets/image/Destination%20port.png)
- Alamat IP gaia.cs.umass.edu: 128.119.245.12
- Port: 80 (HTTP standard)

3. Berapa alamat IP dan nomor port TCP yang digunakan oleh komputer klien Anda (sumber) 
untuk mentransfer  ke gaia.cs.umass.edu? 
    # Lampiran
    ![Paket HTTP POST dari capture kamu sendiri](../assets/image/Paket%20HTTP%20POST%20dari%20capture%20kamu%20sendiri.png)

Pertanyaan Bagian 6.4 — Dasar TCP
1. Berapa nomor urut segmen TCP SYN yang digunakan untuk memulai sambungan TCP antara 
komputer klien dan gaia.cs.umass.edu? Apa yang dimiliki segmen tersebut sehingga 
teridentifikasi sebagai segmen SYN? 
    # Lampiran
    ![Paket [SYN]](../assets/image/Paket%20[SYN].png)

2. Berapa nomor urut segmen SYNACK yang dikirim oleh gaia.cs.umass.edu ke komputer klien 
sebagai balasan dari SYN? Berapa nilai dari field Acknowledgement pada segmen SYNACK? 
Bagaimana gaia.cs.umass.edu menentukan nilai tersebut? Apa yang dimiliki oleh segmen  
sehingga teridentifikasi sebagai segmen SYNACK? 
    # Lampiran
    ![Paket [SYN, ACK]](../assets/image/Paket%20[SYN,%20ACK].png)

3. Berapa nomor urut segmen TCP yang berisi perintah HTTP POST? Perhatikan bahwa untuk 
menemukan perintah POST, Anda harus menelusuri content field milik paket di bagian 
bawah jendela Wireshark, kemudian cari segmen yang berisi "POST" di bagian field DATA
nya. 
    # Lampiran
    ![Sequence number](../assets/image/Sequence%20number.png)

4. Anggap segmen TCP yang berisi HTTP POST sebagai segmen pertama dalam koneksi TCP. 
Berapa nomor urut dari enam segmen pertama dalam TCP (termasuk segmen yang berisi 
HTTP POST)? Pada jam berapa setiap segmen dikirim? Kapan ACK untuk setiap segmen 
diterima? Dengan adanya perbedaan antara kapan setiap segmen TCP dikirim dan kapan 
acknowledgement-nya diterima, berapakah nilai RTT untuk keenam segmen tersebut? 
Berapa nilai EstimatedRTT setelah penerimaan setiap ACK? (Catatan: Wireshark memiliki 
fitur yang memungkinkan Anda untuk memplot RTT untuk setiap segmen TCP yang dikirim. 
Pilih segmen TCP yang dikirim dari klien ke server gaia.cs.umass.edu pada jendela "daftar paket yang ditangkap". Kemudian pilih: Statistics->TCP Stream Graph- >Round Trip Time 
Graph). 
    # Lampiran
    ![waktu kirim dari kolom Time](../assets/image/waktu%20kirim%20dari%20kolom%20Time.png)
    ![packet list ACK](../assets/image/packet%20list%20ACK.png)
- Segmen 1: 16.018940100
- Segmen 2: 16.019502500
- Segmen 3: 16.297645600
- Segmen 4: 16.604700300
- Segmen 5: 16.875473700
- Segmen 6: 16.879455200

5. Berapa panjang setiap enam segmen TCP pertama?
    # Lampiran
    ![waktu kirim dari kolom Time](../assets/image/waktu%20kirim%20dari%20kolom%20Time.png)
- Segmen 1 (No. 2264): Len = 725 bytes
- Segmen 2 (No. 2265): Len = 12708 bytes
- Segmen 3 (No. 2279): Len = 25416 bytes
- Segmen 4 (No. 2288): Len = 50832 bytes
- Segmen 5 (No. 3007): Len = 22592 bytes
- Segmen 6 (No. 3039): HTTP POST (reassembled)

6. Berapa jumlah minimum ruang buffer tersedia yang disarankan kepada penerima dan 
diterima untuk seluruh trace? Apakah kurangnya ruang buffer penerima pernah 
menghambat pengiriman?
    # Lampiran
    ![Window size value](../assets/image/Window%20size%20value.png)

7. Apakah ada segmen yang ditransmisikan ulang dalam file trace? Apa yang anda periksa (di 
dalam file trace) untuk menjawab pertanyaan ini? 
    # Lampiran
    ![tcp.analysis.retransmission](../assets/image/tcp.analysis.retransmission.png)
- Ada retransmisi — terlihat paket No. 246 berlabel [TCP Retransmission]
- Source: 31.13.95.60 → 192.168.18.24
- Yang diperiksa: Sequence number yang sama dikirim ulang, Wireshark otomatis memberi label [TCP Retransmission] di kolom Info

8. Berapa banyak data yang biasanya diakui oleh penerima dalam ACK? Dapatkah anda 
mengidentifikasi kasus-kasus di mana penerima melakukan ACK untuk setiap segmen yang 
diterima?
    # Lampiran
    ![ACK Acknowledgment number (bagian 1)](../assets/image/ACK%20Acknowledgment%20number%20(bagian%201).png)
    ![ACK Acknowledgment number (bagian 2)](../assets/image/ACK%20Acknowledgment%20number%20(bagian%202).png)
- Biasanya server mengirim ACK untuk setiap 2 segmen yang diterima (delayed ACK)
- Sehingga satu ACK mengakui sekitar 2 × 1460 = 2920 bytes
- Ada juga kasus di mana server melakukan ACK untuk setiap segmen

9. Berapa throughput (byte yang ditransfer per satuan waktu) untuk sambungan TCP? 
Jelaskan bagaimana Anda menghitung nilai ini. 
    # Lampiran
    ![throughput koneksi TCP](../assets/image/throughput%20koneksi%20TCP.png)
- Reassembled TCP length: 153046 bytes ← total data
- Time segmen pertama (No. 3039): 16.879455200
- Time HTTP response (No. 3124): 17.172159700
- Time since first frame in this TCP stream: 1.131923700 seconds
Throughput = 153046 bytes / 1.131923700 detik
           = ± 135.213 bytes/detik
           = ± 135 KB/s
           = ± 1.08 Mbps

Pertanyaan Bagian 6.5 — Congestion Control TCP
1. Gunakan alat plotting Time-Sequence-Graph (Stevens) untuk melihat grafik nomor urut 
berbanding waktu dari segmen yang dikirim oleh klien ke server gaia.cs.umass.edu. 
Dapatkah Anda mengidentifikasi di mana fase “slow start” TCP dimulai dan berakhir, dan 
pada bagian mana algoritma ”congestion avoidance” mengambil alih? Berikan komentar 
tentang bagaimana data yang diukur berbeda dari perilaku ideal TCP yang telah kita pelajari.
    # Lampiran
    ![Grafik Time-Sequence Stevens](../assets/image/Grafik%20Time-Sequence%20Stevens.png)

2. Jawablah kedua pertanyaan di atas untuk trace yang Anda dapatkan ketika Anda 
mengirimkan file dari komputer ke gaia.cs.umass.edu.
Fase Slow Start:
- Terlihat di bagian kiri grafik (sekitar 0-1 detik pertama)
- Titik-titik naik sangat curam/vertikal dari 0 bytes langsung loncat ke ~150 kB
- Ini karena cwnd (congestion window) berlipat ganda setiap RTT
Fase Congestion Avoidance:
- Setelah titik-titik berhenti naik, grafik mendatar/flat sampai akhir
- Ini bukan congestion avoidance sesungguhnya, tapi karena file sudah habis terkirim sebelum sempat masuk fase congestion avoidance
Perbandingan dengan TCP Ideal:
- TCP ideal seharusnya: slow start dulu (naik eksponensial) → lalu congestion avoidance (naik linear)
- Grafik hanya terlihat slow start saja karena file alice.txt (~153 KB) terlalu kecil dan jaringan terlalu cepat sehingga langsung habis terkirim dalam waktu sangat singkat (~1 detik)