### Comparing two branches 
- simple branch diff  
`$ git diff branchA..branchB`  
OR   
`$ git diff branchA...branchB`  

- it is also possible to use git difftool to see a graphical diff  
`$ git difftool branchA..branchB`  

- difftool can be configured like this:  
`$ git config --global diff.tool <tool>`  

- to avoid having to see each file one by one, it is possible to call  
`$ git difftool -d branchA..branchB`
