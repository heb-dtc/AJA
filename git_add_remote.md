Add an external remote to local git.
Can be useful when wanting to checkout the branch of a fork:

```
git remote add <name> git://github.com/<name>/<project>
git fetch <name>
git checkout <name>/<branch>
```
