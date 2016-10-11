### Deploy a MongoDB with docker

1. pull the latest docker mongo image  
> $ docker pull mongo:latest -t <image_name>

2. setup where the db will be written on the host  
> $ sudo mkdir </some/path/somewhere>

3. fire up the container  
> $ docker run -p 27017:27017 -v <host:/data/db --name mongo_container -d mongo mongod --auth
 -p: map container port to host port
 -v: map directory on host to directory on container
 --name: name of the container
 -d: launch container in daemon mode
 mongo: name of the image created before
 mongod --auth: the command to run in the container, mongo daemon with auth enable 
