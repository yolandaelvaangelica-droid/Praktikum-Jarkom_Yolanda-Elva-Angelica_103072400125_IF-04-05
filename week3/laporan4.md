# Laporan4 Praktikum Jarkom IF

# modul 4 DNS

4.2 Nslookup
1. Perintah pertama yang dicoba adalah nslookup www.mit.edu. Perintah ini dipakai buat nyari alamat IP dari website www.mit.edu.
# Lampiran
nslookup www.mit.edu ![nslookup www.mit.edu](../assets/image/nslookup%20www.mit.edu.png)
Dari hasilnya, server DNS yang dipake adalah tusbind.ac.id dengan IP 10.217.7.77. Jawabannya bersifat non-authoritative, artinya datanya dari cache server DNS lokal, bukan langsung dari server MIT. Alamat IP yang balik ada dua IPv6 dan satu IPv4 yaitu 23.217.163.122, dengan alias www.mit.edu dan www.mit.edu.edgekey.net.
2. Perintah kedua adalah nslookup -type=NS mit.edu. Ini dipakai buat nyari nameserver yang bertanggung jawab atas domain mit.edu.
# Lampiran
nslookup -type=NS mit.edu (bagian 1) ![nslookup -type=NS mit.edu (bagian 1)](../assets/image/nslookup%20-type=NS%20mit.edu%20(bagian%201).png)
nslookup -type=NS mit.edu (bagian 2) ![nslookup -type=NS mit.edu (bagian 2)](../assets/image/nslookup%20-type=NS%20mit.edu%20(bagian%202).png)