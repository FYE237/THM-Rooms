## PATH : Comptia pentest+

## [Nessus ROOM](https://tryhackme.com/room/rpnessusredux)

nessus tourne sur le port 88344 [here](https://localhost:8834/#/)



#### HOW TO RESET NESSUS PASSWORD

The following steps were found [here](https://www.hackercoolmagazine.com/reset-nessus-password-in-kali-linux/)

1. navigate to /opt/nessus/sbin
2. ls => nessuscli
3. sudo ./nessuscli lsuser : it will shows you the list of current users.
4. sudo sudo ./nessuscli chpasswd name-user : Then you enter the new password for the specify user.