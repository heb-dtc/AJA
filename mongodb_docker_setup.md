### Deploy a MongoDB with docker

1. pull the latest docker mongo image  
> `$ docker pull mongo:latest -t <image_name>`

2. setup where the db will be written on the host  
> `$ sudo mkdir </some/path/somewhere>`

3. fire up the container  
> `$ docker run -p 27017:27017 -v <host:/data/db --name mongo_container -d mongo mongod --auth`  
 -p: map container port to host port  
 -v: map directory on host to directory on container  
 --name: name of the container  
 -d: launch container in daemon mode  
 mongo: name of the image created before  
 mongod --auth: the command to run in the container, mongo daemon with auth enable  

4. add super user to admin db
> launch mongo client on the container:  
 `$ docker exec -it <image-name> mongo`
 once the mongo client started, add the super user:  
 `$ use admin`
 `$  db.createUser({user: "<name>",pwd: "<pass>",roles: [{role: "userAdminAnyDatabase", db: "admin"}]})`  
 
5. try out the connection
> `$ mongo -u "<name>" -p "<pass>" --authenticationDatabase admin`
 
6. add a user to an existing db
> fire up the mongo client with the admin auth  
 once the command line of the client is ready, switch db and add user
 `$ use <dbname>`
 `$ db.createUser({user: "<name>",pwd: "<pass>",roles: ["dbOwner"]})`
