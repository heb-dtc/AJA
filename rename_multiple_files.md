### Rename multiple files

- let say there are 4 directories named drawable-something1, drawable-something2, drawable-something3 and drawable-something4.
- the goal is to rename them drawable-word-something1, drawable-word-something2, drawable-word-something3 and drawable-word-something4.

- run the following command to check the result is proper
`$ for f in drawable*; do u=$(ls $f); n=$(ls  $f | sed 's/something/word-something/'); echo $f/$u $f/$n; done` 

- run this one to do the work:
``$ for f in drawable*; do u=$(ls $f); n=$(ls  $f | sed 's/something/word-something/'); mv $f/$u $f/$n; done` `
