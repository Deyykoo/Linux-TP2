# Linux-TP2

## Partie 1 : Files and users

### I. Fichiers

```
1. Find me

🌞 Trouver le chemin vers le répertoire personnel de votre utilisateur  
- commande pwd : /home/quentin

🌞 Trouver le chemin du fichier de logs SSH
- commande : cd var/log/ 

🌞 Trouver le chemin du fichier de configuration du serveur SSH
- commande : cd etc/ssh/
```

### II. Users

```
 1. Nouveau user

🌞 Créer un nouvel utilisateur
- commande :  sudo useradd -d /home/papier_alu marmotte

```
```

2. Infos enregistrées par le système

🌞 Prouver que cet utilisateur a été créé
- commande :
[marmotte@localhost ~]$ cat /etc/passwd | grep marmotte
marmotte:x:1001:1001::/home/papier_alu:/bin/bash

🌞 Déterminer le hash du password de l'utilisateur marmotte
- commande : 
[quentin@localhost ~]$ sudo cat /etc/shadow | grep marmotte
marmotte:$6$XTjzoJswhE9x4mvP$k1EEni1deXNIzjjOpfCQFcWt85t6/.BPTQ9hbXocyzVIWv5OG0wp7xosSmWbPLcDgw/LnHc6b.oW.zF/E72yq0:19745:0:99999:7:::

```

```
3. Hint sur la ligne de commande

🌞 Tapez une commande pour vous déconnecter : fermer votre session utilisateur
- commande :
[quentin@localhost ~]$ exit
logout


🌞 Assurez-vous que vous pouvez vous connecter en tant que l'utilisateur marmotte
- commande :
Last login: Tue Jan 23 11:14:11 CET 2024 on pts/0
[marmotte@localhost ~]$
- [marmotte@localhost ~]$ ls /home/quentin/
ls: cannot open directory '/home/quentin/': Permission denied

```

## Partie 2 : Programmes et paquets

### I. Programmes et processus

```
1. Run then kill

🌞 Lancer un processus sleep
 - commande : sleep 1000
 quentin     1910  0.0  0.0   5584  1016 pts/0    S+   11:44    
 0:00 sleep 1000

 🌞 Terminez le processus sleep depuis le deuxième terminal
 - commande : kill 1910
 Terminated
 [quentin@localhost ~]$

```

```
2. Tâche de fond

🌞 Lancer un nouveau processus sleep, mais en tâche de fond
- commande : sleep 1000 &
[quentin@localhost ~]$ sleep 1000 &
[1] 1924

🌞 Visualisez la commande en tâche de fond
- commande : jobs 
[quentin@localhost ~]$ jobs
[1]+  Running                 sleep 1000 &
```

```	
3. Find paths

🌞 Trouver le chemin où est stocké le programme sleep
- commande :  cd /usr/bin/sleep

[quentin@localhost ~]$ ls -al /usr/bin | grep sleep
-rwxr-xr-x.  1 root root   36312 Apr 24  2023 sleep



🌞 Tant qu'on est à chercher des chemins : trouver les chemins vers tous les fichiers qui s'appellent .bashrc

- commande : sudo find / -name .bashrc
[quentin@localhost ~]$ sudo find / -name .bashrc
[sudo] password for quentin:
/etc/skel/.bashrc
/root/.bashrc
/home/quentin/.bashrc
/home/papier_alu/.bashrc

🌞 Vérifier que
- commande : which
[quentin@localhost ~]$ which sleep
/usr/bin/sleep
[quentin@localhost ~]$ which ssh
/usr/bin/ssh
[quentin@localhost ~]$ which ping
/usr/bin/ping
[quentin@localhost ~]$
```

### II. Paquets

```	
🌞 Installer le paquet
- commande : sudo dnf install git 

🌞 Utiliser une commande pour lancer Git
- commande : cd /usr/bin/git

🌞 Installer le paquet nginx
- commande : sudo dnf install nginx

🌞 Déterminer
- commande : cd /var/log/nginx
  commande : cd /usr/sbin/nginx

🌞 Mais aussi déterminer l'adresse http ou https des serveurs où vous téléchargez des paquets
- commande : nslookup
[quentin@localhost ~]$ nslookup nginx.com
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   nginx.com
Address: 185.56.152.165

[quentin@localhost ~]$ nslookup github.com
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   github.com
Address: 140.82.121.3
```

