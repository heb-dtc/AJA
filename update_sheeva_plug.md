## Sheevaplug update procedure

### serial access to the sheevaplug
- plug the sheeva via USB to the host machine
```bash
screen /dev/ttyUSB* 115200
```

### flashing uboot
- start a tftp server on host machine
```bash
systemctl start tftp.service
```
- copy the bootloader to the tftp server public directory
- push the image on the sheevaplug internal memory
```bash
setenv serverip <IP of TFTP server>
setenv ipaddr <IP of the sheevaplug>  
tftpboot 0x0800000 u-boot.kwb # copy the bootloader img
```

- write the bootloader
```bash
nand erase 0x0 0x80000  
nand write 0x0800000 0x0 0x80000  
```

- restart
```bash
reset  
```

- write mac address
```bash
setenv ethaddr <MACADDR>  
saveenv  
reset 
```

### flashing debian
- copy the uImage and the uInitrd to the tftp server public directory
- push the images on the sheevaplug internal memory
```bash
setenv serverip <IP of TFTP server>  
setenv ipaddr <IP of the sheevaplug>    
tftpboot 0x00800000 uImage  
tftpboot 0x01100000 uInitrd  
```

 - start the installer
```bash
setenv bootargs console=ttyS0,115200n8 base-installer/initramfs-tools/driver-policy=most  
bootm 0x00800000 0x01100000
```

### references
- http://ftp.debian.org/debian/dists/stretch/main/installer-armel/current/images/kirkwood/u-boot/sheevaplug/
- http://ftp.debian.org/debian/dists/stretch/main/installer-armel/current/images/kirkwood/netboot/marvell/sheevaplug/
- https://www.cyrius.com/debian/kirkwood/sheevaplug/uboot-upgrade/
- https://www.cyrius.com/debian/kirkwood/sheevaplug/install/
 
