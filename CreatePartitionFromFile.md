### Create partition from a file  

- create file of 4MB  
`$ dd if=/dev/zero of=$HOME/fake-tmp-disk count=4000 bs=1024`  

- create file system  
`$ mkfs.ext4 $HOME/fake-tmp-disk`  

- mount it  
`$ sudo mount -o loop $HOME/fake-tmp-disk $HOME/<some-dir>`
