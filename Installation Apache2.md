# Procédure d'installation VM_WEB

***OS : Linux Ubuntu20.4***    

---

1) Mettre à jour l'installeur de packages en exécutant les commandes suivantes :   
   
   
```
sudo apt update
sudo apt upgrade
```

2) Installer le serveur Apache2 :   
   
   
```
sudo apt install apache2
```

2) Installer PHP, le module pour Apache2 et le support MySQL :   
   
   
```
sudo apt install php libapache2-mod-php php-mysql
```

3) Vous pouvez verifier la version de PHP installer  :   
   
   
```
php -v
```

Le résultat attendu est tel que : 

```
PHP 8.1.2-1ubuntu2.11 (cli) (built: Feb 22 2023 22:56:18) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
with Zend OPcache v8.1.2-1ubuntu2.11, Copyright (c), by Zend Technologies
```


4) Installer mbstring : 

```
apt install php-mbstring
```

5) Activer mbstring sur php : 

```
phpenmod mbstring
```

6) Active le module rewrite : 

```
a2enmod rewrite
```

Vous devriez avoir une réponse tel que : 

```
Enabling module rewrite.
To activate the new configuration, you need to run:
  systemctl restart apache2
```

7) Redémarrez alors comme demandé ci-dessus le service PHP en exécutant la commande suivante :
    

```
sudo systemctl restart apache2
```

8) Vérifiez que le service est en cours d'exécution en exécutant la commande suivante :
   

```
sudo systemctl status apache2
```

