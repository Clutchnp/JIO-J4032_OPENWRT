This repo contains the openwrt builds for Jio J4032 router

- You would have to flash the trx file to the trlinux mtd by copying over the file to the router via xmdm or from the stock firmware using mtd

- The system boots with overlayfs mounted on tmpfs, because it cant find the UBI device you have to 
```
ubiformat /dev/mtd4 -y
ubiattach /dev/ubi_ctrl -m 4
ubimkvol /dev/ubi0 -N rootfs_data -m
reboot
```
you have to run the above commands once flashing is complete to mount overlayfs on ubifs, this would make the filesystem persistant

- currently you have to bring up the radios by yourself after booting into openwrt


- This is still work in progress so expect things to break


- I dont take responsibility for anything that might happen to your property while using this, Pls be careful as this may lead to brick ("I only suggest doing this if youare able to get into your router via UART connection, if anything goes south")


The mt76 drivers do work but the speeds are very slow, I am currently working on fixing the issue (related to how eeprom is interprted by the openwrt's mt76 driver)

