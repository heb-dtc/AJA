### Using CCACHE

- enable ccache  
`$ export USE_CCACHE=1`  
`$ export CCACHE_DIR=</some/dir>`  

- Make sure that CCACHE is in the path  
`$ export PATH=/usr/lib64/ccache/bin:$PATH`  

- Make sure that the ccache binary is used for compiling, ff not, create symbolic links  
`$ mkdir ~/bin`
`$ ln -s ~/bin/g++ /usr/lib64/ccache/bin/g++`  

- check cache usage  
`$ ccache -s`
