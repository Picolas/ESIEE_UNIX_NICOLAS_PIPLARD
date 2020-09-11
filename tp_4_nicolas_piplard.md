# TP 4 - Nicolas PIPLARD - E3FIC - 11/09/2020



## 2.1. Commmande test



#### Ecrivez un script qui dit si le paramètre passé est un fichier/dossier/n'existe pas :

```bash
#!/bin/bash
# On check si il y a bien au moin un argument en paramètre
if [ $# -eq 0 ]; then
    echo "Vous devez passer au moin 1 paramètre"
    exit 1
fi
# On bouble le nombre de paramètres et affiche chaque résultat dans le shell
for i in $@
    do
        if [ -f $i ]; then
            echo "$i est un fichier"
        elif [ -d $i ]; then
            echo "$i est un dossier"
        else
            echo "$i n'existe pas"
        fi
done
```

![image-20200911094328257](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911094328257.png)



#### Ecrivez un script qui n'affiche que les répertoires : 

```bash
#!/bin/bash
for i in *; do
    if [ -d $i ]; then
        echo "dossier : $i"
    fi
done
```



#### Ecrivez un script qui n'affiche que lesfichier

```bash
#!/bin/bash
for i in *; do
    if [ -f $i ]; then
        echo "fichier : $i"
    fi
done
```



#### Ecrivez un script qui donne le nombre de fichiers et le nombre de répertoires : 

```bash
#!/bin/bash
d=0
f=0
for i in *; do
    if [ -d $i ]; then
        ((d=d+1))
    elif [ -f $i ]; then
        ((f=f+1))
    fi
done
echo "Il y a $d dossier(s)"
echo "Il y a $f fichier(s)"
```

![image-20200911095040541](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911095040541.png)



## 2.2. Commande case



#### En utilisant la structure case, écrire un script qui affiche le menu/demande à l'utilisateur de saisir une option du menu/affiche l'option qu'il a choisie :

version simple demandé :

```bash
#!/bin/bash
echo "===== Menu ====="
options=("1) Option 1" "2) Option 2" "3) Option 3" "4) Option 4")
for opt in "${options[@]}"; do
    echo $opt
done
echo "Veuillez choisir un option :"
read choice
case $choice in
    1)
        echo "Vous avez choisit l'option 1"
        ;;
    2)
        echo "Vous avez choisit l'option 2"
        ;;
    3)
        echo "Vous avez choisit l'option 3"
        ;;
    4)
        echo "Vous avez choisit l'option 4"
        ;;
    *) echo "Option invalide";;
esac
```

![image-20200911101502934](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911101502934.png)



version amélioré avec le select, c'est-à-dire que le menu se réaffiche à la fin de chaque traitement :

```bash
#!/bin/bash
echo "Choisissez une option :"
options=("Option 1" "Option 2" "Option 3" "Option 4" "Quitter")
select opt in "${options[@]}"
do 
    case $opt in
        "Option 1")
            echo "Vous avez choisit l'option 1"
            ;;
        "Option 2")
            echo "Vous avez choisit l'option 2"
            ;;
        "Option 3")
            echo "Vous avez choisit l'option 3"
            ;;
        "Option 4")
            echo "Vous avez choisit l'option 4"
            ;;
        "Quitter")
            break
            ;;
        *) echo "Option invalide";;
    esac
done
```

![image-20200911100411892](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911100411892.png)



#### En utilisant la structure for, écrire un programme qui donne les valeurs de Y d'une fonction pour les valeurs de X allant de -10 à 10 avec un incrément de 1 :



##### Réalisez le traitement pour la fonction y=x^2 :

```bash
#!/bin/bash
y=0
for (( x=-10; x<=10; x++ )) do
    ((y=$x**2))
    echo "pour x = $x"
    echo "y = $y"
done
```

![image-20200911102630831](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911102630831.png)



##### Réécrivez le programme avec la structure répéter .... jusqu'à :

```bash
#!/bin/bash
y=0
x=-10
until [ $x -gt 10 ]; do
    ((y=$x**2))
    echo "pour x = $x"
    echo "y = $y"
    ((x=$x+1))
done
```



##### Adapter le script afin que les bornes -x et +x soient passées en paramètres au script :

```bash
#!/bin/bash
y=0
xmin=-10
xmax=10
echo "Saisissez -x :"
read xmin
echo "Saisissez +x :"
read xmax
if [ $xmin -gt $xmax ]; then
    echo "-x ne doit pas être supérieur à +x"
    exit 1
fi
until [ $xmin -gt $xmax ]; do
    ((y=$xmin**2))
    echo "pour x = $xmin"
    echo "y = $y"
    ((xmin=$xmin+1))
done
```

![image-20200911103841503](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911103841503.png)



##### Modifiez le script de façon à ce que l'on puisse passer en paramètre l'incrément :

```bash
#!/bin/bash
y=0
xmin=-10
xmax=10
increment=1
echo "Saisissez -x :"
read xmin
echo "Saisissez +x :"
read xmax
echo "Saisissez l'increment :"
read increment
if [ $xmin -gt $xmax ]; then
    echo "-x ne doit pas être supérieur à +x"
    exit 1
fi
if [ $increment -le 0 ]; then
    echo "l'increment doit être supérieur à 0"
    exit 1
fi
until [ $xmin -gt $xmax ]; do
    ((y=$xmin**2))
    echo "pour x = $xmin"
    echo "y = $y"
    ((xmin=$xmin+$increment))
done
```

![image-20200911104106377](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911104106377.png)



## 2.4. Commande if



##### En utilisant la structure if, écrire un script qui : afficher le menu/demande à l'utilisateur de saisir une option du menu/affiche à l'utilisateur l'option qu'il a choisie

```bash
#!/bin/bash
echo "===== Menu ====="
options=("1) Option 1" "2) Option 2" "3) Option 3" "4) Option 4")
for opt in "${options[@]}"; do
    echo $opt
done
echo "Veuillez choisir un option :"
read choice
if [ $choice == 1 ]; then
    echo "Vous avez choisi l'Option $choice"
elif [ $choice == 2 ]; then
    echo "Vous avez choisi l'Option $choice"
elif [ $choice == 3 ]; then
    echo "Vous avez choisi l'Option $choice"
elif [ $choice == 4 ]; then
    echo "Vous avez choisi l'Option $choice"
else
    echo "Votre choix n'est pas valide"
fi
```

![image-20200911105728056](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911105728056.png)



##### Construisez un script qui permet de n'afficher que les enregistrements dont la valeur est supérieure à 10 : 

```bash
#!/bin/bash
while IFS=' ', read -r word number
do
    if [ $number -gt 10 ]; then
        echo $number
    fi
done < data.txt
```

![image-20200911111857294](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911111857294.png)



## 2.5. Commande until



##### En utilisant la structure until...do...done, écrire un script qui : demande à un utilisateur de saisir une commande / exécute la commande ou affiche un message d'erreur si la commande ne s'est pas déroulée. / répète cette opération tant que l'utilisateur le désire :

```bash
#!/bin/bash
response=y
until [ $response == "n" ]; do
    echo "Veuillez saisir une commande à éxécuter :"
    read commande
    $commande 2>/dev/null
    # 2>/dev/null permet d'éviter d'avoir un message d'erreur si la commande n'existe pas:ou tout autre message d'erreur.
    if [ $? -ne 0 ]; then
        echo "La commande : $commande a échoué"
    fi
    # On demande à l'utilisateur si il veut continuer
    echo "Voulez-vous éxécuter une autre commande ? (y/n)"
    read response
done
```

![image-20200911113621913](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911113621913.png)



## 2.6. Commande while



##### En utilisant la structure while, écrire un script qui : Tant que l'utilisateur n'a pas tapé 9 : / affiche un menu / demande à l'utilisateur de saisir une option du menu : 

###### 	1 Afficher la date (date)" 

###### 	2 Afficher le nombre de personnes connectées (who)" 

###### 	3 Afficher la liste des processus (ps)" 

###### 	9 Quitter"

```bash
#!/bin/bash
choice=0
while [ $choice -ne 9 ]; do
    echo "===== Menu ====="
    options=("1) Afficher la date (date)" "2) Afficher le nombre de personnes connectées (who)" "3) Afficher la liste des processus (ps)" "9) Quitter")
    for opt in "${options[@]}"; do
        echo $opt
    done
    echo "Veuillez choisir une option :"
    read choice
    case $choice in
        1)
            date
            ;;
        2)
            who
            ;;
        3)
            ps
            ;;
        9)
            ((choice=9))
            ;;
        *) echo "Option invalide";;
    esac
done
```

![image-20200911114813131](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911114813131.png)



## 2.7. Commande select



##### Vous allez à l'aide de la fonction select réaliser un menu à quatre options pour un utilisateur.

##### Le script doit boucler tant que l'utilisateur n'a pas choisi de quitter. 

###### 	Option 1 : Afficher la liste des utilisateurs connectés 

###### 	Option 2 : Afficher la liste des processus 

###### 	Option 3 : Afficher à l'utilisateur son nom, son UID, son GID, son TTY 

###### 	Option 4 : Quitter

```bash
#!/bin/bash
echo "Choisissez une option :"
options=("Option 1" "Option 2" "Option 3" "Quitter")
select opt in "${options[@]}"
do 
    case $opt in
        "Option 1")
            who
            ;;
        "Option 2")
            ps
            ;;
        "Option 3")
            GID=`id -g $USER`
            TTY=`tty`
            echo "Nom : $USER - UID : $UID - GID : $GID - TTY : $TTY"
            ;;
        "Quitter")
            break
            ;;
        *) echo "Option invalide";;
    esac
done
```

![image-20200911120837126](C:\Users\Picolas\AppData\Roaming\Typora\typora-user-images\image-20200911120837126.png)