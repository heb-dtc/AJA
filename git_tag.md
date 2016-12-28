### Update tag name
> create new tag from old one and push to remote  
`$ git tag new_tag old_tag`  
`$ git push --tags`

### Remove tags
> remove tags from remote repo and from local one  
`$ git push origin :refs/tags/tag_name`  
`$ git tag -d tag_name`

### Update local repo
> delete old tags locally and fetch all remote ones  
`git tag -l | xargs git tag -d && git fetch -t`  
