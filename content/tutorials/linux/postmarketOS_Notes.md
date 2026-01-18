---
title: Notes on pmOS Projects
---
### Issues

#### PMbootstrap on nixOS failing

I have installed pmbootstrap on my nixOS machine using uv. When I attempt to flash a kernel I am met with the error:
```
sudo ln -s usr/bin usr/sbin usr/lib /home/personal/Files/Documents/pmOS/pmbootstrap/chroot_native/
```

Very odd given it is being run as Sudo.
- current theory: Because my documents folder is symbolically linked separate hard drive with a different file format. 
    - THIS WAS CORRECT! Make sure the file format of the drive you are working with is appropriate. The work folder can be whenever but the repository folder cannot!
`` pmbootstrap: Needs to be on linkable hard drive ``
`` pmaports: can be anywhere ``

### Heimdall TWRP

I installed lineageOS on an old samsung galaxy S8 that I intend to keep as a backup phone (I have had my pixel 6 for a very very long time and am sure it will break soon enough) and in that process discovered what TWRP is and how to put it on samsung devices using heimdall on Linux.

#### What is TWRP?
Stands for ["Team Win Recovery Project"](https://en.wikipedia.org/wiki/TWRP_(software))
in a nutshell its a boot menu created by [TeamWin](https://twrp.me/about/). You flash it on to your samsung device, and the default boot menu (called recovery mode) is replaced with a more feature-rich one that somewhat reminds me of an MSI motherboards BIOS menu.
  
They can make flashing custom Versions of Android or other operating systems like PostmarketOS a lot easier, though I found it initially difficult to figure out.
  
#### Installing TWRP
I initially installed TWRP on a [samsung galaxy S8](https://vijayprema.com/installing-lineageos-on-my-old-galaxy-s8/), but was not taking notes. I will be installing it on my S4 while writing these instructions.
##### 1. Get into download mode
- Ensure OEM unlocking is enabled in developer options
- Turn off your device
- Enter download mode, typically by holding the power, volume down, and home/bixby buttons.
- typically a warning appears, and you can enter download mode by pressing the volume up key.

##### 2. Heimdall flash
- connect your phone to your computer **after** entering download mode (sometimes there is an initialisation error if you plug it in before)
- download the right twrp file from the teamwin website (Can usually get the right one by typing the type of phone I have and 'TWRP' into google)
- open terminal in the folder with the TWRP file and type the following command:
``heimdall flash --RECOVERY [TWRP_FIlename]``
- on my arch device I didn't need to use sudo, but due to some lsusb error I needed to use sudo on my nixOS machine.
  
There you have it, once you boot into recovery mode you will have a nice funky new boot menu.

### Owned Devices
``` Found the device info by plugging device into PC, typing in 'adb shell' and then 'getprop'. Codename is found at 'ro.product.name'```

command to get all info:
````echo -n "| manufacturer = "; getprop ro.product.brand; echo -n "| name = "; getprop ro.product.nickname; echo -n "| codename = "; echo "$(getprop ro.product.brand)-$(getprop ro.product.device)"; echo "| image = "; echo -n "| imagecaption = image of a "; getprop ro.product.model; echo "| releaseyear = "; echo "| originalsoftware = Android"; echo -n "| originalversion = "; getprop ro.build.version.base_os; echo -n "| extendedversion = "; getprop ro.build.version.release; echo -n "| chipset = "; getprop ro.chipname; echo -n "| cpu = "; getprop dalvik.vm.isa.arm.variant; echo "| gpu = "; echo "| storage = "; echo "| display ="; echo "| memory = "; echo -n "| architecture = "; getprop ro.product.cpu.abi; echo "| type = "; echo "| category = "; echo "| pmoskernel ="; ````

The command uses echo and getprop commands to format and grab the right info from the connected device, with the -n removing newlines for neatness.

- ZTE Telstra Dave T83
| manufacturer = ZTE
| name = 
| codename = ZTE-demeter (P893A30)
| image = 
| imagecaption = image of a ZTE T83
| releaseyear = 
| originalsoftware = Android
| originalversion = 
| extendedversion = 4.1.2
| chipset = 
| cpu = 
| gpu = 
| storage = 
| display =
| memory = 
| architecture = armeabi-v7a
| type = 
| category = 
| pmoskernel =

- ZTE Blade A602
    - VENDOR: ZTE
    - CODENAME: P637F02
        - TLS_AU_P637F02
    - ARCHITECTURE: armv7l
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD: META MODE??

- Samsung Galaxy J5 Pro
| manufacturer = samsung
| name = J5 Pro
| codename = samsung-j5y17ltedx
| image = 
| imagecaption = image of a SM-J530Y
| releaseyear = 
| originalsoftware = Android
| originalversion = 
| extendedversion = 9
| chipset = 
| cpu = cortex-a15
| gpu = 
| storage = 
| display =
| memory = 
| architecture = armeabi-v7a
| type = 
| category = 
| pmoskernel =


- Samsung Galaxy S6 edge
    - VENDOR: Samsung
    - CODENAME: zeroltedv
        - SM-G925I
    - ARCITECTURE: arm64v8
    - SD_CARD: [TOTEST]
    - FLASH_METHOD: [TOTEST]
    - NOTES: Chipped but functioning screen

- Ulefone Armor 2
    - VENDOR: Ulefone
    - CODENAME: Armor_2
    - ARCITECTURE: arm64v8
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD: [TOTEST]
    - NOTES: Chipped but functioning screen

- Samsung Galaxy S7
    - VENDOR: Samsung
    - CODENAME: samsung-herolte
    - ARCITECTURE: arm64v8
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD: [TOTEST]
    - NOTES: *sniff* *sniff* I used to use this phone before the shutdown.

- thorn thot61
    - VENDOR: Thorn
    - CODENAME: thot61
    - ARCITECTURE: armv7
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD: [TOTEST]
    - NOTES: mysterious lack of details  

- ZTE T815
    - VENDOR: ZTE
    - CODENAME: P172R10
    - ARCITECTURE: armv7
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD:
    - NOTES: 

- Samsung Galaxy Trend Plus S7583t
    - VENDOR: samsung
    - CODENAME: kyleprodv
    - ARCITECTURE: armv7
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD:
    - NOTES: very small, very buggy

- Samsung Galaxy S4
    - VENDOR: samsung
    - CODENAME: jflte
    - ARCITECTURE: armv7
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD:
    - NOTES: gnome resulted in a black screen on boot
        - wiki says best to use xfce first, so gonna try that next.
            - this seems to have failed 11/01/2026

- Samsung Galaxy S5
| manufacturer = samsung
| name = Galaxy S5
| codename = samsung-klte
| image = 
| imagecaption = image of a SM-G900I
| releaseyear = 
| originalsoftware = Android
| originalversion = 4.4.2
| extendedversion = 6.0.1
| chipset = Qualcomm Snapdragon 801 (MSM8974PRO)
| cpu = krait
| gpu = 
| storage = 
| display =
| memory = 
| architecture = armeabi-v7a
| type = 
| category = 
| pmoskernel =
NOTES: uses old charger

- Samsung Galaxy Tab S
    - VENDOR: Samsung
    - CODENAME: chagallwifixx
    - ARCITECTURE: armeabi-v7a,armeabi
    - TYPE: tablet
    - SD_CARD: YES
    - FLASH_METHOD:
    - NOTES: