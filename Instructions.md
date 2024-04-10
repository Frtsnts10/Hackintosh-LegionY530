<h2>Instalation (Catalina)</h2>

1. Pilih config2 di Clover GUI
2. Format Disk -> APFS & GUID partition
> [!NOTE]
> Apabila gagal saat selesai Format Disk, ubah tanggal melalui bios ke 09/27/2019.
3. Install seperti biasa dan tunggu sampai restart sendiri.
4. Kemudian pencet F12 pilih config, kemudian pilih <b> Boot MacOS Catalina from MacOS Catalina</b>, bukan dari MacOS Catalina Installer.
5. Tunggu sampai instalasi selesai.
6. Kemudian pilih <b>Boot MacOS from  nama `driver` kita.
7. Lanjutkan setting sampai selesai.
8. Mount EFI menggunakan ESP Mounter Pro (File ada dalam Logo Apple : `Double click icon 'Install MacOS Catalina', kemudian ke Files, ESP Mounter Pro`).
9. Klik Icon ESP di taskbar atas, pilih `Mount EFI Disk`.
10. Drag n Drop EFI di Folder USB ke EFI Disk.
11. `config.plist` pada EFI Disk dihapus, `config2.plist` rename jadi `config plist`.
12. Selesai.

<h2>Instalation (Big Sur)</h2>

1. Pada OC GUI, pilih `Boot MacOS Installer` (biasanya urutan ke 2)
2. Format Disk -> APFS & GUID partition
3. install sprti biasa, akan auto restart sebanyak 2x, ketika restart, pilih mac os big sur (bkn installer lagi), kedua kali pilih nama driver disk (misal : driver ‘BigSur’)
4. setting up seperti biasa dan selesai
5. kemudian mount efi menggunakan esp mounter pro (file ada dalam logo apple : install mac os Big Sur, kemudian ke files, esp mounter pro)
6. pencet logo esp di taskbar atas, mount efi disk.
7. efi folder di usb di copy paste ke efi disk,
8. selesai

<h2>Patching (Clover)</h2>

| Patching  |  |
| ------------- | ------------- |
| VGA | Buka `config.plist` via Configurator |
| | Pilih menu device -> Properties, List PCI -> pilih VGA |
| | Di bawah kanan `Model` -> `Preset` -> `Mojave & Above` |
| | Saat muncul pop-up pilih Platform dan Device sesuai ID |
| | Masukkan FrameBuffer : `patch enable(1)`, stolenmen : `00003001`, fbmem : `00009000` |
| | Save dan restart |
| DSDT | `F4` dan `Fn+F4` di Bootloader. |
| | Boot ke MacOS Catalina |
| | Mount `EFI`, keluarkan File `Origin` dari folder |
| | File pada Folder Patched dihapus semua |
| | Download [SSDTTime](https://github.com/corpnewt/SSDTTime), Drag n Drop File `dsdt.aml` dari dalam folder `origin` |
| | pilih 1,3,4,5,6,7 kemudian enter, ke file result |
| | pilih file .aml saja masukan ke folder patched. |
| | Download [ProperTree](https://github.com/corpnewt/ProperTree) |
| | buka config.plist copy paste patched config (sesuaikan jika oc, ya oc pny, begitu sebaliknya) ke config.plist di efi |


6.  
7. 
8. 
9. centang fixregion dan fix mutex 
10. save dan reboot.

====================================================

OpenCore
DSDT :
1. download dcpi manager
2. open
3. klik extract dsdt 
4. selesai

SSDT-Time:
1. download ssdttime (ada di github)
2. run .cmd / .bat 
3. pencet D utk drag and drop dsdt.aml
4. drag and drop, enter
5. klik 1 dan enter , 2 (utk pc), 3 (utk laptop) dan seterusnya kemudian enter (1 per 1)
6. cek result, ambil hasil .aml masukkan ke acpi
7. buka config plist dan patched.plist , copy kan hasil patched.plist ke config.plist
8. save config.plist dan reboot 

——————————————————————————————————————

Cleaning up folder efi:
1. sesuaikan kext dengan spek, yang tdk perlu dihapus.

Fix Touchpad: 
1. download voodooi2c (ambil i2chid + vodooi2c)
2. force enable GPIO ( advance BIOS)

Mapping USB + Sleep :
1. Colokin FD satu ke tiap portnya, nanti pasti ada port HSxx yg ngedetect (cirinya, di kolom device akan kluar sesuatu)
2. Catat semua HSxx yg ngerespon.
3. Jika tidak punya USB peripheral yg USB3, kita pakai "kira-kira" (tapi biasanya HS sama SS align).
4. Dari HSxx yg nyala tadi, kita anggap SSxx yg nyala akan diposisi yg sama. Misal, klo HS01 nyala, berarti pasangannya SS01 dan seterusnya. Nah, ke 6 port ini kolom Connectornya di set seperti ini : 
		- kalau HSxx = connector USB2
		- kalau SSxx = connector USB3
5. Dan waktu USBC di colok, perlakuannya juga sama, karena port C non Thunderbolt, pasti punya 2 persona (HS dan SS), Hanya bagian Connectornya di ganti jadi TypeC
6. Jangan lupa juga set ini : 
		- HS06 = Connector Internal
		- HS14 = Connector Internal
7. Selesai. dan export.

Kalau ini udah selesai, hasil Export ada SSDT sama Kext, pilihan pasangnya : 
1. pakai Kext saja, delete kext USBInjectAll, Xhciunsuported, FALSE quirk XHCIportlimit
2. pakai SSDT UIAC, delete kext Xhciunsuported, FALSE quirk Xhciportlimit.
3. Reboot, cek hasilnya di Hackintool.
