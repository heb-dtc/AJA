In order to have several user share rights on a directory, one can use groups:

#create new group
sudo groupadd mygroup

# add users to the new group
sudo usermod -a -G mygroup userOne
sudo usermod -a -G mygroup userTwo

# update permission on the directory to be shared amongs users
sudo chgrp -R mygroup /path/to/the/directory
sudo chmod -R g+w /path/to/the/directory

# update files permissions of the directory so that newly created files are owned by the group
sudo find /path/to/the/directory -type d -exec chmod 2775 {} \;

# find all files in the directory and add read and write permission for owner and group
sudo find /path/to/the/directory -type f -exec chmod ug+rw {} \;




