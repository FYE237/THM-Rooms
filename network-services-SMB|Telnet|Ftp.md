## PATH : Comptia pentest+

# [Network Services ROOM](https://tryhackme.com/room/networkservices)

## 1. Enumerating SMB 
Enumeration is the process of gathering information on a target in order to find potential attack vectors and aid in exploitation.This process is essential for an attack to be successful, as wasting time with exploits that either don't work or can crash the system can be a waste of energy. Enumeration can be used to gather usernames, passwords, network information, hostnames, application data, services, or any other information that may be valuable to an attacker.


### Method Breakdown

So, from our enumeration stage, we know:

    - The SMB share location

    - The name of an interesting SMB share

### SMBClient

Because we're trying to access an SMB share, we need a client to access resources on servers. We will be using SMBClient because it's part of the default samba suite. While it is available by default on Kali and Parrot, if you do need to install it, you can find the documentation here.

We can remotely access the SMB share using the syntax:

`` smbclient //[IP]/[SHARE] ``

Followed by the tags:

- U [name] : to specify the user

- p [port] : to specify the portMethod Breakdown

- P : SPecify the password of the user

- L : list all the shares.

Example : `smbclient -L 10.10.91.31 -U 'svc-admin' -p 'management2005'`



## 2. Enumerating Telnet

### Method Breakdown

So, from our enumeration stage, we know:

- There is a poorly hidden telnet service running on this machine

- The service itself is marked "backdoor"

- We have possible username of "Skidy" implicated

Using this information, let's try accessing this telnet port, and using that as a foothold to get a full reverse shell on the machine!

### Connecting to Telnet

You can connect to a telnet server with the following syntax:

    "telnet [ip] [port]"

We're going to need to keep this in mind as we try and exploit this machine.

`To run command in telnet we need to add .RUN before the cmd to run`


## 3. Enumerating FTP

We can try to login anonymously : 
```
ftp $ip
login: anonymous
password: 
```

### Method Breakdown

So, from our enumeration stage, we know:

- There is an FTP server running on this machine

- We have a possible username

- Using this information, let's try and bruteforce the password of the FTP Server.

Using [Hydra](Hydra--notes.md) : 
The syntax for the command we're going to use to find the passwords is this:

`hydra -t 4 -l dale -P /usr/share/wordlists/rockyou.txt -vV 10.10.10.6 ftp`
Let's break it down:

SECTION  | FUNCTION

hydra  Runs the hydra tool

-t 4 : Number of parallel connections per target

-l [user]  : Points to the user who's account you're trying to compromise

-P [path to dictionary] : Points to the file containing the list of possible passwords

-vV  : Sets verbose mode to very verbose, shows the login+pass combination for each attempt

[machine IP]  : The IP address of the target machine


## Furhter Lectures
## Reading

Here's some things that might be useful to read after completing this room, if it interests you:

https://medium.com/@gregIT/exploiting-simple-network-services-in-ctfs-ec8735be5eef
https://attack.mitre.org/techniques/T1210/
https://www.nextgov.com/cybersecurity/2019/10/nsa-warns-vulnerabilities-multiple-vpn-services/160456/