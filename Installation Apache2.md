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
sudo apt install php libapache2-mod-php php-mysql  php-mbstring
```


5) Activer mbstring sur php : 

```
phpenmod mbstring
```

6) Active le module rewrite : 

```
a2enmod rewrite
```

7) Redémarrez alors comme demandé ci-dessus le service PHP en exécutant la commande suivante :
    

```
sudo systemctl restart apache2
```

8) Vérifiez que le service est en cours d'exécution en exécutant la commande suivante :
   

```
sudo systemctl status apache2
```

