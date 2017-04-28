### Mopidy configuration

1. install mopidy
2. install a front for it (moped i.e.)
3. install spotify plugin
4. add spotify block in config file at `/etc/mopidy/mopidy.conf`
```
[spotify]  
username = <name>  
password = <password>  
```
5. if the system uses *pulseaudio*, configure the server to accept internal connection. Open the config file at `/etc/pulse/default.pa`
```
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1
```
6. stop pulse `pulseaudio --kill` then restart it `start-pulseaudio-x11`
7. add audio config block to modidy config file:
```
[audio]  
output = pulsesink server=127.0.0.1
```
8. enable mopidy service: `systemctl enable mopidy.service`
9. start it: `systemctl start mopidy.service`
10. navigate to `http://localhost:6680`
