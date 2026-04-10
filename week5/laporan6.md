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