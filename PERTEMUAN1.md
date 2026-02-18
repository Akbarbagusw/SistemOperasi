# **Laporan OS Pertemuan 1**

**Nama** : Akbar Bagus Wicaksana
**NIM** : 254107020067
**Kelas** : TI-1H

---

## **1.10.1. Latihan Konseptual**

### **Latihan 1.1**

Jelaskan 5 fungsi utama sistem operasi dengan contoh konkret dari minimal 2 OS berbeda (Windows, macOS, atau Linux).

---

### **Jawaban Latihan 1.1**

### **1. Manajemen Proses**

Mengatur aplikasi atau proses yang berjalan serta penggunaan CPU.

**Contoh konkret:**

* **Windows**: Task Manager digunakan untuk mematikan paksa (*End Task*) aplikasi yang macet atau *hang*.
* **Linux**: Perintah `kill` di terminal digunakan untuk menghentikan proses tertentu yang membebani sistem.

---

### **2. Manajemen Memori**

Mengatur pembagian RAM agar banyak aplikasi dapat berjalan secara bersamaan tanpa konflik.

**Contoh konkret:**

* **Windows**: Menggunakan *virtual memory* berupa `pagefile.sys` ketika RAM fisik penuh.
* **macOS**: Menggunakan fitur *Memory Compression* untuk memadatkan data di RAM sehingga performa tetap optimal tanpa sering memakai disk.

---

### **3. Manajemen File**

Mengatur cara data disimpan, diberi nama, dan diorganisir dalam folder.

**Contoh konkret:**

* **Windows**: Menggunakan sistem huruf drive (C:, D:) dengan format file seperti NTFS.
* **Linux**: Menggunakan struktur direktori berbentuk pohon tunggal yang dimulai dari root (`/`) tanpa huruf drive.

---

### **4. Manajemen Perangkat (I/O Device)**

Menjembatani komunikasi antara perangkat lunak dengan perangkat keras seperti printer, mouse, dan WiFi.

**Contoh konkret:**

* **Windows**: Fitur *Plug and Play* otomatis mendeteksi perangkat baru dan menginstal driver.
* **macOS**: Sistem audio *CoreAudio* yang stabil dan memiliki latensi rendah, sangat cocok untuk produksi musik tanpa konfigurasi driver rumit.

---

### **5. Antarmuka Pengguna (User Interface)**

Media interaksi antara pengguna dengan komputer, baik visual maupun berbasis teks.

**Contoh konkret:**

* **Windows / macOS**: Menggunakan GUI (ikon, jendela, dan mouse) yang mudah dipahami pengguna awam.
* **Linux (Server)**: Sering menggunakan CLI (Command Line Interface) karena lebih ringan, cepat, dan efisien untuk pengelolaan server.