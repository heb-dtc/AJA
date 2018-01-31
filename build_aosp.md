### Build AOSP  

- Create a docker file with all needed dependencies to build the selected version of Android  

- Use repo to init your AOSP worktree  

- Run your docker container  
`$ docker run -u=<uuid-host-user> -v <host-dir>:<docker-dir> -v /tmp/:/tmp/ --rm=true -t -i <image-name>`  

> we pass *-u=\<uuid-host-user\>* so that the user in the docker and the user on the host share the same UUID and therefore the user in the docker can write inside the dir mapped from the host.  
> we map the home of the host on the docker and we map */tmp* from host in */tmp* on the docker 

- once inside the docker run  
```
$ source build/env_setup.sh
$ lunch
$ make -jX <target>
```
