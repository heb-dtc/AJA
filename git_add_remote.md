
### Add remote to existing git repository

Add an external remote to local git.

#### checkout the branch of a fork
```bash
git remote add <name> git://github.com/<name>/<project>
git fetch <name>
git checkout <name>/<branch>
```

#### add push url remote
```bash
git remote set-url --add --push origin <git-repo-url>
```
