## Clean install on the pi
 ### 1.prepare the pi
 - download raspbian (or other) image to flash on sdcard
 - make sure sd card is unmounted
 > $ unzip -p /path/to/zip/file | sudo dd of=/dev/sd* bs=4M status=progress conv=fsync
 - mount boot partition
 > $ sudo mount /dev/s** /mnt/raspboot
 - create an empty file called ssh in order to enable ssh at first boot
 > $ touch /mount/rapsboot/ssh
 
 ### 2.boot the pi
 - find the pi on the local network
 > $ nmap -sP <IPADDRESSES>
 - run rasp-config and configure whatever you may need to configure
 > $ rasp-config
 - do potential update
 > $ sudo apt-get update  
 $ sudo apt-get dist-upgrade
 - install pip for python2
 > $ sudo apt-get install python-pip
 - push up the volume
 > $ aslamixer
 
 ### 3.install mopidy
 - add key to repo list
 > $ wget -q -O - https://apt.mopidy.com/mopidy.gpg | sudo apt-key add -
 - add repo
 > $ sudo wget -q -O /etc/apt/sources.list.d/mopidy.list https://apt.mopidy.com/jessie.list
 - install mopidy
 > $ sudo apt-get mopidy
 - install mopidy-spotify
 > $ sudo pip install Mopidy-spotify
 - install spotipy 
 > $ sudo pip install spotipy
 - install mopidy-tunein
 > $ sudo pip install Mopidy-tunein
 
 ### 4. configure mopidy
 - edit configuration file for mopidy service 
 > $ vim /etc/mopidy/mopidy.conf  
  make sure the web server is reachable on your local network
  add spotify credentials
- enable mopidy service
> $ systemctl enable mopidy
- start mopidy
> $ systemctl start mopidy

 
 
