# Hackintosh-Legion-Y530

💻 Specifications :
- Processor : Intel Core i5 8300H
- IGPU : Intel UHD Graphics 630
- RAM : 8GB SK Hynix DDR4
- Storage : 1x SSD M.2 NVME 512GB + 1x SSD WD Green SATA 120GB
- Wifi : Intel AC 9560
- Ethernet : Realtek 8111 
- Audio : Realtek ALC236 
- Touchpad : Elan I2C HID Controller
- Screen Size : 15”
- Display Resolution : FHD (1920x1080)
- OS Version : 
  - macOS Catalina 10.15.7 Build 19H1311 (Latest) 
  - macOS BigSur 11.3.1 Beta

# Bootloader
Bootloader yang dipakai pada OS Catalina adalah Clover Build 5137, sedangkan pada BigSur adalah OC 0.7.0

# Settingan BIOS (Advanced BIOS)
Required BIOS Configration
- Boot Mode: UEFI
- Storage Mode: AHCI
- Secure Boot : Disabled
- Kernel Debug Serial Port : Legacy UART (Advanced -> Debug settings -> Legacy UART)
- CFG Lock (MSR_E2) : Disabled (Advanced -> Power & Performance -> CPU - Power Management -> View/Configure CPU Lock Options -> CFG Lock)
- DVMT Pre-Allocated Memory : 64MB (Advanced -> System Agent (SA) Configuration -> Graphics Configuration -> DVMT Pre-Allocated Memory)
 
# Disclaimer
Apabila terdapat kerusakan di Laptop anda bukan tanggung jawab saya, saya hanya membagikan EFI ini sebagai patokan dalam pembuatan EFI laptop yang sama spesifikasi nya. Apabila ada yang kurang jelas dapat menghubungi saya di telegram : Chou_10. Terimakasih.

# CATATAN
- Di setiap Folder ACPI terdapat SSDT-DNVME, itu karena NVME yang saya pakai adalah PM-981.
- SSDT-DGPU karena NVIDIA GTX 1050 tidak bisa digunakan di macOS Seri Catalina keatas.
- Untuk <b> SSDT-NVME dan SSDT-DDGPU <b> adalah hasil saya ambil dari repo xiaoMGithub <b>
- <b>UNTUK YANG TIDAK MENGGUNAKAN PM-981 SILAHKAN DIHAPUS SAJA. <b> TERIMAKASIH.

# What's Work??
- QE/CI Graphics Intel UHD 630
- CPU Power Management
- Restart, Sleep and Shutdown
- Internal Speaker, Headphone and Internal Microphone
- Wifi + Bluetooth 
- Touchpad
- Brightness (FN + Brightness Up / Down, FN + K / P)
- Ethernet
- Battery Indicator
- All USB Port

# Not Work??
- External GPU (NVIDIA GTX1050), disabled.
- HDMI Port

# Credits
- [Apple](https://www.apple.com) for macOS.
- [Acidanthera](https://github.com/acidanthera) untuk kexts yang disediakan.
- [Hackintosh Lovers](https://t.me/HackintoshLover) sebagai tempat awal mula EFI ini dapat terbentuk.
- [chilledHamza](https://github.com/chilledHamza) sebagai contoh panduan dalam pembuatan EFI.
- [xiaoMGithub](https://github.com/xiaoMGitHub/LEGION_Y7000Series_Hackintosh) sebagai contoh panduan dalam pembuatan EFI.
- Dan semua pihak yang tidak bisa kami sebutkan satu per satu.
