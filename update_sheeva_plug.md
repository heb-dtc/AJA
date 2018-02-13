## Sheevaplug update procedure

### serial access to the sheevaplug
- plug the sheeva via USB to the host machine
> screen /dev/ttyUSB* 115200

### flashing uboot
- start a tftp server on host machine
> systemctl start tftp.service
- copy the bootloader to the tftp server
> setenv serverip 192.168.1.2 # IP of TFTP server  
  setenv ipaddr 192.168.1.200 # IP of the sheevaplug  
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
