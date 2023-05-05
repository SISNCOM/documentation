
# Procédure d'installation de MariaDB

***OS : Linux Ubuntu20.4***    
***Client SQL : MariaDB***

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
sudo systemctl restart mysql
```

5) Vérifiez que le service est en cours d'exécution en exécutant la commande suivante :
   

```
sudo systemctl status mysql
```
   

6) Lancer la connexion à la base de données et entrer le mot de passe définit plus haut : 
   

```
mysql -u root -p
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
CREATE DATABASE <db name>
```

8) Création d'un utilisateur


```sql
create user '<username>'@'localhost' IDENTIFIED BY '<db password>';
```

9) Allocation des privileges à l'utilisateur <username> : 
    
    
```sql
GRANT ALL PRIVILEGES ON <db name>.* TO '<username>'@'localhost';
```
Vous pouvez verifier que les privileges ont été accorder en executant cette commande : 
   

```sql
SHOW GRANTS FOR '<db name>'@'localhost';
```
10) Utilisé la base de données : 
   

```sql
use <db name>
```

11) Importé les fichiers sql : 
   

```sql
\. <filename.sql>
```

12) Ajouter deux nouveaux utilisateurs et les relier aux IP nécéssaires:
   

```sql
create user '<username>'@'IP' IDENTIFIED BY '<db password>';
```
```sql
GRANT ALL PRIVILEGES ON <db name>.* TO '<username>'@'IP';
```

13) Recharger les privilèges MySQL stockés en mémoire et les réappliquer immédiatement: 
   

```
FLUSH PRIVILEGES
```
