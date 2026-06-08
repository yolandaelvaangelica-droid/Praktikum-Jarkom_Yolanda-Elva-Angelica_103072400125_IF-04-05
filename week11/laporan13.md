# Laporan Praktikum Jarkom IF

# Modul 13 Ethernet and ARP

## 13.2 Menangkap dan Menganalisis Frame Ethernet

Langkah-langkah:

    a. Pastikan cache browser kosong terlebih dahulu

        - Mozilla Firefox: Tools → Clear Recent History → centang Cache

        - Internet Explorer: Tools → Internet Options → Delete Files
    
     b. Jalankan Wireshark dan mulai capture paket
     
     c. Masukkan URL berikut ke browser:
        
        http://gaia.cs.umass.edu/wireshark-labs/HTTP-ethereal-lab-file3.html
       
        Browser akan menampilkan Bill of Rights AS yang cukup panjang
    
    d. Hentikan capture di Wireshark
    
    e. Temukan paket HTTP GET yang dikirim dari komputer ke gaia.cs.umass.edu pada kolom paling kiri (nomor paket) di jendela Wireshark

    f. Karena modul ini fokus pada Ethernet, ubah tampilan Wireshark agar hanya menampilkan protokol di bawah IP: AAnalyze → Enabled Protocols → uncheck IP → OK

![modul13(2)](../assets/image/modul13(2).png)

## 13.3 Address Resolution Protocol

### 13.3.1 Caching ARP

    a. Buka Command Prompt
    
    b. Lihat isi ARP cache dengan perintah: arp -a

    c. Hapus ARP cache dengan perintah:
       
       - Windows : arp -d *
       
       - Linux/MacOS : arp -d *  (butuh akses root)

![modul 13.3.1](../assets/image/modul%2013.3.1.png)


