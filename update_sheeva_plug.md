## Sheevaplug update procedure

### serial access to the sheevaplug
- plug the sheeva via USB to the host machine
> screen /dev/ttyUSB* 115200

### flashing uboot
- start a tftp server on host machine
> systemctl start tftp.service
- copy the bootloader to the tftp server public directory
- push the image on the sheevaplug internal memory
> setenv serverip <IP of TFTP server>
  setenv ipaddr <IP of the sheevaplug>  
  tftpboot 0x0800000 u-boot.kwb # copy the bootloader img

- write the bootloader
> nand erase 0x0 0x80000  
 nand write 0x0800000 0x0 0x80000  
 
- restart
> reset  

- write mac address
> setenv ethaddr <MACADDR>  
 saveenv  
 reset  

### flashing debian
- copy the uImage and the uInitrd to the tftp server public directory
- push the images on the sheevaplug internal memory
> setenv serverip <IP of TFTP server>  
 setenv ipaddr <IP of the sheevaplug>    
 tftpboot 0x00800000 uImage  
 tftpboot 0x01100000 uInitrd  
 
 - start the installer
 > setenv bootargs console=ttyS0,115200n8 base-installer/initramfs-tools/driver-policy=most  
 bootm 0x00800000 0x01100000
