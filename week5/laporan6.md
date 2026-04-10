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

2. Apa alamat IP dari gaia.cs.umass.edu? Pada nomor port berapa ia mengirim dan menerima 
segmen TCP untuk koneksi ini?
    # Lampiran
    ![Destination port](../assets/image/Destination%20port.png)

3. 