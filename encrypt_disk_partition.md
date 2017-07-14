
# Encrypt disk partition

Block device encryption. Everything written to the block device (here a partition) will be encrypted. When offline, it appears as big blob of random data. To read the data, the block device should be mounted in a specific way.
This explains how to achieve that using `dm-crypt`, the standard device mapper encryption facility provided by the linux kernel.

### encrypt partition
- setup a partition as an encrypted LUKS partition: 
`$ sudo cryptsetup -v luksFormat /dev/sdXX`  
- check result: 
`$ sudo cryptsetup luksDump /dev/sdXX`
- open and unlock partition: 
`$ sudo cryptsetup luksOpen /dev/sdXX <name>`  
- create file system: 
`sudo mkfs.ext4 /dev/mapper/<name>`

### open, unlock and mount partition
- open and unlock partition: 
`$ sudo cryptsetup luksOpen /dev/sdXX <name>`  
- mount: 
`$ sudo mount -t ext4 /dev/mapper/dataz /mnt/<name>`  

### unmount and close partition
- unmout: 
`$ sudo umount /mnt/<name>`  
- close and lock: 
`$ sudo cryptsetup close <name>`  
