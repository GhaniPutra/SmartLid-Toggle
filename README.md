# SmartLid Toggle

SmartLid Toggle adalah script sederhana untuk menyalakan dan mematikan mode "Ignore Lid Close" pada Ubuntu.  
Cocok untuk pengguna laptop yang memakai monitor eksternal dan ingin mengontrol fungsi lid tanpa restart atau mengedit file sistem berulang kali.

---

## ✨ Fitur
- Toggle cepat: aktif/nonaktif hanya dengan shortcut keyboard  
- Memberi notifikasi status menggunakan `notify-send`  
- Tidak mengubah sistem secara permanen  
- Bekerja di Ubuntu GNOME

---

## 📦 Instalasi

### 1. Edit `logind.conf`
Ubuntu butuh ini agar mode toggle bisa berjalan.

```bash
sudo nano /etc/systemd/logind.conf
````

Hilangkan tanda `#` (uncomment) pada baris-baris berikut:

```
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

Simpan, lalu reload:

```bash
sudo systemctl restart systemd-logind
```

---

### 2. Install dependency `notify-send`

```bash
sudo apt install libnotify-bin
```

---

### 3. Pasang script

Copy file `laptop-mode-toggle` ke:

```
sudo cp laptop-mode-toggle /usr/local/bin/laptop-mode-toggle
```

Lalu beri permission agar bisa dieksekusi:

```bash
sudo chmod +x /usr/local/bin/laptop-mode-toggle
```

---

### 4. Tambahkan Shortcut GNOME

Buka:

**Settings → Keyboard → View and Customize Shortcuts → Custom Shortcuts**

Buat shortcut baru:

* **Name:** SmartLid Toggle
* **Command:** `/usr/local/bin/laptop-mode-toggle`

Pilih tombol shortcut sesuai selera (misal: `Ctrl + F12` atau `Ctrl + Super + L`).

---

## 🚀 Cara Pakai

Tekan shortcut → mode Ignore Lid akan berubah (ON ↔ OFF).
Sebuah notifikasi akan muncul sebagai konfirmasi.

---

## ❌ Uninstall

Hapus script:

```bash
sudo rm /usr/local/bin/laptop-mode-toggle
```

Kembalikan setting logind ke default bila perlu:

```bash
sudo nano /etc/systemd/logind.conf
```

Lalu restart service:

```bash
sudo systemctl restart systemd-logind
```
