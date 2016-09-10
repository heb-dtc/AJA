Load virtualbox custom kernel module on ArchLinux

1. install virtualbox-host-modules package
sudo pacman -S virtualbox-host-modules
2. load the 4 modules 
sudo modprobe vbox*
