# obnam backup wrapper

This utility will backup your data to a network storage server, mounted over NFS.
Following data is backed up:
* MySQL databases
* system packages (apt)
* custom additional folders

The tool needs the following binaries to be installed:
* obnam (for incremental backups)
* apt-clone (for package backup)
* mysql (obviously..)
* dpkg-repack (for package backup)
* nfs-common (for mounting remote storage as nfs [default])
* glusterfs-client (for mounting remote storage as glusterfs)

Every backup after the first one is incremental.
Obnam uses deduplication and you can delete any backup generation without manipulating the others. For more information see obnam.org.

### sample backup.conf storage configurations
```
# mount via NFS
REMOTE_STORAGE_PATH="00.00.00.00:/vol-00000-1"
REMOTE_STORAGE_TYPE="nfs"
REMOTE_STORAGE_OPTIONS=""

# mount via GlusterFS
REMOTE_STORAGE_PATH="00.00.00.00:/vol-00000-1"
REMOTE_STORAGE_TYPE="glusterfs"
REMOTE_STORAGE_OPTIONS=""

# mount via Samba
REMOTE_STORAGE_PATH="//00.00.00.00/vol-00000-1"
REMOTE_STORAGE_TYPE="cifs"
REMOTE_STORAGE_OPTIONS="-o username=xxx -o password=xxx"
```
