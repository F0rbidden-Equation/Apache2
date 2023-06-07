## Modèle 1 : Sécurité de base

Ce modèle comprend des directives de base pour la sécurité d'Apache2, telles que la désactivation de l'affichage des index des répertoires, l'interdiction de l'override des configurations par les fichiers .htaccess, et la restriction d'accès par adresse IP.

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Désactiver l'affichage des index des répertoires
    Options -Indexes
    
    # Interdire l'override des configurations par les fichiers .htaccess
    AllowOverride None
    
    # Restreindre l'accès par adresse IP
    <Directory /var/www/html>
        Order Deny,Allow
        Deny from all
        Allow from 192.168.0.0/24
    </Directory>
    
    # Autres directives de configuration spécifiques à la sécurité de base
    
</VirtualHost>
