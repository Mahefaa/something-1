## _Utilisation du fichier json en utilisant JS HTML CSS BOOTSTRAP WAMP SERVER_
Avant tout , il vous faut d'abord installer wamp serveur dans votre machine 

# Installation de wamp seveur sur windows 10 :
Voici un lien vous menant vers comment installer wamp serveur sur windows 10

```sh
https://waytolearnx.com/2020/01/comment-installer-wampserver-sur-windows-10.html

```

Pour s'assurer que ces codes marchent , veuillez mettre le dossier "data" dans wamp64 / www 

# Et pour le voir dans le navigateur , tapez :

```sh

localhost/data/index.html

```
# Une autre façon de l'afficher sur le navigateur est de changer la base_url ,pour ce faire il va falloir faire quelques configurations :
Allez dans le dossier :

```sh
C:\wamp64\bin\apache\apache2.4.46\conf

```

Puis , ouvrez le fichier httpd.conf et décommentez :

```sh
Include conf/extra/httpd-vhosts.conf
```

Ensuite dans le même dossier conf , allez dans le dossier : "Extra"
On va apporter quelques modifications dans le fichier "httpd-vhosts.conf" (fichier de configuration du vhost)  
 > Copiez ceci dans le fichier
``` sh
<VirtualHost *:80>
DocumentRoot "C:/wamp64/www/data/"
ServerName web
ServerAlias web
<Directory "C:/wamp64/www/data/">
  Options +Indexes +Includes +FollowSymLinks +MultiViews
    AllowOverride All
    Require local
  # Order allow , deny
  # Allow from all
</Directory>
</VirtualHost>
``` 

Dernière configuration à faire 
Allez dans le repertoire :
```sh
C:\Windows\System32\drivers\etc
```
Dans le dossier etc , vous y trouverez un fichier "hosts" , 
sans rien supprimer , ajoutez ceci dans ce fichier 

```sh

127.0.0.1 web

```

>Vous n'avez plus qu'à redémarrez le serveur et au lieu de localhost vous pourriez juste tapez comme base url : :rocket:

```sh
web/data
```

 
