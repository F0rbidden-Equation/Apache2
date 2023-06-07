## Modèle 10 : Protection contre les attaques par inclusion de fichiers avec le module mod_include

Ce modèle utilise le module mod_include pour renforcer la sécurité contre les attaques par inclusion de fichiers. Il inclut des directives visant à limiter les vulnérabilités potentielles associées à l'inclusion de fichiers sur votre serveur Apache2.
### ModInclude
Pour installer le module mod_include pour Apache2 :
```bash
     sudo apt-get install libapache2-mod-include
     sudo service apache2 restart
```
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Désactiver l'inclusion de fichiers dans le répertoire racine
    <Directory /var/www/html>
        Options -Includes
        AllowOverride None
        Require all granted
    </Directory>
    
    # Limiter les options d'inclusion de fichiers dans d'autres répertoires
    <Directory /var/www/includes>
        Options +Includes -Indexes
        AddType text/html .shtml
        AddOutputFilter INCLUDES .shtml
        Require all granted
    </Directory>
    
    # Autres directives de configuration spécifiques à mod_include
    
</VirtualHost>
