### TP 1.2 - Nicolas PIPLARD - 07/09/2020



### I .MANIPULATION DES FICHIERS ET REPERTOIRES



#### Exercice 1:

La racine du système contient tous les répertoires principaux.

Nous avons :

| Dossier        | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| **bin**        | Exécutables essentiels au système, utilisables par tous les utilisateurs (ls pwd cp) |
| **boot**       | Ensemble des fichiers permettant à Linux de démarrer         |
| **dev**        | Point d'entrée de tous les périphériques (disque dur, écran, partition, consoles TTY) |
| **etc**        | Ce dossier contient les commandes et fichiers nécessaires à l'administrateur système (XXX.conf, passwd, inittab, runlevels) |
| **home**       | Répertoire personnel des utilisateurs                        |
| **lib**        | Ce dossier contient les bibliothèques partagées essentielles au système lors du démarrage |
| **lib64**      | idem /lib mais pour les 64bits (parfois, on trouvera lib et lib32. Dans ce cas, lib = 64bits et lib32 = 32bits) |
| **mnt /media** | Ce dossier contient les point de montage des partitions temporaires (clés USB, partitions de données) |
| **opt**        | Répertoire générique pour l'installation de programmes compilés par |
| **proc**       | Ce dossier n'existe pas physiquement sur un disque, elle est créée par le noyau dans la mémoire. Cette partition permet de donner des informations sur le système. |
| **root**       | Répertoire personnel de l'administrateur                     |
| **sbin**       | Ce dossier contient les programmes système essentiels utilisables par l'administrateur uniquement. |
| **srv**        | Ce dossier n'est pas présent dans toutes les distributions. C'est un répertoire de données pour divers services (stockage des documents de comptes FTP, ou pages de sites web) |
| **tmp**        | Répertoire fichiers temporaires                              |
| **usr**        | Ce dossier contient des programmes installés (`/usr/bin`) avec leurs librairies (`/usr/lib` ou `/usr/lib64`) tels que firefox, libreoffice, ... quelques programmes réservés à l'administrateur système (`/usr/sbin`) et les fichiers de code source (`/usr/src`) |
| **var**        | Ce dossier contient les données variables (fichiers de log) mais parfois les bases de données (`/var/lib/mysql`) et les pages de site web (`/var/www/html`) |
| **sys**        | Ce dossier permet de connaître les informations sur le système et ses composants (matériels attachés et installés) d'une manière structurée |

source : [rebootinformatique.org](https://www.rebootinformatique.org/tutos/cours/fichiers_systeme/co/arborescence.html#:~:text=Comme%20tout%20syst%C3%A8me%2C%20Linux%20poss%C3%A8de,comme%20sous%20MS%2DDOS)



#### Exercice 2:

##### 2.1)

L'option -R de la command **ls** permet d'afficher récursivement le contenu des sous-répertoires.

##### 2.2)

Par défaut, les fichiers sont triés par ordre alphabétique en fonction de la première lettre des fichiers. Plus précisément, l'ordre générale de classement de dossiers et fichiers est le suivant : **ponctuations, chiffres, majuscules, minuscules, selon l'ordre défini par la table des caractères ASCII**.

La commande **sort** permet de changer l'ordre d'affichage. Notamment avec l'option **-r** qui permet d'inverser l'ordre de classement. l'option **-t** qui permet de trier en fonction de la date de dernière modification du fichier ou dossier.

Voici toutes les options de la commande sort :

| **Option** | **Signification**                                            |
| ---------- | ------------------------------------------------------------ |
| **-b**     | Saute les colonnes constituées de blancs.                    |
| **-d**     | Trie de type dictionnaire.                                   |
| **-n**     | Trie par ordre numérique.                                    |
| **-f**     | Aucune différentiation n'est faite entre minuscules et majuscules. |
| **-b**     | Ignore les espaces placés en début de champ.                 |
| **-r**     | Trie inverse.                                                |
| **-M**     | Trie chronologiquement les mois.                             |
| **-t:**    | Trie suivants les champs séparés par les caractères deux points (`` **:**''). |

##### 2.3)

Voici les commandes à réaliser :

```bash
cd && ls -t
ou
cd && sort -t
```

##### 2.4)



##### 2.5)

La commande **ls** permet de lister le contenu d'un répertoire, à savoir ses fichiers et dossiers.

La commande **ls** suivi de l'argument **-l** permet, en plus du nom, d'afficher le type du fichier, les permissions d'accès, le nombre de liens physiques, le nom du propriétaire et du groupe, la taille en octets, et l'horodatage.

##### 2.6)

Voici la commande à réaliser :

```bash
ls -l dossier/
```



#### Exercice 3:

##### 3.1)

```bash
mkdir d1 && mkdir d2 && mkdir d3
```

##### 3.2)

```bash
rmdir d*
```

##### 3.3)

Le répertoire **mkdir** est créé

![image-20200907170118352](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200907170118352.png)

##### 3.4)

Pour trouver les fichiers cachés on fait :

```bash
ls -la
```

##### 3.5)

Oui, mkdir dispose de plusieurs options :

| Option | Description                                                  |
| ------ | ------------------------------------------------------------ |
| -m     | Créer les répertoires avec le mode d'accès indiqué.          |
| -p     | S'assurer que chaque répertoire indiqué existe. Créer les répertoires parents manquants. |

##### 3.6)

La commande ne peut que fonctionner avec l'option **-p** :

```bash
mkdir -p Rapport/annexes
```

##### 3.7)

L'option **-p** permet cela.

##### 3.8)

L'option **-m** permet cela.

##### 3.9)

L'exécution de cette commande va supprimé le répertoire tutu. L'option **-p** permet de supprimé également les répertoires parents s'ils deviennent vides après la suppression des répertoires mentionnés en arguments.

##### 3.10)

Le dossier toto et dossier enfant tutu seront créés.



#### Exercice 4:

##### 4.1)

Oui, l'option **-R** ou **-r** permet de le faire de façon récursive avec tous les fichiers et sous-dossier.

```bash
cp -R /dossier /destination
```

##### 4.2)

Une erreur s'affiche, **cp: -r not specified; omitting directory 'mkdir'**

Il nous montre qu'il faut utiliser l'option **-R**

Une fois l'option **-R**, la commande créé une copie de /dossier dans /destination.

##### 4.3)

Le fichier de destination est écrasé et remplacé par le nouveau.

##### 4.4)

Les 3 fichiers **fichier1, fichier2 et fichier3** sont copiés dans **/répertoire**.

##### 4.5)

Pour renommer un répertoire, on utilise la commande **mv**, comme il n'y a pas de commande **"rename"**, on doit déplacer le dossier et changer son nom de destination pour le renommer.

```bash
mv dossier/ nouveau-nom-du-dossier/
```

Si le nom du dossier existe déjà, le dossier sera alors déplacé dans le dossier de destination, et il ne sera donc pas renommé.

##### 4.6)

Pour déplacer un fichier et changer son nom en même temps il faut lui donner le chemin que l'on veut du dossier et à la suite le nouveau nom du fichier :

![image-20200910110413103](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910110413103.png)

Si le nom du fichier existe déjà, il sera alors écrasé par le nouveau.

##### 4.7)

Pour ce qui est du dossier, le même principe s'applique que pour le déplacement et renommage d'un fichier.

Si, pour le dossier, lors du déplacement et du renommage il s'avère qu'un dossier est déjà présent avec le même nom, alors le dossier sera déplacé dans le dossier portant le même nom et deviendra alors un sous-dossier de celui-ci.

##### 4.8)

L'option **-i** permet de demander confirmation avant écrasement d'un fichier déjà existant.

L'option **-f** permet de forcer l'écrasement d'un fichier sans demander confirmation.

D'après la documentation de la commande **mv**, l'option **-f** prend le dessus sur l'option **-i**, la commande sera donc semblable à **mv -f fichier1 fichier2**.



### II. Commandes de base (suite). 



#### Exercice 1:

##### a) Compter le nombre de fichiers se trouvant dans le répertoire courant : 

```bash
ls | wc -l
```

Pour exemple, si cela donne **"12"** il y a alors 12 fichiers/dossiers dans le dossier courant. Cette commande n'est pas récursive.

##### b) Afficher (en utilisant le fichier /etc/passwd) la liste des utilisateurs pouvant travailler en bash classée par ordre alphabétique :

```bash
cat /etc/passwd | sort | grep bash$
```

![image-20200910215816700](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910215816700.png)

#### Exercice 2:

Voici le résultat de exécution :

![image-20200910214339432](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910214339432.png)



#### Exercices simples :

![image-20200910214534156](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910214534156.png)

##### Exercice 1:

![image-20200910214711403](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910214711403.png)

**ls** permet seulement d'afficher les fichier et dossier.

**ls -l** permet, en plus du nom, d'afficher le type du fichier, les permissions d'accès, le nombre de liens physiques, le nom du propriétaire et du groupe, la taille en octets, et l'horodatage.

**ls -l** permet d'afficher les même caractéristique que **ls -l** mais, avec tous les fichiers/dossiers cachés et également les fichiers commençant par **"."**.



##### Exercice 2:

```bash
set
man set
set --help
```

La commande **set** permet d'afficher toutes les variables d'environnements.

![image-20200910215233368](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910215233368.png)

##### Exercice 3:

```bash
alias ls='ls --color=auto'
```

La commande **rm** à été remplacé par **rm -i** grâce à l'alias (on a créé un alias pour la commande **rm -i**). De ce fait, la commande **rm *** nous demande une confirmation avant suppression.

![image-20200910215527622](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910215527622.png)

##### Exercice 4:

**ls -al > listefic**, cette commande va écrire le résultat de la commande **ls -al** dans le fichier **listefic**.

**more listefic** va lire le fichier listefic avec des pages.

**cat listefic** va ouvrir le fichier **listefix** dans l'éditeur.

![image-20200910220448406](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910220448406.png)

##### Exercice 5:

Exemple si tmpo et tempo sont dans le répertoire courant.

```bash
cp -r ~/tmpo/exos ~/tempo
```

##### Exercice 6:

Pour différencier un fichier d'un répertoire on regarde le premier caractère de la ligne affiché, s'il s'agit d'un **d**, alors c'est un dossier pour directory. Si c'est un tiret, alors c'est un fichier.

![image-20200910220818530](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910220818530.png)

##### Exercice 7:

```bash
rm -r ~/tempo
```

![image-20200910221118400](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910221118400.png)

##### Exercice 8:

La commande **df** (disk free) permet d’afficher la taille de l’espace disque occupée et la taille de l’espace disque libre.

La commande **du** (disk usage) permet d’afficher la taille d’un répertoire et de tous les sous répertoires qu’il contient (récursivement).

![image-20200910221520722](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910221520722.png)

##### Exercice 9:

La commande **who** permet de savoir qui est connecté sur le système et que font-ils.  

La commande **id** permet d'afficher tous les groupes et l'uid de l'utilisateur actuel. 

(Vous avez marqué la réponse dans la question)

![image-20200910221626822](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200910221626822.png)