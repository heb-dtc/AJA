### Fix unicode errror when ssh  

Fix the "Error opening terminal: rxvt-unicode-256color" 
(after ssh using urxvt)

- create *.terminfo/r* directory on the target machine  
- copy local one on remote machine  
`$ scp .terminfo/r/rxvt-unicode* remote:.terminfo/r`
