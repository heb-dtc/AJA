### Install ArchLinux with UEFI boot mode

1. get latest arch linux ISO and write it on usb stick  
> $ dd if=/path/to/iso/file of=/dev/sdx bs=1M && sync

2. boot on the usb stick
> might have to disable secure boot in the BIOS  
  $ loadkeys fr-pc

3. wipe the existing data and create new partition 

- create partition using `parted`  
> $ parted  
  (parted) mklabel gpt  
  (parted) mkpart ESP fat32 1MiB 513MiB  
  (parted) set 1 boot on  
  (parted) mkpart primary ext4 513MiB 20GiB  
  (parted) mkpart primary linux-swap 20GiB 28GiB  
  (parted) mkpart primary ext4 28GiB 100%  
  (parted) q   
  
- format the newly created partition  
>  $ mkfs.fat -F32 /dev/sdx1  
  $ mkfs.ext4 /dev/sdx2  
  $ mkswap /dev/sdx3  
  $ swapon /dev/sdx3  
  $ mkfs.ext4 /dev/sdx4  
  
4. mount the file system  
> $ mount /dev/sdx2 /mnt  
  $ mmkdir /mnt/boot  
  $ mount -t vfat /dev/sdx1 /mnt/boot  
  $ mkdir /mnt/home  
  $ mount /dev/sdx4 /mnt/home  
  
5. install base system  

- plug ethernet cable or configure wifi
>$ wifi-menu  

- proceed to installation  
>$ pacstrap /mnt base base-devel  
  
