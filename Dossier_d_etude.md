# Dossier d'étude et de choix des solutions:

## 1- Mise en Contexte du sujet:

Dans le cadre de la SAE 1.03, nous avions à réaliser une intallation d'un poste pour le développement sur un OS de type UNIX libre. Une des raison à ce choix est sa gratuité et son large panel de distribution. J'ai choisi d'utiliser Debian comme distribution. Il est très complet car il possède de nombreux paquets gratuits mais surtout car il est très stable et sur. Debian offre une compatibilité avec de nombreux logiciels, idispensable selon moi. De plus son installation pour une personne inexpérimentée n'est pas si difficile et est plutot bien guidée. Sa taille a également été un facteur important dans mon choix car en effet un iso de Debian est largement plus léger que celui d'Ubuntu par exemple. Avec quelques Go de stockage il est possible de posséder un environnement de travail plus que suffisant.


## Tableau des Besoins:

Ci-dessous, vous trouverez une liste de logicielle répondant à des besoins spécifiques, ils sont triés selont les critères:

- `logiciels préférés`;

- | logiciel favoris  ------> logiciel le moins apprécié |


| Besoin                                                                             | Nombre d'outils différents demandés | Logiciels proposés |
| ---------------------------------------------------------------------------------- | :----------------------------------:| -------------------|
| Avoir des Gestionnaires de bureau/fenêtre (dont un qui vous plaise)                | 4                                   |Bureau: `XFCE4` - LXDE;  Fenetre `Xfwm4` - I3,  |
| Avoir deux utilisateurs: vous et "stagiaire"                                       |                                     | bastien et stagiaire |
| Compiler un programme C                                                            | 2                                   | `gcc` - llvm |
| Regarder les pages de man de la libC                                               | 2                                   | glibc-doc - manpages-fr-dev               |
| Lancer un `make`                                                                   |                                     | make                   |
| Éditer du code source                                                              | 4                                   |  `Visual_Studio_Code` - `Vim` - Geany - Bluefish                  |
| Déboguer du code                                                                   | 2                                   | `gdb` - Valgrind                   |
| Naviguer sur le Web                                                                | 2                                   | Google `Chrome` - firefox-esr                  |
| Éditer une image matricielle (png...)                                              | 2                                   | `Gimp` - Krita                  |
| Éditer une image vectorielle (svg)                                                 | 1                                   | `Inkscape`                   |
| (Dé)Compresser les formats `targz` et `7z` et `rar`                                | 1                                   | `p7zip` - unrar-free                  |


## Explications des choix:

### Gestionnaires de bureau/fenêtre:

Selon moi XFCE4 est le meilleur compromis comme environnement de bureau, il est léger et assez sobre, ce qui le rend très pratique et simple d'utilisation. De plus il comprend un gestionnaire de fenetre intégré très agréable à utiliser. Tout cet ensemble est très bien optimisé et ne requiert que très peu de puissance. Bien que XFCE et LXDE soient extrement similaire en tout point, je trouve que son gestionnaire de fenetre (open box) ainsi que son editeur de texte, son terminal, son visionneur d'image sont beaucoup moins intéressant que ceux de XFCE. I3 est également très interressant, c'est un des gestionnaire de fenetre le plus léger possible. Il est reconnu pour son minimalisme et sa grande efficacité.

### Compiler un programme en C:

GCC permet de compiler un programme C. Il est possible de lui passer en argument le paramètre `-Wall` qui permet d'afficher plus en détail les erreurs ainsi que certains maladresses qui pourraient entrainer une éventuelle erreur. GCC est très malin et permet de passer outre certaines règles originelles du C, il accorde donc plus de liberté au développeur. LLVM est quant à lui très optimisé pour le gain de temps et de performance mais demande beaucoup de rigueur.

### Regarder les pages de man de la libC:

glibc-doc offre une documentation très complète sur l'ensemble des librairies en C. Alors que manpages-fr-dev permet de lire en francais des pages de manuel sur de nombreuses librairies de la libC mais également sur celles d'autres langages.

### Éditer du code source:

Visual_Studio_Code est selon le meilleur éditeur de code source. Il est simple de télécharger des extansions pour faciliter la programmation. C'est un logiciel très complet qui permet notamment l'option `sharecode` qui permet de coder en même temps à plusieurs sur un même fichier. Vim est quand à lui beaucoup plus simple et léger, cependant il est possible de télécharger de nombreux plugins pour le rendre vraiment personnel. C'est sa grande force. Geany est simple et épuré mais offre toute les fonctionnalités primordiales comme un terminal d'intégré... Pour finir, Bluefish est assez similaire à Geany et qui permet une coloration syntaxique de plus de 25 langages de programmation.

### Déboguer du code :

GDB est selon moi le meilleur debogeur, il est simple et fonctionne pour plusieurs langages: C, C++ etc...Valgrind quant à lui permet d'avertir sur les fuites mémoire notamment, très pratique pour faire face au fameux `segmentation fault` qui donne des migraines.

### Naviguer sur le Web:

Google permet un accès rapide à internet tout en intégrant de nombreuses fonctionnalités comme la traduction d'une page, l'accès rapide à ses mail via Gmail. En revanche la où est la force de firefox-esr est sa garantie de la vie privée.

### Éditer une image matricielle: 

Gimp est un éditeur d'image matricielle assez complet mais surtout largement plus léger que Krita bien plus complet. De plus Krita possède une aide au lancement du logiciel pour expliquer comment se dernier fonctionne.

### Éditer une image vectorielle (svg)

Inkscape est un éditeur d'image vectorielle, très facile à prendre en main et plutot léger. Il est entre autre préconisés par l’État français dans le cadre de la modernisation globale de ses systèmes d’informations. Inkscape permet à vos projets d'être exportés dans de nombreux formats.

### DéCompresser les formats `targz` et `7z` et `rar`

p7zip par ses nombreuses options permet d'avoir pleinement le controle sur ce que l''on décide d'archiver ou de désarchiver. En effet, il est possible de savoir si l'on veur respecter l'l'arborescence dans les fichiers extraits ou pas... p7zip permet de compresser sous de nombreux formats: tar.gz, gz.b2z... Unrar-free permet de décompresser des archives en .rar de manière totalement gratuite.


## Points indispensables à maitriser:

### Gestionnaire de paquets:

-    Installer un logiciel: 

sudo apt-get install nom_paquet : va chercher les paquets sur les serveur mirroir de l'archive
dpkg -i nom_paquet : permet d'installer un paquet déjà téléchargé.
-    Désinstaller un logiciel: 

sudo apt-get --purge remove nom_paquet

-    Faire une recherche sur les paquets disponibles:

apt-cache search nom_paquet

-    Faire une mise à jour: 

sudo apt-get update

-    Lister les fichiers installés par un paquet: 

sudo dpkg -S nom_paquet

-    Rechercher quel paquet contient un fichier donné:

apt-file search -v nom_fichier

-    Idem si le paquet n'est pas installé:

apt-cache show nom_paquet


### Réseau: 
Une connexion Internet:

-    Pouvoir se connecter sur une autre machine avec ssh: 

requiert le paquet openssh-client;
ip locale de la machine sur laquelle on cherche à se connecter: *ip addr show*
*ssh nom_utisateur@adresse_ip_locale* 
/!\ Openssh doit etre lancé sur la machine sur laquelle on se connecte: *systemclt start openssh*


-   Permettre à une autre machine de se connecter sur la vôtre:

requiert le paquet openssh-server;
*ssh nom_utisateur@adresse_ip_locale* 
/!\ Véerifier que Openssh est lancé: *systemclt status openssh*, si il n'est pas lancé: *systemclt start openssh*


-   Installer un serveur web capable de lire vos pages perso (userdir):

requiert le paquet apache2;
mkdir ~/public_html
Tous les fichiers présents dans ce dossiers seront accessibles à l'URL: localhost/~nom_utilisateur/ ou adresse_ip_locale/~nom_utilisateur depuis un navigateur web
/!\ Apache2 doit etre lancé *systemclt status apache2* pour vérifier si il est lancé, si ce n'est pas le cas *systemclt start apache2*


### Sauvegardes:

-   Faire une archive d'un répertoire (et de ses sous répertoires):

tar cfvj nom_archive.gz.bz2 /chemin/fichier

-   Copier l'archive sur une clé USB:

cp /chemin/fichier/source /media/usb/chemin/destination/
    
-   Copier l'archive via scp (vous pouvez vous entraîner sur localhost):

scp -r /chemin/source/fichier@adresse_ip_locale_machine_destinataire:/répertoire/destination


### Services (voir systemd ou autre selon OS)

-   Savoir démarrer/stopper un service:

systemctl start nom_service : démarrer un service; 

systemctl stop nom_service: stop un service


-   Savoir en vérifier l’état:

systemctl status nom_service

-   Savoir aﬀicher les messages d’erreur:

sudo journalctl -u nom_service | grep "failed"


### Divers:

-   Comment faire pour que le stagiaire n’ait pas accès aux données de votre compte ?

chmod 700 ~ : permet de restreindre son home aux autres utilisateurs.
