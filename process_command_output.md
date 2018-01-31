## Different methods to pipe output to another command

### xarg
`git branch --merged master | egrep -v "master" | xargs echo git branch -d`

### while
`while read b; do echo "git branch -d $b"; done < <(git branch --merged master | grep -v 'master')`

### echo
`echo git branch -d $(git branch --merged master | grep -v 'master')`
