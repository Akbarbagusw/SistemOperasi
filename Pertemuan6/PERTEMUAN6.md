# **Laporan OS Pertemuan 4**

**Nama** : Akbar Bagus Wicaksana  
**NIM** : 254107020067  
**Kelas** : TI-1H  

---

## **Praktikum 6.1: Melihat Proses dan Thread**
**Langkah-langkah:**  
1.Tampilkan semua proses yang berjalan: ps aux  
![Step 1](img/1.png "Step1")  
2.Tampilkan proses beserta thread-nya, dapat dilihat pada kolom LWP (LightWeight
Process ID): ps aux -L  
![Step 2](img/2.png "Step2")  
3.Lihat PID shell aktif dan detail prosesnya: echo $$, ps -p $$ -f  
![Step 3](img/3.png "Step3")
4.Lihat hierarki proses secara visual: pstree -p
![Step 4](img/4.png "Step4")

### **Latihan 6.1**
1.Berapa total proses yang berjalan? Proses apa yang memiliki PID terkecil?
![Step 1](img/36.png "Step1")
2.Jalankan pstree -p dan temukan proses bash Anda. Proses apa yang menjadi induk (PPID) dari bash tersebut?  
![Step 2](img/37.png "Step2")
Pada struktur pohon (tree) yang muncul, Anda akan melihat garis cabang sebelum proses bash Anda. Induk (PPID) dari bash tersebut biasanya adalah program terminal emulator yang Anda gunakan (contoh: gnome-terminal-server) atau layanan sshd jika Anda sedang remote menggunakan SSH.  
3.Bandingkan output ps aux dan ps aux -L. Apa perbedaan yang Anda lihat?  
Perbedaan utamanya ada pada kolom informasi yang ditampilkan. Perintah ps aux hanya menampilkan informasi ringkas dari proses utama. Sedangkan perintah ps aux -L akan memunculkan kolom tambahan bernama LWP (Light-Weight Process ID), yang fungsinya untuk menampilkan rincian setiap thread tunggal yang ada di dalam sebuah proses secara mendetail.  

## **Percobaan 6.2: Mengamati Siklus Hidup Proses**
**Langkah-langkah:**  
1.Buat proses di background dan amati kondisinya: sleep 60 &, ps aux | grep sleep  
![Step 1](img/6.png "Step1")
2.mati perubahan exit code dari perintah yang berhasil dan gagal:  
![Step 2](img/7.png "Step2")  

### **Latihan 6.2**
1.Jalankan sleep 120 & dan amati kolom STAT pada ps aux. Kondisi apa yang ditampilkan? Mengapa proses sleep berada di kondisi tersebut?  
Kondisinya adalah S (Sleeping). Proses berada di kondisi ini karena sedang menunggu event (jeda waktu habis) dan dapat diinterupsi oleh sinyal.  
2.Jalankan beberapa perintah yang berhasil dan yang gagal, lalu catat exit code masing-masing. Pola apa yang Anda temukan?  
Perintah yang berhasil akan memberikan nilai exit code 0, sedangkan perintah yang gagal memberikan nilai selain nol (misalnya 2).

## **Praktikum 6.3: Mengatur Prioritas Proses**
**Langkah-langkah:**  
1.Jalankan proses dengan prioritas rendah: nice -n 10 sleep 300 &  
![Step 1](img/10.png "Step1")
2.Verifikasi nilai nice pada kolom NI: ps aux | grep sleep  
![Step 2](img/11.png "Step2")
3.Ubah nilai nice proses yang sudah berjalan:  
![Step 3](img/12.png "Step3")
4.Bersihkan proses percobaan: kill %1  

### **Latihan 6.3**
1.Jalankan nice -n 5 sleep 200 & dan verifikasi nilai NI-nya dengan ps.  
![Step 1](img/30.png "Step1")
2.Ubah nilai nice menjadi 10 menggunakan renice, lalu verifikasi kembali.  
![Step 2](img/31.png "Step2")
3.Coba ubah nilai nice menjadi -5 tanpa sudo. Apa yang terjadi? Mengapa Linux membatasi hal ini untuk user biasa?  
Akses akan ditolak (Permission denied). Linux membatasi nilai nice negatif (prioritas lebih tinggi dari normal) hanya untuk root agar user biasa tidak memonopoli CPU sistem.  

## **Praktikum 6.4: Mengirim Sinyal ke Proses**
**Langkah-langkah:**  
1.Buat proses percobaan:  
![Step 1](img/13.png "Step1")
2.Hentikan satu proses dengan SIGTERM dan verifikasi:  
![Step 2](img/14.png "Step2")
3.Jeda dan lanjutkan proses dengan SIGSTOP/SIGCONT:  
![Step 3](img/15.png "Step3")
4.Hentikan semua proses sleep sekaligus: pkill sleep  
![Step 4](img/16.png "Step4")

### **Latihan 6.4**
1.Jalankan sleep 400 &, kirim SIGSTOP, dan amati perubahan kolom STAT. Kondisi apa yang muncul?  
Saat dikirim SIGSTOP, proses sleep akan berubah kondisinya menjadi T (Stopped) atau dijeda.  
2.Kirim SIGCONT dan verifikasi proses kembali berjalan.  
Setelah dikirim SIGCONT, proses akan kembali berjalan (kolom STAT kembali ke S)  
3.Hentikan proses dengan SIGTERM lalu verifikasi sudah tidak ada. Kapan Anda memilih SIGKILL daripada SIGTERM?  
SIGTERM digunakan sebagai default untuk menghentikan proses secara normal sehingga aplikasi sempat melakukan cleanup. SIGKILL mematikan proses secara paksa (berisiko pada data) dan hanya digunakan jika aplikasi hang dan kebal terhadap SIGTERM.  

## **Praktikum 6.5: Manajemen Job Foreground dan Background**
**Langkah-langkah:**  
1.Jalankan tiga job di background  
![Step 1](img/17.png "Step1")
2.Bawa job pertama ke foreground, jeda, lalu kembalikan ke background  
![Step 2](img/18.png "Step2")
3.Hentikan semua job: kill %1 %2 %3, jobs
![Step 3](img/19.png "Step3")

### **Latihan 6.5**
1.Jalankan top di foreground. Apa yang terjadi di terminal?  
![Step 1](img/32.png "Step1")
2.Tekan Ctrl+Z dan cek statusnya dengan jobs. Kondisi apa yang ditampilkan?  
![Step 2](img/33.png "Step2")
3.Pindahkan ke background dengan bg. Apakah top dapat berjalan dengan baik di background? Mengapa?  
Proses interaktif seperti top tidak dapat berjalan dengan baik di background karena aplikasinya membutuhkan akses input dan output ke layar terminal secara terus-menerus.  
4.Kembalikan ke foreground dengan fg, lalu keluar dengan q .  
![Step 4](img/34.png "Step4")

## **Praktikum 6.6: Pemantauan Proses**
**Langkah-langkah:**  
1.Temukan proses dengan penggunaan CPU dan memori tertinggi:  
![Step 1](img/20.png "Step1")
2.Jalankan top dan eksplorasi shortcut-nya:  
![Step 2](img/21.png "Step2")
3.Instal dan jalankan htop  
![Step 3](img/22.png "Step3")

### **Latihan 6.6**
1.Gunakan ps aux –sort=%mem untuk menemukan proses yang menggunakan memori paling banyak di VM Anda. Proses apa itu?  
Proses memori terbesar. Jika di sistem dengan GUI, umumnya antarmuka desktop atau browser berada di urutan teratas.  
2.Di dalam top, tekan 1 . Apa yang berubah pada tampilan? Mengapa informasi ini berguna?  
Tampilan rata-rata total CPU akan berubah (membentang) menjadi informasi penggunaan CPU spesifik per core (misal: Cpu0, Cpu1, dsb). Sangat berguna untuk mendeteksi apabila ada program bermasalah yang hanya memonopoli satu inti CPU.  
3.Di dalam htop, navigasikan ke proses sshd menggunakan tombol panah. Tekan F9 dan amati opsi sinyal yang tersedia.  
![Step 3](img/35.png "Step3")

## **Latihan 6.A**
**Eksplorasi Proses Sistem**
 1. Jalankan ps aux –forest dan temukan proses dengan PID 1. Apa nama dan fungsi proses tersebut dalam sistem Linux modern?  
![Step 1](img/23.png "Step1")  
 Bernama systemd (atau init), berfungsi menginisialisasi sistem saat boot dan menjadi induk bagi proses lainnya.  
 2. Hitung berapa proses yang dimiliki oleh user root dan berapa yang dimiliki oleh user Anda. Mengapa root memiliki lebih banyak proses?  
 User root memiliki proses lebih banyak karena bertugas menjalankan layanan inti sistem di background.  
 3. Temukan semua proses yang berada dalam kondisi S. Mengapa sebagian besar proses di sistem berada dalam kondisi ini?  
 Mayoritas proses berstatus ini karena sedang "sleep" menunggu event atau input/output agar tidak memboroskan CPU.  

## **Latihan 6.B**
**Simulasi Manajemen Job**
 1. Jalankan tiga perintah sleep dengan durasi 100, 200, dan 300 detik di background. Verifikasi ketiganya dengan jobs.  
![Step 1](img/24.png "Step1")
 2. Bawa job kedua ke foreground, jeda dengan Ctrl+Z , lalu kembalikan ke background dengan bg.  
![Step 2](img/25.png "Step2")
 3. Hentikan job pertama dengan kill %1. Tampilkan kembali daftar job. Berapa job yang tersisa?  
![Step 3](img/26.png "Step3")

## **Latihan 6.C**
**Prioritas dan Sinyal**
 1. Jalankan dua proses sleep: satu dengan nice +5 dan satu dengan nice +15. Verifikasi nilai NI keduanya dengan ps.  
![Step 1](img/27.png "Step1")
 2. Gunakan renice untuk mengubah nice proses pertama menjadi +10. Proses mana yang kini lebih diprioritaskan scheduler?  
![Step 2](img/28.png "Step2")  
 Proses pertama (nice +10) kini lebih diprioritaskan oleh scheduler karena nilainya lebih kecil (prioritas lebih tinggi) dibanding proses kedua (+15).  
 3. Kirim SIGSTOP ke salah satu proses, verifikasi kondisi T-nya, lalu kirim SIGCONT. Akhiri semua proses percobaan dengan pkill sleep.  
![Step 3](img/29.png "Step3")