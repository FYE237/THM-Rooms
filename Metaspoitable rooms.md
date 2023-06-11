#   NOTES SUR LA ROOM 3
### Concernant la tâche 5 - question 2
Une fois que l'exploit a marché. on doit reprendre le control en utilisant le shell meterpreter. Donc on lance un exploit qui permet d'avoir accès au shell par meterpreter


## commandes utiles:

- shell : permet  d'accéder au shell de la machine dont la session est crée sur meterpreter
- help : liste les cmds possibles dasn meterpreter console
- sysinfo : Elle nous donne les informations sur la machine cible
- hashdump nous donne les hashs des mots de passe des différents utilisateurs


### Concernant la tâche 6 
Une fois qu'on a fait la question 3, il faut choisir le bon payload notamment ici  linux/meterpreter/reverse_tcp
 faire : 
 - Set les bons paramètres sur l'exploit ie lhost: @IP_locale , lport: le port sur lequel le payload crée par msfvenom  a été défini
 - search meterpeter/reverse_tcp  pour retrouver le bon payload ensuite _on set les options_
 - On a donc une session.
 
 Concernant la question 6 : 
 - Dans le shell de meterpreter on remarque qu'on pas accès à hasdump
 - On fait une recherche sur hasdump et on trouve le paylaod qui est sir linux && meterpreter 
 - on set les paramètres ici la session sur laquelle meterpreter est lancé et on a dans le terminal le hash des mots de passe

