# Laporan7 Praktikum Jarkom IF

# modul 7 SOCKET PROGRAMMING: MEMBUAT APLIKASI JARINGAN 

Modul 7 mengajarkan cara membuat aplikasi jaringan menggunakan socket programming dengan Python. Ada 2 jenis yang dipelajari:
- UDP (User Datagram Protocol) — tanpa koneksi
- TCP (Transmission Control Protocol) — berorientasi koneksi

Tahap 1 — Buat Folder & File
1. Buat folder baru contoh: modul 7 praktikum jarkom
2. Buka VS Code -> File -> Open Folder -> pilih folder tadi
3. Buat file baru: klik ikon New File di panel kiri

Kode UDPServer.py
# Lampiran
![Kode UDPServer.py (bagian 1)](../assets/image/Kode%20UDPServer.py%20(bagian%201).png)
![Kode UDPServer.py (bagian 2)](../assets/image/Kode%20UDPServer.py%20(bagian%202).png)
from socket import *
    -> import library socket

serverPort = 12000
    -> tentukan port yang dipakai

serverSocket = socket(AF_INET, SOCK_DGRAM)
    -> buat socket UDP (DGRAM = UDP, INET = IPv4)

serverSocket.bind(('', serverPort))
    -> ikat socket ke port 12000, '' = semua interface

while True:

    message, clientAddress = serverSocket.recvfrom(2048)
    -> tunggu & terima pesan dari client, max 2048 bytes

    modifiedMessage = message.decode().upper()
    -> decode bytes → string, lalu ubah jadi HURUF BESAR

    serverSocket.sendto(modifiedMessage.encode(), clientAddress)
    -> kirim balik ke client, encode string → bytes 

Kode UDPClient.py
![Kode UDPClient.py (bagian 1)](../assets/image/Kode%20UDPClient.py%20(bagian%201).png)
![Kode UDPClient.py (bagian 2)](../assets/image/Kode%20UDPClient.py%20(bagian%202).png)
from socket import *

serverName = 'localhost'
    -> alamat server (komputer yang sama)

serverPort = 12000
    -> port tujuan

clientSocket = socket(AF_INET, SOCK_DGRAM)
    -> buat socket UDP

sentence = input('Masukkan kalimat: ')
    -> minta input dari user

clientSocket.sendto(sentence.encode(), (serverName, serverPort))
    -> kirim pesan ke server (encode = ubah string → bytes)

modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
    -> terima balasan dari server

print(modifiedMessage.decode())
    -> decode bytes → string lalu print

clientSocket.close()
    -> tutup socket

# Contoh Output
![Output UDPServer.py](../assets/image/Output%20UDPServer.py.png)
![Output UDPClient.py](../assets/image/Output%20UDPClient.py.png)
