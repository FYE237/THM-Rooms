## PATH : Comptia pentest+

## [Network Services ROOM](https://tryhackme.com/room/networkservices)

### Enumerating SMB 
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
