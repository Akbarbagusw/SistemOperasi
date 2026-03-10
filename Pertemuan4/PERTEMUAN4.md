# **Laporan OS Pertemuan 4**

**Nama** : Akbar Bagus Wicaksana  
**NIM** : 254107020067  
**Kelas** : TI-1H  

---

### **Percobaan 1: Directory**
**Hasil:**  
1.Melihat direktori HOME  
![Step 1](img/1.png "Step1")
2.Menyimpan hasilnya ke file large-logs.txt  
![Step 2](img/2.png "Step2")  
3.Menampilkan output juga di terminal menggunakan tee  
![Step 3](img/3.png "Step3")
4.Menangani error dengan redirect ke error.logMemahami spesifikasi CPU dan kondisi memori pada server/VM.
![Step 4](img/4.png "Step4")

### **Percobaan 2: Manipulasi file**
**Hasil:**  
1.Perintah cp untuk mengkopi file atau seluruh direktori  
![Step 1](img/6.png "Step1")
2.Perintah mv untuk memindah file  
![Step 2](img/7.png "Step2")  
3.Perintah rm untuk menghapus file  
![Step 3](img/8.png "Step3")

### **Percobaan 3: Symbolic Link**
**Hasil:**  
1.Membuat shortcut (file link)  
![Step 1](img/9.png "Step1")

### **Percobaan 4: Melihat Isi File**
**Hasil:**   
![Step 1](img/10.png "Step1")

### **Percobaan 5: Mencari file**
**Hasil:**  
1.Perintah find  
![Step 1](img/11.png "Step1")  
2.Perintah which  
![Step 2](img/12.png "Step2")  
3.Perintah locate  
![Step 3](img/13.png "Step3")

### **Percobaan 6: Mencari text pada file**
**Hasil:**   
![Step 1](img/14.png "Step1")

### **Latihan:**
1. **Cobalah urutan perintah berikut :** 
   ![Step 1](img/15.png "Step1")

2. **Lanjutkan penelusuran pohon pada sistem file menggunakan cd, ls, pwd dan cat. Telusuri direktory /bin, /usr/bin, /sbin, /tmp dan /boot.** 
   ![Step 2](img/16.png "Step2")

3. **Telusuri direktory /dev. Identifikasi perangkat yang tersedia. Identifikasi tty (termninal) Anda (ketik who am i); siapa pemilih tty Anda (gunakan ls –l).** 
   ![Step 3](img/17.png "Step3")

4. **Telusuri derectory /proc.  Tampilkan isi file interrupts, devices,
cpuinfo, meminfo dan uptime menggunakan perintah cat.  Dapatkah Anda
melihat mengapa directory /proc disebut pseudo -filesystem  yang memungkinkan akses ke struktur data kernel ?** 
   ![Step 4](img/18.png "Step4")

5. **Ubahlah direktory home ke user lain secara langsung menggunakan cd ~username.** 
   ![Step 5](img/19.png "Step5")

6. **Ubah kembali ke direktory home Anda.** 
   ![Step 6](img/20.png "Step6")

7. **Buat subdirektory work and play.** 
   ![Step 7](img/21.png "Step7")

8. *Hapus subdirektory work.** 
   ![Step 8](img/22.png "Step8")

9. **Copy file /etc/passwd ke direktory home Anda.** 
   ![Step 9](img/23.png "Step9")

10. **Pindahkan ke subdirektory play.** 
   ![Step 10](img/24.png "Step10")

11. **Ubahlah ke subdirektory play dan buat symbolic link dengan nama terminal yang menunjuk ke perangkat tty.  Apa yang terjadi jika melakukan hard link ke perangkat tty ?** 
   ![Step 11](img/25.png "Step11")

12. **Buatlah file bernama hello.txt yang berisi kata ”hello word”.  Dapatkah Anda gunakan ”cp” menggunakan ”terminal” sebagai file asal untuk menghasilkan efek yang sama ?** 
   ![Step 12](img/26.png "Step12")

13. **Copy hello.txt ke terminal.  Apa yang terjadi ?** 
   ![Step 13](img/27.png "Step13")

14. **Masih direktory home, copy keseluruhan direktory play ke direktory bernama work menggunakan symbolic link.** 
   ![Step 14](img/28.png "Step14")

15. **Hapus direktory work dan isinya dengan satu perintah** 
   ![Step 15](img/29.png "Step15")