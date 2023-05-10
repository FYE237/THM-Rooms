## PATH : Comptia pentest+

## [N-map ROOM](https://tryhackme.com/room/furthernmap)

ALlez régulièrement checker la page de nmap [here](https://nmap.org/book/)
### 1. Description de quelques options :  

- -sS : Syn scan
- -sU : Udp scan
- -o :  OS scan
- -sV : Script version scan
- -v : Rend Nmap plus verbeux (-vv pour plus d'effet)
- -oN/-oX/-oS/-oG <file>: Sortie dans le fichier en paramètre des résultats du scan au format normal, XML, s|<rIpt kIddi3 et Grepable, respectivement
- -oA <basename>: Sortie dans les trois formats majeurs en même temps
- -A : This is a shorthand switch that activates service detection, operating system detection, a traceroute and common script scanning.
- -p- : ON dit à nmap de scanner tous les ports
- FIrewall evasion : options : NULL,FIN,Xmas. Examples [here](https://tryhackme.com/room/furthernmap)

** Firewall evasion : [here](https://nmap.org/book/man-bypass-firewalls-ids.html)


### Task 11
There are many categories available. Some useful categories include:

* safe:- Won't affect the target 
* intrusive:- Not safe: likely to affect the target
* vuln:- Scan for vulnerabilities
* exploit:- Attempt to exploit a vulnerability
* auth:- Attempt to bypass authentication for running services (e.g. Log into an FTP server anonymously)
* brute:- Attempt to bruteforce credentials for running services
* discovery:- Attempt to query running services for further information about the network (e.g. query an SNMP server).

A more exhaustive list can be found [here](https://nmap.org/book/nse-usage.html).

Les scripts sont ici : /usr/share/nmap/scripts

Pour chercher un type de script:
On peut :
` grep "safe" /usr/share/nmap/scripts/* `

ou des scripts pour ftp
``` ls -l /usr/share/nmap/scripts/*ftp* ```

ou on cherche dans le fichier : ` /usr/share/nmap/scripts/script.db. ` 

C'est un fichier qui garde la liste des scripts ainsi que et leur type:
`grep "ftp" /usr/share/nmap/scripts/script.db`

 `head /usr/share/nmap/scripts/script.db ` : print the 10 first line of the files.

_To install new scripts_ : 

Installing New Scripts

``` We mentioned previously that the Nmap website contains a list of scripts, so, what happens if one of these is missing in the scripts directory locally? A standard sudo apt update && sudo apt install nmap should fix this; however, it's also possible to install the scripts manually by downloading the script from Nmap (sudo wget -O /usr/share/nmap/scripts/<script-name>.nse https://svn.nmap.org/nmap/scripts/<script-name>.nse). This must then be followed up with nmap --script-updatedb, which updates the script.db file to contain the newly downloaded script.Its worth noting that you would require the same "updatedb" command if you were to make your own NSE script and add it into Nmap -- a more than manageable task with some basic knowledge of Lua! ```.



### Notes sur le cas pratique : 
Si les ping ne marchent pas.
On peut faire des scans silencieux en supposant que les ports sont ouverts(Pn) . Par : nmap -Pn  -sX/sN/-sF -pa-b @IP  -vv(verbose)


Si on voulait faire un scan syn on aurait utiliser -sS


