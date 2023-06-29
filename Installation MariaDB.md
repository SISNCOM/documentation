
# Procédure d'installation de MariaDB

prérequis :

- OS version : Ubuntu 22.04.2 LTS   
- SGBD MariaDB version : 10.3.28-MariaDB ou 10.6-MariaDB

---

1) Mettre à jour l'installeur de packages en exécutant les commandes suivantes :   
   
   
```
sudo apt update
sudo apt upgrade
```

2) Installer le serveur MySQL en utilisant le package de MariaDB :
   

```
sudo apt install mariadb-server mariadb-client
```

3) Configurer de MariaDB et de sa sécurité en exécutant la commande suivante :
   

```
sudo mysql_secure_installation
```

- Lorsqu'on vous demande de saisir le mot de passe actuel, appuyez simplement sur Entrée car il n'y en a pas.   
- Pour le commutateur d'authentification du socket Unix, vous pouvez laisser la valeur par défaut, qui est "Yes".   
- Changez le mot de passe root de MySQL en suivant les instructions à l'écran (assurez-vous de ne pas perdre ce mot de passe).   
- Répondez "Yes" pour supprimer les utilisateurs anonymes.
- Répondez "Yes" pour désactiver la connexion à distance de root.
- Répondez "Yes" pour supprimer la base de données de test.
- Répondez "Yes" pour recharger les privileges des tables.

C'est fait !  Si vous avez suivi toutes les étapes ci-dessus, votre installation MariaDB devrait maintenant être sécurisée.   

4) Redémarrez le service MySQL en exécutant la commande suivante :
    

```
sudo service mysql restart
```


6) Lancer la connexion à la base de données et entrer le mot de passe définit plus haut : 
   

```
mysql
```

Suite à cela, vous devriez avoir un affichage comme ci-dessous :
   
```
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 31
Server version: 10.6.12-MariaDB-0ubuntu0.22.04.1 Ubuntu 22.04

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> 
```

7) Créer une base de données :
   

```mysql
CREATE DATABASE sis4web;
```

8) Création d'un utilisateur


```sql
create user 'sis4web'@'localhost' IDENTIFIED BY '<votre mot de passe>';
```

9) Allocation des privileges à l'utilisateur <username> : 
    
    
```sql
GRANT ALL PRIVILEGES ON sis4web.* TO 'sis4web'@'localhost';
```

10) Utilisé la base de données : 
   
```sql
use sis4web
```


11) Télécharger le fichier de base de données : 

#-----#

11) Importé les fichiers sql : 
   

```sql
use sis4web
\. <filename.sql>
```

12) Ajouter deux nouveaux utilisateurs et les relier aux IP nécéssaires:

```
create user sis4web@'IP-VM-WEB' IDENTIFIED BY '<votre mot de passe>';
create user sis4web@'IP-VM-CALC' IDENTIFIED BY '<votre mot de passe>';
create user glb4web@'IP-VM-WEB' IDENTIFIED BY '<votre mot de passe>';
create user glb4web@'IP-VM-CALC' IDENTIFIED BY '<votre mot de passe>';
```
```sql
GRANT ALL PRIVILEGES ON sis4web.* TO sis4web@'192.168.255.14';
GRANT ALL PRIVILEGES ON sis4web.* TO sis4web@'192.168.255.24';
GRANT ALL PRIVILEGES ON sis4web.* TO glb4web@'192.168.255.14';
GRANT ALL PRIVILEGES ON sis4web.* TO glb4web@'192.168.255.24'
```

13) Recharger les privilèges MySQL stockés en mémoire et les réappliquer immédiatement: 
   

```
FLUSH PRIVILEGES
```
   
14) Pour retirer la variable bind_address du fichier de configuration MySQL sur Ubuntu, vous pouvez suivre les étapes suivantes : 
   
- Ouvrez le fichier de configuration MySQL mariadb.conf avec un éditeur de texte. Vous pouvez utiliser la commande suivante dans le terminal pour ouvrir le fichier avec l'éditeur de texte nano :
   
   ```
   sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
   ```
   
- Recherchez la ligne qui contient la variable bind_address. Cette ligne peut ressembler à ceci et commenter là en ajoutant un (#) devant la ligne:
   ```
      #bind-address            = 127.0.0.1
   ```
   
- Redémarrez le serveur MySQL pour appliquer les modifications de configuration. Vous pouvez utiliser la commande suivante pour redémarrer le serveur MySQL : 
   ```
   sudo systemctl restart mysql
   ```


# INSTALLER PHPMYADMIN


1) sudo apt-get install php libapache2-mod-php php-mysql

1) sudo apt-get install PHPMYADMIN

2)
- apache -> appuyer sur entrer
- dbCommon-> yes 
- mdp (mettre le meme que pour la db) -> Entrer

3) redemarrer apache 

  
