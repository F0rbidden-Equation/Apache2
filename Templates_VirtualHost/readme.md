# Tutoriel Apache2

## Chapitre 5 : Configurations de VirtualHost HTTP 80

Les configurations de VirtualHost vous permettent de définir différents sites web sur votre serveur Apache2. Voici un exemple de configuration pour le port 80 (HTTP) :

```apacheconf
<VirtualHost *:80>
    # Définit le VirtualHost pour le port 80.
    ServerName example.com
    # Spécifie le répertoire racine du site web.
    DocumentRoot /var/www/html
    # Fichier de log des erreurs.
    ErrorLog ${APACHE_LOG_DIR}/error.log
    # Fichier de log des accès.
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
