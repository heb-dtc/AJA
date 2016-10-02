### Add a user for a specific daemon

1. create group for user  
`$ sudo addgroup --system <groupname>`  
2. add user  
`sudo adduser --disabled-password --system --home <path-to-hom> --gecos "<readable-name" --ingroup <groupname> <username>`

> --system: the user is intended for running a daemon  
--disabled-password: no need to have password for the daemon  
--ingroup: add new user to group  
--home: override defautl home dir  
--gecos: some human readable name
