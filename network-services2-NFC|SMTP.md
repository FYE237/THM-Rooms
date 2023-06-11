## PATH : Comptia pentest+

# [Network Services 2  ROOM](https://tryhackme.com/room/networkservices2)

## 1. Enumerating NFC
### Requirements

In order to do a more advanced enumeration of the NFS server, and shares- we're going to need a few tools. The first of which is key to interacting with any NFS share from your local machine: nfs-common.

### a. NFS-Common

It is important to have this package installed on any machine that uses NFS, either as client or server. It includes programs such as: lockd, statd, showmount, nfsstat, gssd, idmapd and mount.nfs. Primarily, we are concerned with "showmount" and "mount.nfs" as these are going to be most useful to us when it comes to extracting information from the NFS share. If you'd like more information about this package, feel free to read: https://packages.ubuntu.com/jammy/nfs-common.

You can install nfs-common using "sudo apt install nfs-common", it is part of the default repositories for most Linux distributions such as the Kali Remote Machine or AttackBox that is provided to TryHackMe.

### b. Port Scanning
The first step of enumeration is to conduct a port scan, to find out as much information as you can about the services, open ports and operating system of the target machine. You can go as in-depth as you like on this, however, I suggest using nmap with the -A and -p- tags. also the -v for verbose.

### c. Mounting NFS shares

Your client’s system needs a directory where all the content shared by the host server in the export folder can be accessed. You can create
this folder anywhere on your system. Once you've created this mount point, you can use the "mount" command to connect the NFS share to the mount point on your machine like so:

`sudo mount -t nfs IP:share /tmp/mount/ -nolock`




* use /usr/sbin/showmount -e [IP] to list the NFS shares, what is the name of the visible share?

First, use "mkdir /tmp/mount" to create a directory on your machine to mount the share to. This is in the /tmp directory- so be aware that it will be removed on restart.

Then, use the mount command we broke down earlier to mount the NFS share to your local machine. Change directory to where you mounted the share.

Use the `ls -la` to list file even the hidden ones.


## 2. Enumerating SMTP

SMTP runs on port 25.

With metaspoitable, we can  use modules like :
* Smtp_version
* smtp_enum 

Example of usernames list search for : usr/share/seclists/

We exploit smtp to have a username. The we use hydra to find by brute force the password for an ssh connection if ssh was amongst the services found.

With this we gain an ssh access to the remote server