#   NOTES SUR LA ROOM 3

### Commandes utiles

- _cat /etc/passwd | cut -d ":" -f 1_ : Cette commande nous permet de formater la sortie du fichier /etc/passwd. On coupe à partir de  :  et on affiche le caractère juste après

- _env_ : elle nous donne la lsite des variables d'envrionnement

 - _uname -a_ : Elle nous donne la version du logiciel

Looking at _/proc/version_ may give you information on the kernel version and additional data such as whether a compiler (e.g. GCC) is installed.

 looking at the _/etc/issue_ file. This file usually contains some information about the operating system but can easily be customized or changes. 

 - _find cmd_
 Find files:

    *  find . -name flag1.txt: find the file named “flag1.txt” in the current directory    
   *  find /home -name flag1.txt: find the file names “flag1.txt” in the /home director    
    * find / -type d -name config: find the directory named config under “/”    
    * find / -type f -perm 0777: find files with the 777 permissions (files readable, writable, and executable by all users)     
    * find / -perm a=x: find executable files
    * find /home -user frank: find all files for user “frank” under “/home”
    * find / -mtime 10: find files that were modified in the last 10 days
    * find / -atime 10: find files that were accessed in the last 10 day
    * find / -cmin -60: find files changed within the last hour (60 minutes)
    * find / -amin -60: find files accesses within the last hour (60 minutes)
    * find / -size 50M: find files with a 50 MB size



