# Konfigurasi OpenCore untuk ThinkPad X1 Carbon Gen 5 (macOS Sequoia)

Repositori ini berisi folder EFI untuk instalasi macOS 15 Sequoia pada laptop **Lenovo ThinkPad X1 Carbon Generasi ke-5 (Kaby Lake)**. Konfigurasi ini dioptimalkan untuk fungsionalitas sehari-hari.

![ThinkPad X1 Carbon Gen 5](https://i.imgur.com/K0G31aE.jpeg) 

---

### **PENAFIAN (DISCLAIMER)**

Gunakan dengan risiko Anda sendiri. Saya tidak bertanggung jawab atas kehilangan data atau kerusakan apa pun yang mungkin terjadi pada perangkat keras Anda. Selalu buat cadangan (backup) data penting Anda sebelum mencoba.

---

### **Spesifikasi Perangkat Keras**

| Komponen | Model                                       |
|:--- |:--- |
| **Model** | Lenovo ThinkPad X1 Carbon (Generasi ke-5)     |
| **CPU** | Intel® Core™ i5-7300U (Kaby Lake)             |
| **GPU** | Intel® HD Graphics 620                      |
| **RAM** | 16GB DDR3                                   |
| **Penyimpanan** | NVMe SSD AGI                                 |
| **Audio Codec** | Realtek ALC298                              |
| **Wi-Fi / BT** | Intel® Dual Band Wireless-AC 8265           |
| **Layar** | 14" FHD (1920x1080)                         |

---

### **Versi Perangkat Lunak**

* **OpenCore:** `1.0.2`
* **macOS:** `macOS 15 Sequoia (Telah diuji pada versi ini)`

---

### **Status Fungsionalitas**

| Fitur | Status | Catatan |
|:--- |:---:|:--- |
| **Akselerasi Grafis** | ✅ | QE/CI berfungsi penuh. |
| **Audio** | ✅ | Speaker, headphone jack, dan mikrofon internal berfungsi. |
| **Wi-Fi** | ✅ | Menggunakan `itlwm.kext` + HeliPort. |
| **Bluetooth** | ✅ | Berfungsi. |
| **iService** | ✅ | Berfungsi. |
| **Port USB** | ✅ | Semua port USB-A dan USB-C berfungsi (dengan mapping). |
| **Keyboard** | ✅ | Berfungsi, termasuk backlight. |
| **Trackpad & TrackPoint** | ✅ | Berfungsi dengan gestur multi-touch. |
| **Manajemen Daya CPU** | ✅ | Berfungsi dengan baik untuk performa dan suhu optimal. |
| **Indikator Baterai** | ✅ | Berfungsi dengan akurat. |
| **Webcam** | ✅ | Berfungsi. |
| **Microphone** | ✅ | Berfungsi. |
| **Sleep Biasa (S3)** | ✅ | Berfungsi dengan baik (Suspend to RAM). |
| **Hibernasi (S4)** | ⚠️ | **Bermasalah.** Laptop berhasil hibernasi (mati total), namun saat dinyalakan kembali, BIOS menampilkan error **"CMOS Checksum Bad"**. Memerlukan perbaikan lebih lanjut dengan `SSDT-RTC0.aml`. |
| **AirDrop & Handoff**| ❌ | Tidak berfungsi karena menggunakan intel wifi (Gunakan Wifi card broadcom agar berfungsi) . |
| **Fingerprint Reader**| ❌ | **Tidak Berfungsi.** Tidak didukung oleh macOS. |
| **Card Reader** | ❌ | Kemungkinan tidak berfungsi. |
| **Thunderbolt 3** | ⚠️ | Berfungsi sebagai port USB-C. Fungsionalitas penuh Thunderbolt belum dikonfigurasi. |

---

### **Instalasi dan Penggunaan**

1.  **Salin Folder EFI:**
    * Salin seluruh folder `EFI` ini ke partisi EFI dari USB installer Anda atau drive utama Anda.

2.  **Reset NVRAM:**
    * Saat pertama kali boot dengan EFI ini, sangat disarankan untuk memilih **"Reset NVRAM"** pada menu boot OpenCore. Komputer akan restart sekali, lalu Anda bisa boot ke macOS.
    * Catatan: jika tidak ada menu reset nvram matikan opsi hideAuxulary pada config.plist

---

### **Catatan Penting**

* **Tentang Wi-Fi:** Dikarenakan intelwifi tida k mengupdate agar support macOS 15 maka kita gunakan `itlwm.kext` dan menggunakan aplikasi **HeliPort** untuk koneksi Wi-Fi.
* **Tentang Hibernasi:** Seperti yang disebutkan, hibernasi menyebabkan error CMOS. Solusi standar untuk ini adalah menambahkan `SSDT-RTC0.aml` atau mengaktifkan quirk `DisableRtcChecksum` di `config.plist`. Hal ini belum diterapkan dalam konfigurasi ini.

---

### **Kredit dan Terima Kasih**

Konfigurasi ini tidak akan mungkin terwujud tanpa kerja keras dari banyak orang di komunitas Hackintosh.
* **[@Acidanthera](https://github.com/acidanthera)** untuk OpenCore dan sebagian besar kext esensial.
* **[Dortania](https://dortania.github.io/getting-started/)** untuk panduan OpenCore yang sangat mendalam.
* Komunitas Hackintosh dan para developer untuk alat-alat bantu yang sangat berguna.