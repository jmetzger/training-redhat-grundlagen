# Journalctl 

## Show all boots 

``` 
 journalctl --list-boots
 0 3c3cf780186642ae9741b3d3811e95da Tue 2020-11-24 14:29:44 CET▒<80><94>T>
lines 1-1/1 (END)
```

## Show boot log 

```
journalctl -b 
```


## Journal persistent 

  * Normalerweise (auf den meisten Systemen), überlebt das Journal kein Reboot 
 
```
# persistent setzen
# Achtung: in /etc/systemd/journald.conf muss Storage=auto gesetzt sein
# Dies ist auch der Default - Fall 
# Achtung Achtung: Alle gezeigten Einträge mit # am Anfang sind die Default-Werte (in journald.conf) 
mkdir /var/log/journal 
systemctl restart systemd-journal-flush.service 

```

## Restrict how much is logged / data 

```
# in /etc/systemd/journald.conf 
SystemMaxUse=1G 
```

## journalctl 

```
# ubuntu
journalctl -u sshd 

# Nicht von Anfang, sondern die letzten Zeilen anzeigen 
journactl -eu sshd
```

## journalctl - ausgabe json 

```
# sehr schön um alle felder zu sehen 
journalctl -o json-pretty 
```

## journalctl - konkreten Prozess anzeigen 

```
journalctl _PID=5
```


## journalctl 

```
# ubuntu
journalctl -u ssh.service 
# Rocky / RHEL 
journalctl -u sshd.service

# sehr schön um alle felder zu sehen 
journalctl -o json-pretty 

# alles was pid xy
journalctl _PID=5 

# alles seit gestern 
journalctl --since yesterday 
journalctl --since now 
journalctl --since today
# mit datum -> hier wichtig, dass richtige format
# Mindestens Tag oder Tag und Uhrzeit (ohne sekunden)
# nur Stunde geht nicht
journalctl --since "2022-08-17 00:05"

# nur neuen Sachen / Veränderungen ausgeben
journalctl -f -u apache2.service 


```

## Help-pages 

```
man journalctl
man systemd.journal-fields
```


## Show all boots 

``` 
 journalctl --list-boots
 0 3c3cf780186642ae9741b3d3811e95da Tue 2020-11-24 14:29:44 CET▒<80><94>T>
lines 1-1/1 (END)
```

## Journal persistent 

  * Update: Ubuntu 22.04 ist per default persistent !!!
  * Normalerweise (auf den meisten Systemen), überlebt das Journal kein Reboot 
 
```
# persistent setzen
# Achtung: in /etc/systemd/journald.conf muss Storage=auto gesetzt sein
# Dies ist auch der Default - Fall 
# Achtung Achtung: Alle gezeigten Einträge mit # am Anfang sind die Default-Werte (in journald.conf) 
mkdir /var/log/journal 
systemctl restart systemd-journal-flush.service 

```

## Restrict how much is logged / data 

```
# in /etc/systemd/journald.conf 


