# **Laporan OS Pertemuan 3**

**Nama** : Akbar Bagus Wicaksana  
**NIM** : 254107020067  
**Kelas** : TI-1H  

---

### **Latihan 3.1**
**Buatlah Script yang:**  
1.Menampilkan daftar 10 file terbesar di direktori /var/log/  
2.Menyimpan hasilnya ke file large-logs.txt  
3.Menampilkan output juga di terminal menggunakan tee  
4.Menangani error dengan redirect ke error.logMemahami spesifikasi CPU dan kondisi memori pada server/VM.

**Hasil:**
   ![Step 1](img/1.png "Step1")

### **Latihan 3.2**
**Buat pipeline yang:**  
1.Membaca /etc/passwd  
2.Mengekstrak username (kolom pertama)  
3.Mengurutkan alfabetis  
4.Menyimpan ke file sorted-users.txt

**Hasil:**

   ![Step 2](img/2.png "Step2")

### **Latihan 3.3**
**Buat pipeline yang:**  
1.Mencatat penggunaan CPU dan memory setiap 5 detik  
2.Menyimpan log dengan timestamp  
3.Berjalan selama 1 menit (12 iterasi)  
4.Output ditampilkan di terminal dan disimpan ke file

**Hasil:**

   ![Step 3](img/3.png "Step3")

### **Latihan 3.4**
**Buat perintah yang:**  
1.Mencari semua file .conf di sistem  
2.Membuang pesan *Permission denied*  
3.Menghitung jumlah file yang ditemukan  
4.Menyimpan daftar path lengkap ke file

**Hasil:**

   ![Step 4](img/4.png "Step4")

### **Latihan 3.5**
**Implementasikan script backup yang:**  
1.Menggunakan tar untuk backup direktori  
2.Menampilkan progress dengan tee  
3.Mencatat stdout ke backup-success.log  
4.Mencatat stderr ke backup-error.log  
5.Menambahkan timestamp di setiap log entry

**Hasil:**

   ![Step 5](img/5.png "Step5")