# Laporan OS Pertemuan 1

<h4>Nama : Akbar Bagus Wicaksana<h4>
<h4>NIM : 254107020067<h4>
<h4>Kelas : TI-1h<h4>

## 1.10.1. Latihan Konseptual

### Latihan 1.1
Jelaskan 5 fungsi utama sistem operasi dengan contoh konkret dari minimal 2 OS berbeda (Windows, macOS, atau Linux).

### Jawaban Latihan 1.1
1. Manajemen Proses  
Mengatur aplikasi mana yang berjalan dan menggunakan CPU.
- Contoh Konkret
    > Windows: Task Manager digunakan untuk mematikan paksa ("End Task") aplikasi yang macet/hang.  
    > Linux: Perintah ("kill") di terminal digunakan untuk menghentikan proses spesifik yang membebani sistem.
2. Manajemen Memori  
Mengatur pembagian RAM agar banyak aplikasi bisa berjalan sekaligus tanpa tabrakan.
- Contoh Konkret
    > Windows: Menggunakan Pagefile.sys (memori virtual) di harddisk saat RAM fisik penuh.
    > macOS: Fitur Memory Compression memadatkan data di RAM agar tidak perlu sering memakai swap/disk, menjaga performa tetap cepat.
3. Manajemen FIle  
Mengatur cara data disimpan, dinamai, dan diorganisir dalam folder.
- Contoh Konkret
    > Windows: Menggunakan sistem partisi dengan Huruf Drive (C:, D:) dan format NTFS.
    > Linux: Menggunakan struktur pohon tunggal yang dimulai dari Root ( / ), tanpa huruf drive.
4. Manajemen Device (I/O)  
Menjembatani komunikasi antara software dengan hardware (printer, mouse, WiFi).
- Contoh Konkret
    > Windows: Fitur Plug and Play otomatis mencari driver saat hardware baru dicolokkan.
    > macOS: Driver audio (CoreAudio) yang sangat stabil dan minim latency, ideal untuk produksi musik tanpa instalasi driver rumit.
5. Antarmuka (User Interface)  
Cara Pengguna berinteraksi dengan komputer (visual atau teks)
- Contoh Konkret
    > Windows/macOS: Menggunakan GUI (ikon, jendela, mouse) yang mudah dipahami pengguna awam.
    > Linux (Server): Sering menggunakan CLI (layar hitam berisi teks perintah) karena lebih ringan dan cepat untuk server.
