### Simply generate a random alphanumeric password
`$ strings /dev/urandom | grep -o '[[:alnum:]]' | head -n 12 | tr -d '\n'`
> get random stuff from /dev/urandom  
 grep only alhpa numeric character
 get the 12 first
 trim the line jump
 
