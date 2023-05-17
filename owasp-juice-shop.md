## PATH : Comptia pentest+

## [OWAPS JUICE- SHOP](https://tryhackme.com/room/owaspjuiceshop)

sql injection is possible enven with JSON object.

Example : 
{
    email : value,
    password
}

injection : 
{
    "email" : "' or 1=1 -- ",
    "password" : ".."
}

if the email is knwon
{
    "email":"ali@xx.com' --",
    "password":"cc"
}


Another list of payload for BUrpsuite : spectlists 
Installation : sudo apt-get install seclists

Stored : /usr/share/seclists

IN this case we will use : /usr/share/SecLists/Passwords/Common-Credentials/best1050.txt

* Poison null bytes
    To get around this, we will use a character bypass called "Poison Null Byte". A Poison Null Byte looks like this: %00. 

    Note: as we can download it using the url, we will need to encode this into a url encoded format.

    The Poison Null Byte will now look like this: %2500. Adding this and then a .md to the end will bypass the 403 error!



    Why does this work? 

    A Poison Null Byte is actually a NULL terminator. By placing a NULL character in the string at a certain byte, the string will tell the server to terminate at that point, nulling the rest of the string. 


## TO -DO 
come on this room later on @ip/#/score-board/ to practice more difficult tasks (XSS-injection,...)
