CONFIGURER LES SITES SUR VIRTUALHOSTS 
/etc/apache2/sites-available/a.example.com.conf

<VirtualHost *:80>
    ServerName a.example.com
    DocumentRoot /var/www/a.example.com
</VirtualHost>
/etc/apache2/sites-available/b.example.com.conf

<VirtualHost *:80>
    ServerName b.example.com
    DocumentRoot /var/www/b.example.com
</VirtualHost>
Cette configuration de base suffit pour faire vivre les deux sites! le *:80 signifie qu’Apache envisagera d’utiliser cet hôte virtuel pour toute demande arrivant sur le port 80. Ils seront dissipés plus tard par le ServerName déclarations.


ACTIVATION DES HOTES VIRTUELS
Ajout d’un hôte virtuel à sites-available le fait disponible mais pas actif. Vous devez activer manuellement chaque site que vous souhaitez utiliser. Les configurations d’hôte virtuel à activer doivent être liées par un lien symbolique dans /etc/apache2/sites-enabled (ou alors /etc/httpd/sites-enabled).

Sur les systèmes Debian, vous pouvez utiliser le a2ensite commande pour simplifier cette étape:

a2ensite a.example.com
a2ensite b.example.com
Sur les autres distributions, utilisez le ln commande pour créer un lien symbolique manuellement.

sudo ln -s /etc/httpd/sites-available/a.example.com.conf /etc/httpd/sites-enabled/a.example.com.conf
sudo ln -s /etc/httpd/sites-available/a.example.com.conf /etc/httpd/sites-enabled/b.example.com.conf
Enfin, redémarrez Apache pour appliquer votre nouvelle configuration. Les modifications d’hôte virtuel nécessitent un redémarrage du serveur après les avoir ajoutées à sites-enabled.