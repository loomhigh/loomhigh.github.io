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

### Owned Devices
``` Found the device info by plugging device into PC, typing in 'adb shell' and then 'getprop'. Codename is found at 'ro.product.name'```
- ZTE Telstra Dave T83
    - VENDOR: ZTE
    - CODENAME: P893A30
        - ZTE-Demeter??
    - ARCHITECTURE: armv7
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD:

- ZTE Blade A602
    - VENDOR: ZTE
    - CODENAME: P637F02
        - TLS_AU_P637F02
    - ARCHITECTURE: armv7l
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD: META MODE??

- Samsung Galaxy J5 Pro
    - VENDOR: Samsung
    - CODENAME: j5y17ltedx
      - MODEL: SM-J530Y
    - ARCITECTURE: armv8l
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD: Has odin?
    - NOTES: Stuck in an updating bootloop

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
    - VENDOR: Samsung
    - CODENAME: klte dv
    - ARCITECTURE: armv7
    - TYPE: handset
    - SD_CARD: YES
    - FLASH_METHOD:
    - NOTES: uses old charger