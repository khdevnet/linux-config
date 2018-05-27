# General

* cat /etc/passwd - show all users in system
* su - [username] - switch to user
* ssh-keygen -f ~/.ssh/id_rsa -y > ~/.ssh/id_rsa.pub  - generate public key from private
* cat /etc/*-release - show linux version

### Filesystem commands
* find / -type f -name "*.ext" - find file by pattern
* rm -r mydir - remove directory with files
* mv file_name file_name - move file 
* cp file_name /folder_name - copy file to folder [-r] - recursive
* df -ah - show hdd space
* chmod -R 777 - set all permissions to folder
* du -sh /folder  - calc folder size
* tr -d '\r' < badscript   > goodscript - save file wirh \r end of the line instead \r\n
* pwd - current directory
* find /Applications/Unity/ -iname "libjpeg*" ### find by name
