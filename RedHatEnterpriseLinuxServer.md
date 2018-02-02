# Red Hat Enterprise Linux Server 7.3 (Maipo)

cat /etc/*-release - show linux version (Red Hat Enterprise Linux Server 7.3 (Maipo))

df -ah - show hdd space

### Share NFS folder
#### Configure NFS Server
* /usr/sbin/exportfs - command show exported folders
* Run vim /etc/exports - Update config add line "/folder_name *(rw)" in it and save
* Run /usr/sbin/exportfs -ra - Export folders

#### Configure NFS Client
* Run vim /etc/fstab - Update config add line "server:/remote/export_folder /local/folder nfs options 0 0" 
* Run mount /remote/export_folder

#### Problems: 
Running NFS behind firewall if you can't mount NFS folder from nodes.  

* Connect to NFS server
* Run rpcinfo -p you should see in console output
  ```javascript
  100003    2   udp   2049  nfs
  ...
  ```

  if you don't have  nfs in console you should enable sharing in firewall


* Run vim /etc/sysconfig/nfs - if not exist create new

  Add/Update config line RPCMOUNTDOPTS="-p port" 
  Example RPCMOUNTDOPTS="-p 22334"

* Restart NFS services 
* Run systemctl restart nfs-config
* Run systemctl restart nfs-server - if server doesn't start then port can be reserved

* Run rpcinfo -p you should see in console output
 ```
 javascript100003    2   udp   2049  nfs
 ...
 ```
 