# Kerbrute

To enumerate kerberos we can use [kerbrute](https://github.com/ropnop/kerbrute/releases), we can use kerbrus(version 1.0.2 in my case). ON my Computer it is stored in my user directory. /home

* chmod +x kerbru...

* ./kerbru.. -h


Global Flags:
```
      --dc string       The location of the Domain Controller (KDC) to target. If blank, will lookup via DNS
  -d, --domain string   The full domain to use (e.g. contoso.com)
  -o, --output string   File to write logs to. Optional.
      --safe            Safe mode. Will abort if any user comes back as locked out. Default: FALSE
  -t, --threads int     Threads to use (default 10)
  -v, --verbose         Log failures and errors
```

If the DNS_domain_name isn't known , just give the IP adress
Example for enumerating usernames : 

``./kerbrute_linux_386  `userenum` -d spookysec.local --dc 10.10.91.31 Téléchargements/userlist-AD.txt -t 100```

or 

(in the /etc/hosts we added this line : 10.10.91.31     spookysec.local)
`` ./kerbrute_linux_386  userenum -d spookysec.local --dc spookysec.local Téléchargements/ userlist-AD.txt -t 100 ```

