## Chapitre 5 : Configurations de VirtualHost HTTPS 443

Voici un exemple de configuration pour le port 443 (HTTPS) avec SSL et la redirection du port 80 :
Avant de configurer le VirtualHost pour le port 443 avec SSL, nous devons installer et configurer Certbot pour générer les certificats SSL. Voici les étapes à suivre :

1. **Installation de Certbot** :

   Assurez-vous d'avoir les droits d'administration (root) sur votre serveur et exécutez les commandes suivantes pour installer Certbot :

   ```bash
   $ sudo apt-get update
   $ sudo apt-get install certbot python3-certbot-apache
   ```
   
```apacheconf
<VirtualHost *:443>
    # Définit le VirtualHost pour le port 443.
    ServerName example.com
    # Spécifie le répertoire racine du site web.
    DocumentRoot /var/www/html
    # Fichier de log des erreurs.
    ErrorLog ${APACHE_LOG_DIR}/error.log
    # Fichier de log des accès.
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # Configuration pour activer SSL
    SSLEngine on
    SSLCertificateFile /chemin/vers/certificat.pem
    SSLCertificateKeyFile /chemin/vers/clé_privée.pem

    # Redirection du port 80 vers le port 443
    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

    # Autres directives de configuration spécifiques au VirtualHost pour le port 443
</VirtualHost>
```

