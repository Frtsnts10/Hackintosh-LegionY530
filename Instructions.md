Tutorial Y530 (Indonesian)

Preparation :
Required BIOS Configration
 • Boot Mode: UEFI
 • Storage Mode: AHCI
 • Secure Boot : Disabled
 • Kernel Debug Serial Port : Legacy UART 
 • Advanced -> Debug settings -> Legacy UART
 • CFG Lock (MSR_E2) : Disabled 
 • Advanced -> Power & Performance -> CPU - Power Management -> View/Configure CPU Lock Options -> CFG Lock
 • DVMT Pre-Allocated Memory : 64MB 
 • Advanced -> System Agent (SA) Configuration -> Graphics Configuration -> DVMT Pre-Allocated Memory

—————————————————————————————————————

Instalation (Catalina) 
1. pilih config2 di clover gui
2. format disk -> apfs & GUID partition
3. apabila gagal  waktu slsai format disk, ubah tanggal melalui bios (09272019)
4. install sprti biasa, akan auto restart kemudian pencet f12 pilih config, kemudia pilih boot mac os catalina from ‘mac os catalina, bkn mac os catalina installer’.
5. kemudian menyelesaikan instalation.
6. auto restart, pilih boot mac os from ‘nama driver kita’
7. setting up dan selesai
8. kemudian mount efi menggunakan esp mounter pro (file ada dalam logo apple : install mac os catalina, kemudian ke files, esp mounter pro)
9. pencet logo esp di taskbar atas, mount efi disk.
10. efi folder di usb di copy paste ke efi disk,
11. kemudian config plist pada efi disk dihapus, config2.plist rename jadi config plist.
12. selesai


=====================================================

Instalation (Big Sur)
1. di OC GUI, pilih boot mac os installer (biasanya urutan ke 2)
2. format disk -> apfs & GUID partition
3. install sprti biasa, akan auto restart sebanyak 2x, ketika restart, pilih mac os big sur (bkn installer lagi), kedua kali pilih nama driver disk (misal : driver ‘BigSur’)
4. setting up seperti biasa dan selesai
5. kemudian mount efi menggunakan esp mounter pro (file ada dalam logo apple : install mac os Big Sur, kemudian ke files, esp mounter pro)
6. pencet logo esp di taskbar atas, mount efi disk.
7. efi folder di usb di copy paste ke efi disk,
8. selesai


——————————————————————————————————————
Clover
Patching:
VGA:
1. buka config.plist via configurator
2. ke menu device -> properties, terus list pci -> pilih VGA. 
3. Klik kanan di bwh model -> preset -> mojave above
4. ketika pop up pilih platform dan device sesuai ID. 
5. Kemudian tmbh framebuffer patch enable(1), stolenmen(00003001), fbmen(00009000)
6. save dan reboot. 

DSDT:
1. F4 dan Fn+F4 di bootloader.
2. boot ke catalina
3. mount efi, file origin pindah keluar dr efi, 
4. file patched dihapus semua 
5. download ssdttime, drag and drop file dsdt.aml dri dlm folder origin , klik 1,3,4,5,6,7 kemudian enter, ke file result 
6. pilih file .aml saja masukan ke folder patched. 
7. download propertree 
8. buka config.plist copy paste patched config (sesuaikan jika oc, ya oc pny, begitu sebaliknya) ke config.plist di efi
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
