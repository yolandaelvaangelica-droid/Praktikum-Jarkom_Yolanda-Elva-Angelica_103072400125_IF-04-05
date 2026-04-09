# Laporan3 Praktikum Jarkom IF

# Modul 3_HTTP

3.1 Basic HTTP GET/response
1. Buka Wireshark, kemudian pilih tools yang mau kita pakai bisa Wi-Fi, Local Area Connection, dsb. disini saya akan pakai Wi-Fi sebagai Toolsnya
2. Kemudian kita ketik "http" di kolom filter yang bertuliskan "Apply a display filter ... <Ctrl-/>"
3. Tunggu lebih dari 1 menit, baru mulai capture paket
4. Buka URL ini di browser: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
5. Stop capture Wireshark

# Lampiran
![Pencarian http di tools WiFi](../assets/image/Pencarian%20http%20di%20tools%20WiFi.png)
![Tampilan berhasil Umass Edu di Chrome](../assets/image/Tampilan%20berhasil%20Umass%20Edu%20di%20Chrome.png)
![Tampilan hasil browser di tools WiFi](../assets/image/Tampilan%20hasil%20browser%20di%20tools%20WiFi.png)

3.2 HTTP CONDITIONAL GET
1. Kita bersihkan cache browser dulu
2. Kemudian kita mulai Wireshark lagi
3. Buka: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file2.html
4. Refresh halaman (atau buka URL yang sama lagi)
5. Stop capture, filter dengan "http"

# Lampiran
![Tampilan Umass edu link (2)](../assets/image/Tampilan%20Umass%20edu%20link%20(2).png)
![Tampilan http link (2)](../assets/image/Tampilan%20http%20link%20(2).png)

3.3 Retrieving Long Documents
1. Bersihkan cache browser
2. Mulai capture Wireshark
3. Buka: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
4. Stop capture, filter "http"

# Lampiran
![Tampilan Umass edu link (3)](../assets/image/Tampilan%20Umass%20edu%20link%20(3).png)
![Tampilan http link (3)](../assets/image/Tampilan%20http%20link%20(3).png)

3.4 HTML dengan Embedded Objects
1. HTML dengan Embedded Objects
2. Mulai capture Wireshark
3. Buka: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
4. Stop capture, filter "http"

# Lampiran
![Tampilan Umass edu link (4)](../assets/image/Tampilan%20Umass%20edu%20link%20(4).png)
![Tampilan http link (4)](../assets/image/Tampilan%20http%20link%20(4).png)

3.5 HTTP Authentication
1. Bersihkan cache browser
2. Mulai capture Wireshark
3. Buka: http://gaia.cs.umass.edu/wireshark-labs/protected_pages/HTTP-wireshark-file5.html
    Username: wireshark-students
    Password: network
4. Stop capture, filter "http"

# Lampiran
![Tampilan Umass edu link (5)](../assets/image/Tampilan%20Umass%20edu%20link%20(5).png)
![Tampilan http link (5)](../assets/image/Tampilan%20http%20link%20(5).png)
