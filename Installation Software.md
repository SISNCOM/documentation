
# Procédure d'installation VM_CALCULE

**OS : Windows 10**   
   

   Prérequis :      

1) Installer MYSQL en utilisant le lien ci-dessous.  
    
https://dev.mysql.com/downloads/installer/

Veillez à choisir la bonne version à installer soit là Windows (x86, 32-bit), MSI Installer	8.0.33	qui pèse 428.3M.

Après avoir installer MYSQL, le configurer afin de pouvoir lancer une instance mysql grâce à la commande depuis l'invite de commande windows.

```
mysql -u<identifiant bdd> -h<adresse hote de la bdd> -p sis4web
```

2) Installer python avec le lien ci-dessosus.

https://www.python.org/downloads/release/python-3913/

L'installation va nous permettre d'installer python et son arboresence de fichier et libraire.

N'oubliez pas de mettre à jours vos variable d'environnement en y ajoutant le ***bin*** de mysql et python. 

3) Créer le dossier ```sisncome``` 

Rendez-vous sur votre disque de travail et créée un dossier sisncom à la racine puis ses 3 sous-dossiers associées.
Ouvrez une invite de commande est taper : 

```mkdir -p sisncom/config sisncom/python sisncom/services```



## Installation des programme

#### Python

Rendez-vous sur https://github.com/SISNCOM/sis4web_python_libraries
   

afin d'installer nos libraire python, vous devez au préalable installer git dans le but de cloner les répos git dans le dossier de destintation python.

Voici l'arboresence de python post-installation : 

```
.
└── AppData
    └── Local
        └── Programs
            └── Python
                └── Python3.9
                    ├── DLLs: Ce répertoire contient les bibliothèques dynamiques (DLL) utilisées par Python.
                    ├── include: Ce répertoire contient les fichiers d'en-tête (headers) utilisés lors de la compilation de modules Python.
                    ├── Lib
                    │   └── site-packages: Ce sous-répertoire contient les packages Python installés à l'aide de pip ou d'autres outils de gestion de paquets.
                    ├── Scripts: Ce répertoire contient les scripts exécutables associés à Python, tels que pip et d'autres outils.
                    ├── python.exe: C'est l'exécutable principal de Python.
                    ├── pythonw.exe: C'est l'exécutable principal de Python en mode fenêtré.
                    ├── python3.dll: Il s'agit de la bibliothèque dynamique (DLL) principale de Python.
                    ├── python39.dll: Il s'agit également d'une bibliothèque dynamique (DLL) principale de Python.
                    ├── python39._pth 
                    ├── python39.zip: Il s'agit d'une archive compressée contenant les fichiers principaux de Python.
                    ├── pyvenv.cfg: Ce fichier contient la configuration de l'environnement virtuel Python.
                    ├── LICENSE.txt: Ce fichier contient les termes de la licence de Python.
                    ├── NEWS.txt: Ce fichier contient les notes de version de Python.
                    └── README.txt: Ce fichier contient des informations générales sur l'installation de Python.
```


Diriger vous vers le dossier ```Lib``` puis lancer la commande 
```git clone https://github.com/SISNCOM/sis4web_python_libraries.git```

#### Config

Diriger vous vers le dossier ```config``` dans le dossier ```sisncom``` à la racine de votre disque où vous avez créée le dossier au préalable (voir Prérequis). 

Lancer la commande ```git clone https://github.com/SISNCOM/config.git```


