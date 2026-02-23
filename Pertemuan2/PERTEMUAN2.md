# **Laporan OS Pertemuan 2**

**Nama** : Akbar Bagus Wicaksana  
**NIM** : 254107020067  
**Kelas** : TI-1H  

---

## **Praktikum: Manajemen Perangkat Keras & Perintah Dasar**

### **Praktikum 2.1 Identifikasi CPU dan Memori**
**Tujuan:** Memahami spesifikasi CPU dan kondisi memori pada server/VM.

**Langkah-langkah:**

1. **Tampilkan informasi CPU: lscpu** 
   ![Step 1](img/1.png "Step1")

2. **Tampilkan ringkasan memori: free -h** 
   ![Step 2](img/2.png "Step2")

### **Praktikum 2.2 Identifikasi Perangkat PCI/USB dan Driver**
**Tujuan:** Mengenali perangkat PCI/USB dan melihat driver/modul yang dipakai.

**Langkah-langkah:**

1. **Lihat daftar perangkat PCI: lspci** 
   ![Step 1](img/3.png "Step1")

2. **Lihat perangkat PCI beserta driver kernel yang digunakan: lspci -nnk** 
   ![Step 2](img/4.png "Step2")

3. **Fokus pada NIC (Ethernet) untuk mencari modul driver: lspci -nnk | grep -A3 -i ethernet** 
   ![Step 3](img/5.png "Step3")

4. **Lihat perangkat USB: lsusb** 

   ![Step 4](img/6.png "Step4")

5. **Lihat topologi USB (tree): lsusb -t** 
   ![Step 5](img/7.png "Step5")

### **Praktikum 2.3 Identifikasi Storage dan Filesystem**
**Tujuan:** Memahami disk/partisi dan filesystem yang terpasang.

**Jawaban:**

1. **Lihat daftar disk/partisi: lsblk -f** 
   ![Step 1](img/8.png "Step1")

2. [cite_start]**Tampilkan UUID dan tipe filesystem: sudo blkid** 
   ![Step 2](img/9.png "Step2")

3. **Lihat mount point untuk root filesystem: findmnt /** 
   
   ![Step 3](img/10.png "Step3")

### **Praktikum 2.4 Melihat Modul Aktif dan Informasinya**
**Tujuan:** Mengenal modul aktif dan keterkaitannya dengan perangkat.

**Langkah-langkah:**

1. **Cek versi kernel: uname -r** 

   ![Step 1](img/11.png "Step1")

2. **Tampilkan daftar modul aktif: lsmod | head** 

   ![Step 2](img/12.png "Step2")

3. **Pilih salah satu modul (contoh aman: loop) dan lihat detailnya: modinfo loop** 
   ![Step 3](img/13.png "Step3")

4. **Muat modul (jika belum aktif), lalu verifikasi: sudo modprobe loop dilanjut lsmod | grep -i loop** 
   ![Step 4](img/14.png "Step4")

### **Praktikum 2.5 Konfigurasi Auto-load dan Blacklist**
**Tujuan:** Memahami cara membuat modul otomatis dimuat atau diblokir.

**Langkah-langkah:**

1. **Buat file auto-load: echo "loop" | sudo tee /etc/modules-load.d/loop.conf** 
   ![Step 1](img/16.png "Step1")

2. **Simulasikan verifikasi dengan memastikan modul sudah aktif: lsmod | grep -i loop** 
   ![Step 2](img/17.png "Step2")

### **Praktikum 2.6 Mengenali Block vs Character Device**
**Tujuan:** Membedakan perangkat disk vs terminal.

**Langkah-langkah:**

1. **Lihat detail salah satu disk (Block Device): ls -l /dev/sda** 

   ![Step 1](img/18.png "Step1")

2. **Lihat detail device terminal (Character Device): ls -l /dev/tty** 

   ![Step 2](img/19.png "Step2")

3. **Lihat disk dan partisi untuk mengaitkan dengan /dev: lsblk** 
   ![Step 3](img/20.png "Step3")

### **Praktikum 2.7 Melihat Informasi udev**
**Tujuan:** Melihat metadata yang dipakai udev untuk membuat device node.

**Langkah-langkah:**

1. **Cek atribut udev untuk disk: udevadm info --query=all --name=/dev/sda | head -n 30** 
   ![Step 1](img/21.png "Step1")

### **Praktikum 2.8 Membuat Workspace Praktikum**
**Tujuan:** Membuat area kerja aman untuk semua latihan bab ini.

**Langkah-langkah:**

1. **Buat direktori praktikum dan masuk ke dalamnya: mkdir -p ~/praktikum-os/week02` lalu `cd ~/praktikum-os/week02** 
   ![Step 1](img/22.png "Step1")

2. **Buat beberapa file contoh: touch notes.txt data.log config.txt lalu ls -lah** 
   ![Step 2](img/23.png "Step2")

3. **Isi file log contoh: gunakan perintah `echo` ke dalam `data.log` lalu lihat isinya dengan cat data.log** 
   ![Step 3](img/24.png "Step3")

4. **Baca file dengan less: less data.log** 

   ![Step 4](img/25.png "Step4")

### **Praktikum 2.9 Pencarian Pola dengan grep**
**Tujuan:** Mencari baris yang cocok dengan pola (pattern) di file.

**Langkah-langkah:**

1. **Cari baris yang mengandung ERROR pada data.log: grep "ERROR" data.log** 
   ![Step 1](img/26.png "Step1")

2. **Cari tanpa memperhatikan huruf besar/kecil: grep -i "error" data.log** 
   ![Step 2](img/27.png "Step2")

3. **Tampilkan nomor baris: grep -n "WARN" data.log** 
   ![Step 3](img/28.png "Step3")

4. **Tampilkan baris yang tidak cocok (invert match): grep -v "INFO" data.log** 
   ![Step 4](img/29.png "Step4")

### **Praktikum 2.10 Substitusi dengan sed**
**Tujuan:** Melakukan transformasi teks, terutama substitusi (cari-ganti).

**Langkah-langkah:**

1. **Siapkan file konfigurasi latihan: config.txt** 
   ![Step 1](img/30.png "Step1")

2. **Ganti dev menjadi prod (tanpa mengubah file asli): sed 's/MODE dev/MODE=prod/' config.txt** 
   ![Step 2](img/31.png "Step2")

3. **Terapkan perubahan langsung ke file (-i): sed -i 's/MODE dev/MODE=prod/' config.txt lalu cat config.txt** 
   ![Step 3](img/32.png "Step3")

4. **Ganti semua kemunculan kata (global replacement): sed -i 's/myserver/node/g' config.txt lalu cat config.txt** 
   ![Step 4](img/33.png "Step4")

### **Praktikum 2.11 Ekstraksi Kolom dengan awk**
**Tujuan:** Memproses teks berbasis kolom/field.

**Langkah-langkah:**

1. **Lihat output: df -h** 

   ![Step 1](img/34.png "Step1")

2. **Ambil kolom filesystem dan persentase pemakaian: df -h | awk 'NR==1 {print $1, $5, $6} NR>1 {print $1, $5, $6}'** 
   ![Step 2](img/35.png "Step2")

3. **Filter hanya yang pemakaian disk di atas 80%: df -h | awk 'NR==1 || ($5+0) [cite_start]> 80 {print $1, $5, $6}'** 
   ![Step 3](img/36.png "Step3")

### **Praktikum 2.12 Melihat Proses dengan ps**
**Tujuan:** Melihat snapshot proses dan pemakaian CPU/MEM.

**Langkah-langkah:**

1. **Tampilkan semua proses (format BSD): ps aux | head** 
   ![Step 1](img/37.png "Step1")

2. **Cari proses tertentu (misal sshd): ps aux | grep -i sshd** 
   ![Step 2](img/38.png "Step2")

### **Praktikum 2.13 Monitoring Real-time dengan top**
**Tujuan:** Memantau pemakaian resource secara real-time.

**Langkah-langkah:**

1. **Jalankan top dan amati pemakaian CPU/RAM: top** 
   ![Step 1](img/39.png "Step1")

### **Praktikum 2.14 Menghentikan Proses dengan kill**
**Tujuan:** Mengirim sinyal untuk menghentikan proses berdasarkan PID.

**Langkah-langkah:**

1. **Jalankan proses dummy di background: sleep 300 &** 
   ![Step 1](img/40.png "Step1")

2. **Cari PID proses sleep: ps aux | grep -E "sleep 300" | grep -v grep** 
   ![Step 2](img/41.png "Step2")

3. **Hentikan dengan SIGTERM: kill <PID_ANDA>** 
   ![Step 3](img/42.png "Step3")

4. **Verifikasi proses berhenti: ps aux | grep -E "sleep 300" | grep -v grep** 
   ![Step 4](img/43.png "Step4")

### **Praktikum 2.15 Cek Disk, Load, dan Service**
**Tujuan:** Melakukan "Health Check" pada server.

**Langkah-langkah:**

1. **Cek penggunaan disk: df -h** 

   ![Step 1](img/44.png "Step1")

2. **Cari direktori yang besar: sudo du -sh /var/* 2>/dev/null | sort -h | tail -n 10** 
   ![Step 2](img/45.png "Step2")

3. **Cek load dan uptime: uptime** 

   ![Step 3](img/46.png "Step3")

4. **Cek service yang gagal: systemctl --failed** 

   ![Step 4](img/47.png "Step4")

5. **Ambil log error terbaru: journalctl -xe | tail -n 50** 
   ![Step 5](img/48.png "Step5")

### **Praktikum 2.16 Monitoring Port dan Koneksi**
**Tujuan:** Melihat interface, routing, dan port yang sedang listen.

**Langkah-langkah:**

1. **Lihat interface dan IP: ip a** 
   ![Step 1](img/49.png "Step1")

2. **Lihat routing table: ip r** 

   ![Step 2](img/50.png "Step2")

3. **Lihat port yang sedang listening: sudo ss -tulpn** 
   ![Step 3](img/51.png "Step3")

---

## **Latihan Praktikal**

### **Latihan 2.A**
**Soal:** Jalankan lspci -nnk. Pilih 1 perangkat PCI dan tuliskan: nama perangkat, ID vendor:device, dan kernel driver in use.

**Jawaban:**

1. **Jalankan lspci -nnk dan pilih perangkat:**
   ![Step 1](img/52.png "Step1")

2. **Hasil Analisis (Sesuai Screenshot):**
   * **Nama Perangkat:** Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller
   * **ID Vendor:Device:** [8086:100e]
   * **Kernel driver in use:** e1000

### **Latihan 2.B**
**Soal:** Tentukan device root filesystem dengan findmnt /. Lalu cocokkan dengan lsblk -f dan tuliskan tipe filesystem serta UUID-nya.

**Jawaban:**

1. **Tentukan device root: findmnt /**

   ![Step 1](img/53.png "Step1")

2. **Cocokkan dengan partisi: lsblk -f**
   ![Step 2](img/54.png "Step2")

3. **Hasil Analisis:**
   * **Device Root (`/`):** ubuntu--vg-ubuntu--lv
   * **Tipe Filesystem:** ext4 
   * **UUID:** 2057a55d-fef1-4ed0-96c7-669baf808d04

### **Latihan 2.C**
**Soal:** Buat file server.log berisi minimal 10 baris dengan variasi kata: INFO, WARN, ERROR. Gunakan grep untuk menampilkan hanya baris ERROR.

**Jawaban:**

1. **Buat file server.log dengan perintah cat > server.log lalu isi 10 baris:**
   ![Step 1](img/55.png "Step1")

2. **Gunakan grep untuk mencari kata ERROR: grep "ERROR" server.log**
   ![Step 2](img/56.png "Step2")

### **Latihan 2.D**
**Soal:** Gunakan sed untuk mengganti semua kata server menjadi node pada file latihan. Tunjukkan sebelum dan sesudah.

**Jawaban:**

1. **Tampilkan teks SEBELUM diubah: cat server.log**

   ![Step 1](img/57.png "Step1")

2. **Gunakan perintah sed -i 's/server/node/g' server.log lalu tampilkan hasilnya SESUDAH diubah:**
   ![Step 2](img/58.png "Step2")

### **Latihan 2.E**
**Soal:** Gunakan `df -h` lalu `awk` untuk menampilkan filesystem yang penggunaan disk di atas 70%.

**Jawaban:**

1. **Jalankan perintah: df -h | awk 'NR==1 || ($5+0) > 70 {print $1, $5, $6}'**
   ![Step 1](img/59.png "Step1")

### **Latihan 2.F**
**Soal:** Jalankan sleep 600 &. Temukan PID-nya dengan ps. Hentikan dengan SIGTERM. Jelaskan beda SIGTERM vs SIGKILL.

**Jawaban:**

1. **Jalankan proses sleep 600 & lalu temukan PID-nya dengan `ps aux | grep sleep:**
   ![Step 1](img/60.png "Step1")

2. **Hentikan dengan perintah kill <PID>:**

   ![Step 2](img/61.png "Step2")

3. **Perbedaan SIGTERM vs SIGKILL:**
   * **SIGTERM (15):** Meminta proses berhenti secara baik-baik, aplikasi bisa menyimpan data dulu sebelum mati.
   * **SIGKILL (9):** Memaksa proses berhenti seketika tanpa ampun.

### **Latihan 2.G**
**Soal:** Gunakan systemctl --failed. Jika tidak ada yang gagal, pilih satu service aktif (misal ssh) dan tampilkan status serta 30 baris log terakhirnya.

**Jawaban:**

1. **Gunakan perintah: systemctl --failed**

   ![Step 1](img/62.png "Step1")

2. **Tampilkan status service aktif (contoh: ssh): systemctl status ssh**
   ![Step 2](img/63.png "Step2")

3. **Tampilkan 30 baris log terakhirnya: journalctl -u ssh -n 30**
   ![Step 3](img/64.png "Step3")