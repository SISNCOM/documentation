
# Procédure d'installation VM_CALCULE

**OS : Windows 10**   
   
   

   Prérequis :      

1) Installer MYSQL en utilisant le lien ci-dessous.  
    
https://dev.mysql.com/downloads/installer/

Téléchargez la version "Windows (x86, 32-bit), MSI Installer 8.0.33" qui pèse 428.3M.

Après avoir installé MYSQL, lancez depuis l'invité de commande windows afin de tester la connexion.

```
mysql -u<identifiant bdd> -h<adresse hote de la bdd> -p sis4web
```

2) Installer python avec le lien ci-dessosus.

https://www.python.org/downloads/release/python-3913/

L'installation va nous permettre d'installer python et son arborescence de fichiers et libraire.

N'oubliez pas de mettre à jour vos variables d'environnement en y ajoutant le dossier ***bin*** de mysql et python.

3) Créer le dossier ```sisncom``` 

Rendez-vous sur votre disque de travail est créez un dossier `sisncom` à la racine ainsi que ses 3 sous-dossiers associés.
Ouvrez une invite de commande et entrer la commande suivante : 

```mkdir -p sisncom/config sisncom/python sisncom/services```


## Installation des programme

#### Python

Rendez-vous sur https://github.com/SISNCOM/sis4web_python_libraries
   

afin d'installer nos libraires python, vous devez au préalable installer git dans le but de cloner les repos git dans le dossier de destination python.

Voici l'arboresence de python post-installation : 

```
.
└── AppData
    └── Local
        └── Programs
            └── Python
                └── Python3.9
                    ├── DLLs
                    ├── include
                    ├── Lib
                    │   └── site-packages
                    ├── Scripts
                    ├── python.exe
                    ├── pythonw.exe
                    ├── python3.dll
                    ├── python39.dll
                    ├── python39._pth 
                    ├── python39.zip
                    ├── pyvenv.cfg
                    ├── LICENSE.txt
                    ├── NEWS.txt
                    └── README.txt
```
   

----   
- Dirigez-vous vers le dossier ```Lib``` puis lancer la commande: ```git clone https://github.com/SISNCOM/sis4web_python_libraries.git```


- Dirigez-vous ensuite vers le dossier ```sisncom\python``` puis lancer la commande:    ```https://github.com/SISNCOM/sisncom-python-executables.git .``` ( Attention à ne pas oublier le "point" à la fin de la commande ! )

#### Config

- Dirigez-vous vers le dossier ```config``` dans le dossier ```sisncom``` à la racine de votre disque où vous avez créée le dossier au préalable (voir Prérequis). 

- Lancez la commande:```git clone https://github.com/SISNCOM/config.git . ```( Attention à ne pas oublier le "point" à la fin de la commande ! )

#### Services

- Dirigez-vous vers le dossier ```sisncom\services``` dans le dossier ```sisncom``` à la racine de votre disque où vous avez créée le dossier au préalable (voir Prérequis). 

- Lancez-la commande:```https://github.com/SISNCOM/sisncom-cpp-executables.git .```( Attention à ne pas oublier le "point" à la fin de la commande ! )

Lancer un des services disponibles : 
- 1_srvImg
- 2_screenDisque
- ...

Dans le cas où vous tombez sur une erreur de fichier .dll manquant.
Téléchargez le dll ```libmysql.dll``` et déposez-le sur le dossier ```systeme32```, puis relancez le service et verifiez qu'il se lance.

