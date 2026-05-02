# Laporan9 Praktikum Jarkom IF

# modul 9 WEB SERVER

9.5 skeleton kode Python untuk Web Server
kode server.py
![modul 9.5 server.py](../assets/image/modul%209.5%20server.py.png)
![modul 9.5 server.py (2)](../assets/image/modul%209.5%20server.py%20(2).png)

kode index.html

![modul 9.5 index.html](../assets/image/modul%209.5%20index.html.png)

Penjelasan Kode(9.5)
1. Program dimulai dengan mengimpor modul socket untuk keperluan komunikasi jaringan dan modul sys untuk menghentikan program. Setelah itu, program membuat sebuah socket server menggunakan protokol TCP dengan IPv4, kemudian mengikatnya ke port 6789 dan mulai mendengarkan koneksi masuk.

2. Server berjalan terus-menerus dalam sebuah loop. Setiap kali ada klien yang terhubung, server menerima HTTP request dari browser dan mengambil nama file yang diminta. Nama file tersebut kemudian dibuka dan dibaca isinya oleh server.

3. Jika file ditemukan, server mengirimkan HTTP header 200 OK beserta isi file tersebut ke browser. Jika file tidak ditemukan, server mengirimkan HTTP header 404 Not Found beserta pesan error ke browser. Setelah selesai mengirim data, koneksi dengan klien ditutup dan server kembali menunggu koneksi berikutnya.

Penjelasan File HTML(9.5)
1. File HTML ini adalah file yang akan ditampilkan di browser ketika klien mengaksesnya. File ini berisi judul halaman yaitu "Web Server Modul 9" yang akan muncul di tab browser, serta dua konten utama yaitu heading "Hello World!" dan paragraf "Web Server Jaringan Komputer berhasil!" yang akan ditampilkan di halaman browser.

Output:
![modul 9.5 output](../assets/image/modul%209.5%20output.png)
![modul 9.5 hello world](../assets/image/modul%209.5%20hello%20world.png)

9.6 Latihan Tambahan 
kode server.py
![modul 9.6 server.py](../assets/image/modul%209.6%20server.py.png)
![modul 9.6 server.py (2)](../assets/image/modul%209.6%20server.py%20(2).png)
![modul 9.6 server.py (3)](../assets/image/modul%209.6%20server.py%20(3).png)

kode index.html

![modul 9.6 index.html](../assets/image/modul%209.6%20index.html.png)

Penjelasan Kode(9.6)
1. Program dimulai dengan mengimpor modul socket untuk keperluan komunikasi jaringan, modul sys untuk menghentikan program, dan modul threading untuk keperluan multithreading.

2. Berbeda dengan 9.5, pada 9.6 ini terdapat sebuah fungsi bernama handle_client yang bertugas menangani setiap klien yang terhubung. Di dalam fungsi ini, server menerima HTTP request dari browser dan menampilkannya di terminal server. Kemudian server mengambil nama file yang diminta, membuka dan membaca isinya. Jika file ditemukan, server mengirimkan HTTP header 200 OK beserta isi file tersebut ke browser. Jika file tidak ditemukan, server mengirimkan HTTP header 404 Not Found beserta pesan error ke browser. Setelah selesai, koneksi dengan klien ditutup.

3. Setelah fungsi tersebut, program membuat socket server menggunakan protokol TCP dengan IPv4, mengikatnya ke port 6789, dan mulai mendengarkan koneksi masuk dengan maksimal 5 koneksi yang bisa antri sekaligus.

4. Server kemudian berjalan terus-menerus dalam sebuah loop. Setiap kali ada klien yang terhubung, server tidak langsung menanganinya sendiri melainkan membuat sebuah thread baru yang menjalankan fungsi handle_client tadi. Dengan cara ini, server bisa melayani banyak klien secara bersamaan tanpa harus menunggu klien sebelumnya selesai terlebih dahulu, berbeda dengan 9.5 yang hanya bisa melayani satu klien dalam satu waktu.

- Untuk file HTML-nya sama persis dengan 9.5, tidak ada perubahan apapun karena yang berbeda hanya di sisi server Pythonnya saja.

Output:
![modul 9.6 output](../assets/image/modul%209.6%20output.png)
![modul 9.6 hello world](../assets/image/modul%209.6%20hello%20world.png)