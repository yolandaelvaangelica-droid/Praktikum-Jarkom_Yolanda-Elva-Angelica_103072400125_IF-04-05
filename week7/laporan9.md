# Laporan9 Praktikum Jarkom IF

# modul 9 WEB SERVER

9.5 skeleton kode Python untuk Web Server
kode server.py
![modul 9.5 server.py](../assets/image/modul%209.5%20server.py.png)
![modul 9.5 server.py (2)](../assets/image/modul%209.5%20server.py%20(2).png)

kode index.html
![modul 9.5 index.html](../assets/image/modul%209.5%20index.html.png)

Penjelasan Kode(9.5)
1. from socket import *
    import sys

Baris ini mengimpor modul socket untuk komunikasi jaringan, dan sys untuk menghentikan program.

2. serverSocket = socket(AF_INET, SOCK_STREAM)

Membuat socket server. AF_INET artinya menggunakan IPv4, dan SOCK_STREAM artinya menggunakan protokol TCP.

3. serverSocket.bind(('', 6789))
    serverSocket.listen(1)

- bind → mengikat socket ke port 6789 di semua interface jaringan yang tersedia
- listen(1) → server mulai mendengarkan koneksi masuk, dengan maksimal 1 koneksi yang bisa antri

4. while True:
    print('Ready to serve...')
    connectionSocket, addr = serverSocket.accept()

Server berjalan terus-menerus dalam loop. accept() akan menunggu sampai ada klien yang terhubung, lalu membuat connectionSocket khusus untuk klien tersebut.

5. message = connectionSocket.recv(1024).decode()
    filename = message.split()[1]
    f = open(filename[1:])
    outputdata = f.read()

- recv(1024) → menerima HTTP request dari browser, maksimal 1024 byte
- message.split()[1] → mengambil nama file dari request, contohnya /index.html
- filename[1:] → menghapus karakter / di depan, jadi index.html
- f.read() → membaca isi file tersebut

6. connectionSocket.send("HTTP/1.1 200 OK\r\n\r\n".encode())
    for i in range(0, len(outputdata)):
     connectionSocket.send(outputdata[i].encode())
    connectionSocket.send("\r\n".encode())
    connectionSocket.close()

- Mengirim HTTP header 200 OK ke browser, artinya file ditemukan
- Lalu mengirim isi file karakter per karakter ke browser
- Setelah selesai, koneksi ditutup

7. except IOError:
    connectionSocket.send("HTTP/1.1 404 Not Found\r\n\r\n".encode())
    connectionSocket.send("<h1>404 Not Found</h1>".encode())
    connectionSocket.close()

Kalau file tidak ditemukan, server mengirim HTTP header 404 Not Found beserta pesan error ke browser.

8. serverSocket.close()
    sys.exit()

Menutup server socket dan menghentikan program (meskipun dalam praktiknya jarang tercapai karena ada while True).

Penjelasan File HTML (index.html) (9.5)
1. <!DOCTYPE html>
    <html>

Deklarasi bahwa ini adalah dokumen HTML5, dan tag pembuka HTML.

2. <head>
    <title>Web Server Modul 9</title>
    </head>

Bagian head berisi title yang akan muncul di tab browser, yaitu "Web Server Modul 9".

3. <body>
    <h1>Hello World!</h1>
    <p>Web Server Jaringan Komputer berhasil!</p>
    </body>
    </html>

Bagian body adalah konten yang ditampilkan di browser:
- <h1> → heading besar bertuliskan "Hello World!"
- <p> → paragraf bertuliskan "Web Server Jaringan Komputer berhasil!"

