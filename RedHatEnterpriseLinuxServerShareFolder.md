# Red Hat Enterprise Linux Server 7.3 (Maipo)

### Share NFS folder
#### Configure NFS Server
* Run df -ah - show hdd space
* Run /usr/sbin/exportfs - command show exported folders
* Run vim /etc/exports - Update config add line "/folder_name *(rw)" in it and save [*(rw,sync,no_subtree_check,no_root_squash)"]
* Run /usr/sbin/exportfs -ra - Export folders

#### Configure NFS Client
* Run vim /etc/fstab - Update config add line "server:/remote/export_folder /local/folder nfs defaults 0 0" 
* Run mount -t nfs nfs_server_dom:/folder /folder

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
 ```javascript
 100003    2   udp   2049  nfs
 ...
 ```
 
 Links:
 * [How NFS Works](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/storage_administration_guide/ch-nfs)
 * [Running NFS Behind a Firewall](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/nfs-serverconfig)
 * [Troubleshooting NFS and rpcbind](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/s2-nfs-methodology-portmap#s3-nfs-methodology-portmap-rpcinfo)
 * [Mounting NFS File Systems using /etc/fstab](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/storage_administration_guide/nfs-clientconfig)

 
