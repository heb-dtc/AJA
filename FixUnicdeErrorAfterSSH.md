Fix the "Error opening terminal: rxvt-unicode-256color" 
(after ssh using urxvt)

1. create .terminfo/r directory on the target machine
2. scp .terminfo/r/rxvt-unicode* remote:.terminfo/r
