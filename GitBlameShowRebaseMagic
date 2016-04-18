Clean up some dirty file before commiting

- find which commit introduced the dirt:
$ git blame <file>

- look at the commit (if needed)
$ git show <commit>

- rebase just before that commit
$ git rebase -i <commit>~1

- edit the faulty commit and add the file
$ git add <file>
- finish the rebase 
$ git rebase --continue

ENJOY!
