# Hackintosh Legion Y530
<h2>💻 Specifications :</h2>

| Device Hardware  | Name |
| ------------- | ------------- |
| Processor : | Intel Core i5 8300H |
| IGPu : | Intel UHD Graphics 630 |
| RAM : | 8GB SK Hynix DDR4 |
| Storage : | 1 x SSD M.2 NVME 512GB |
|  | 1 x HDD Toshiba 500 GB |
|  | 1 x SSD WD Green SATA 120GB (Removeable) |
| Wifi : | Intel AC 9560 |
| Ethernet : | Realtek 8111 |
| Audio : | Realtek ALC236 |
| Touchpad : | Elan I2C HID Controller |
| Screen Size : | 15" |
| Display Resolution : | FHD (1920x1080) |
| OS Version : | macOS Catalina 10.15.7 Build 19H1311 (Latest) |
|  | macOS BigSur 11.3.1 Beta |

# Disclaimer
> [!CAUTION]
> Apabila terdapat kerusakan di Laptop anda bukan tanggung jawab saya. Saya hanya membuat EFI dari sumber yang ada dan membagikan EFI ini sebagai patokan dasar dalam pembuatan EFI laptop yang memiliki spesifikasi yang sama.
> Apabila ada yang kurang jelas dapat menghubungi saya di [Telegram](t.me/frtsnts10). Terimakasih.

# Bootloader
> [!NOTE]
> Bootloader yang dipakai pada OS Catalina adalah Clover Build 5137.
> Bootloader yang dipakai pada BigSur adalah OC 0.7.0.

# Settingan BIOS (Advanced BIOS)
<h2>Required BIOS Configration :</h2>

| BIOS Settings  | |
| ------------- | ------------- |
| Boot Mode : | UEFI |
| Storage Mode : | AHCI |
| Kernel Debug Serial Port : | Legacy UART |
| | Advanced -> Debug settings -> Legacy UART |
| CFG Lock (MSR_E2) : | Disabled |
|  | Advanced -> Power & Performance -> CPU - Power Management -> View/Configure CPU Lock Options -> CFG Lock |
| DVMT Pre-Allocated Memory : | 64 MB |
|  | Advanced -> System Agent (SA) Configuration -> Graphics Configuration -> DVMT Pre-Allocated Memory |
 
# CATATAN
> [!TIP]
> - Di setiap Folder ACPI terdapat SSDT-DNVME, itu karena NVME yang saya pakai adalah PM-981.
> - SSDT-DGPU karena NVIDIA GTX 1050 tidak bisa digunakan di macOS Seri Catalina keatas.
> - Untuk <b> SSDT-NVME dan SSDT-DDGPU <b> adalah hasil saya ambil dari repo [xiaoMGithub](https://github.com/xiaoMGitHub/LEGION_Y7000Series_Hackintosh) <b>
> - <b>UNTUK YANG TIDAK MENGGUNAKAN PM-981 SILAHKAN DIHAPUS SAJA. <b> TERIMAKASIH.

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
- Numpad

# Credits
- [Apple](https://www.apple.com) for macOS.
- [Acidanthera](https://github.com/acidanthera) untuk kexts yang disediakan.
- [Hackintosh Lovers](https://t.me/HackintoshLover) sebagai tempat awal mula EFI ini dapat terbentuk.
- [chilledHamza](https://github.com/chilledHamza) sebagai contoh panduan dalam pembuatan EFI.
- [xiaoMGithub](https://github.com/xiaoMGitHub/LEGION_Y7000Series_Hackintosh) sebagai contoh panduan dalam pembuatan EFI.
- Dan semua pihak yang tidak bisa saya sebutkan satu per satu.
