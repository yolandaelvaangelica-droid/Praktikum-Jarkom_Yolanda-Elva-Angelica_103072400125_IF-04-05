# Laporan14 Praktikum Jarkom IF

# modul 14 802.11 WiFi

## 14.2 Starting

    1. Download file zip dari http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
    
    2. Ekstrak file Wireshark_802_11.pcap
    
    3. Buka Wireshark → File → Buka → pilih file Wireshark_802_11.pcap

    Konteks aktivitas host dalam jejak ini adalah:
    
    - Host sudah terasosiasi dengan AP 30 Munroe St sejak awal pelacakan
    
    - Pada t = 24,82 → host membuat HTTP request ke gaia.cs.umass.edu (IP: 128.119.245.12)
    
    - Pada t = 32,82 → host membuat HTTP request ke www.cs.umass.edu (IP: 128.119.240.19)
    
    - Pada t = 49,58 → host disconnect dari 30 Munroe St dan mencoba connect ke linksys_ses_24086 namun gagal karena AP tersebut tidak terbuka
    
    - Pada t = 63,0 → host menyerah dan kembali berasosiasi dengan 30 Munroe St

![modul 14 gambar 1](../assets/image/modul%2014%20gambar%201.png)

## 14.3 Beacon Frames

    1. Pada daftar paket, cari frame dengan Protocol: IEEE 802.11 dan Info berisi "Beacon frame"
    
    2. Klik salah satu Beacon frame untuk memilihnya
    
    3. Di panel tengah, expand bagian "IEEE 802.11 wireless LAN management frame"
    
    4. Perhatikan subbidang seperti: SSID, Beacon Interval, Capabilities, Supported Rates, dll

![modul 14 gambar 2](../assets/image/modul%2014%20gambar%202.png)

![modul 14 gambar 3](../assets/image/modul%2014%20gambar%203.png)

## 14.4 Data Transfer

    1. Pada filter Wireshark, ketik filter untuk melihat paket HTTP: http
    
    2. atau filter berdasarkan IP tujuan: ip.dst == 128.119.245.12

    3. Cari paket pada sekitar t = 24,82 yang berisi permintaan HTTP GET ke alice.txt
    
    4. Klik paket HTTP GET tersebut
    
    5. Di panel detail, expand bagian IEEE 802.11 untuk melihat alamat MAC sumber, tujuan, dan BSSID

![modul 14 gambar 4](../assets/image/modul%2014%20gambar%204.png)

![modul 14 gambar 5](../assets/image/modul%2014%20gambar%205.png)

## 14.5 Association/Disassociation

    1. Pada filter Wireshark, hapus filter sebelumnya agar semua paket tampil
    
    2. Scroll ke area waktu sekitar t = 49,58 untuk melihat proses disasosiasi dan asosiasi ke AP baru

    3. Cari frame dengan Info:
    
    - "Disassociation" → frame ketika host memutus dari 30 Munroe St AP
    - "Association Request" → frame tipe 0, subtipe 0 (host → AP)
    - "Association Response" → frame tipe 0, subtipe 1 (AP → host)
    
    4. Klik masing-masing frame dan expand detail IEEE 802.11

![modul 14 gambar 6](../assets/image/modul%2014%20gambar%206.png)

![modul 14 gambar 7](../assets/image/modul%2014%20gambar%207.png)

![modul 14 gambar 8](../assets/image/modul%2014%20gambar%208.png)