# SAE_1.03 - Installation d'une machine virtuelle sur Debian:


## 1.0. Prérequis:

- Il sera  nécessaire de posséder **une connexion à internet** tout le long de l'insatallation, pour pouvoir installer tous les logiciels et se connecter à cette machine à distance par exemple. 

- Nous avons choisi un **iso de debian** en *64 bits* disponible au téléchargement sur ce lien:
<https://www.debian.org/distrib/netinst>.

- VirtualBox sera également à posséder; si ce n'est pas votre cas il est possible de télécharger le logiciel sur ce lien: 
<https://www.virtualbox.org/wiki/Downloads>.

- Un espace de stockage 10Go libre sera nécessaire pour installer tous les logiciels; (taille recommandée 20Go).

## 2.0. Début de l'installation:

Lancez l'application *VirtualBox*. Tout d'abord il faut créer une nouvelle machine, depuis le bouton **nouveau**. 
Choisissez un nom de machine, le répertoire dans lequel vous voulez installer cette machine ainsi que pour le type de système *linux* et pour la version: *debian 64bits*.

Nous commancerons par faire une **installation simple** c'est à dire sans **interface graphique**. 
L'insatallation est désormais lancée, vos péréphériques seront automatiquement détecté. Si un problème est détecté sur un de vos péréphérique, un message d'erreur vous l'indiquera. Vous devrez choisir manuellement le péréphérique adéquat et éventuellement installer des pilotes. 

(**A tout moment lors de l'installation, si vous faites une erreur, vous pouvez revenir en arrière et sélectionner l'étape à laquelle vous voulez recommencer la configuration.**)

### 2.1. Configuration du réseau:
Entrez le nom que vous voulez donnez à votre machine ainsi que le domaine, en étant sur un réseau local, vous devez saisir le même nom de domaine pour toutes vos machines connectées dessus.

### 2.2. Création des utilisateurs:
Vous devez ensuite entrer le mot de passe de **root**, c'est à dire le compte utilisateur disposant de tous les **droits d'administration**.

Créer ensuite votre profil personnel avec son nom et son mot de passe.
Vous devez ensuite *partitionner* votre-vos disque(s), vous pouvez sélectionner *partitionnement assisté* pour plus de facilité.

Nous ne choisirons de ne pas installer les différents *répertoires personnel* sur des partitions différentes pour plus de facilité. Une fois cela fait, appliquez les changements sur votre disque et **l'installation du système** de base débutera.

### 2.3. Outil de Gestion des Paquets:

Si vous n'avez pas d'autres disques à partitionner séléctionner *non*, sinon réitérez le même processus.
En france séléctionner comme **miroir de l'archive débian**: *ftp.fr.debian.org*. 

De plus si vous passez par un proxy pour accéder à internet veuillez indiquer son URL, c'est à dire http:// + l'ip + le port.
Il sera donc de la forme `http://193.49.118.36:8080`; sinon laissez vide.


L'installation des paquets et des logiciels peut prendre un certain temps, pas d'inquiétude.


### 2.4. Logiciels:

Certaines distribution vous demande les logiciels à pré-installer nous allons prendre un peu d'avance et télécharger *serveur web*, *serveur ssh* et pour terminer *utilitaires usuels du système*.
Vu que nous avons de faire une installation non graphique, décochez *environnement de bureau débian* et *GNOME*, qui sont sélectionnés par défaut.

Installez le logiciel *GRUB* sur le disque que vous venez de partitionner par exemple. Il vous permettra de notamment de choisir sur quelle **système d'exploitation** vous souhaitez démarrer votre machine.

**Félicitations, vous venez de terminer l'insatallation de base de debian**


## 3. Installation de paquets:

Pour installer un paquet, c'est à dire un logiciel proposé par votre distribution, il faut saisir la commande **apt-get install nom_paquet**, par exemple *apt-get install sudo*

Si vous ne savez pas si votre logiciel est présent dans cette liste, il est possible de faire une recherche: *apt search nom_paquet*

Or, si vous ne vous etes pas connectés en tant que root, il vous sera impossible d'installer les paquets. En effet pour cela vous devez attribuer à votre utilisateur certains droits.

## 4.1. Attribution des Droits:

La première chose à faire est de se connecter en tant que root. Nous allons attribuer les droits *super-utilisateurs* à votre utilisateur. La commande *su* permet de vous connecter depuis votre session en tant que root. 

**Attention** Root est très puissant, il donc très facile de détruire toute votre installation. il est conseillé de l'utiliser pour faire le stricte minimun.

Une fois connecté en tant que root, il faut installer *sudo*, de la même manière que nous l'avons vu plus tot,(`3-`)


### 4.2. Sudo:

Pour pouvoir exécuter des commandes nécessitant les droits super-utilisateurs, il faut ajouter *sudo* devant.
*sudo apt-get install nom_paquet*


### 4.3. Ajout de groupe:

Pour que votre utilisateur passe au statut de super utilisateur, vous devez ajouter le groupe *sudo* à votre utilisateur. De manière génrale, pour ajouter un utilisateur à un groupe il faut faire la commande **gpasswd -a nom_utilisateur nom_groupe** (Remplacer *-a* par *-d* pour retirer l'utilisateur du groupe).

Tout le reste de l'installation peut désormais se faire depuis votre compte personnel, redémarrer donc votre machine et connectez sur votre utilisateur.


## 5. installation graphique

Nous allons désormais installer une interface graphique. Pour cela il faut tout d'abord choisir un **gestionnaire de bureau**. Il existe notemment **GNOME, KDE** qui sont les environnements traditionnels ainsi que **XFCE, LXDE**, plus légers. 

Nous choisirons XFCE: (*sudo apt-get install xfce4*)

Une fois fini, redémarrez votre machine et les changements apparaitrons. Si des bordures sont présentes pensez à changer la résolution depuis les paramètres d'affichage. 


## 6. Stagiaire:

### 6.1 Utilisateur Stagiaire:

Pour ajouter un nouvel utilisateur entrez la commande suivante *sudo useradd -m nom_utilisateur*. L'option *m* permet de créer un répertoire **Home** lors de sa création. Pour supprimer un utilisateur : *userdel*.
Pour l'instant, votre nouvel utilisateur ne possède pas de mot de passe, pour en ajouter un: *passwd nom_utilisateur*

### 6.2 Groupe Stagiaires:

Créons également un groupe pour pouvoir ajouter un utilisateur dedans. Pour cela: *sudo groupadd nom_groupe*; *groupdel* pour supprimer un groupe existant.


## 7. Réseau:

### 7.1 Curl:

Pour pouvoir envoyer des requetes sur des sites web et obtenir une réponse depuis le terminal il faut installer **curl**: *sudo apt-get install curl*.

### 7.2 SSH:

Le protocole **ssh** ou **Secure Shell** permet de se connecter sur une machine à distance depuis une autre de manière sécurisée.
Nous allons connecter votre virtualbox à une machine sur le meme réseau local. La première chose à faire et de modifier la configuration résseau directement depuis VirtualBox. Il faut ensuite changer l'adaptateur, et modifier *lié par* qui devrait etre de base *NAT* et le remplacer par **Pont**

Nous avons déja installé **openssh client** et **openssh serveur** mais vous devrez également le faire sur la seconde machine que vous voulez connecter.

#### 7.2.1 Statut d'un processus:

Pour pouvoir se connecter sur la machine il faut que le serveur openssh soit lancé, pour vérifier cela, il faut utiliser la commande *systemctl status openssh/nom_processus*. Sur la 3eme ligne, le statut sera affiché ainsi que depuis combien de temps il est dans cet état.

- *sudo /etc/init.d/ssh start* : lance le programme
- *sudo /etc/init.d/ssh stop* : stop le programme
- *sudo /etc/init.d/ssh reload* : relance le programme



#### 7.2.3. Connexion en locale:

Pour se connecter sur la machine:
*ssh nom@adresse_ip_locale/nom_machine*

L'adresse ip locale se trouve par la commande: *ip addr show* et est à coté d'**inet**: de la forme 192.78.189.129 par exemple.


### 7.2.4. Transmission de fichier sécurisé:

Grace à ssh, il est possible de tansférer des fichier grace à la commande **scp**:
*scp -r /chemin/fichier nom_utilisateur@adresse_ip_locale:répertoire_destination*

exemple:
scp -r Documents/IUT/1ere\ ANNEE/algo/tp bastien@192.168.43.223:~


### 7.3. Web browser - Userdir:

Pour pouvoir accéder à son espace personnel sur un serveur web, nous utilserons le paquet **apache2**.

Dans le répertoire courrant de l'utilisateur, créez un fichier **public_html** : *mkdir ~/public_html*. Tous les répertoires et documents qui se trouveront dans ce dossier seront accessibles en ligne. 


Apache2 fonctionne de la même manière que openssh, ce qui signifi que le processus doit etre lancé grace à la commande **systemctl** et porte le nom de *apache2* ( `cf 7.2.1` pour l'utilisation de *systemctl* ).

Dans votre navigateur saissez *adresse_ip_locale/~nom_utilisateur* en url. Si vous souhaitez directement vous rendre dans le répertoire *sae* : *adresse_ip_locale/~nom_utilisateur/chemin/sae*


