## Chapitre 5 : Configurations de VirtualHost HTTPS 443 LocalHost

Voici un exemple de configuration pour le port 443 (HTTPS) avec SSL et la redirection du port 80 :
Avant de configurer le VirtualHost pour le port 443 avec SSL, nous devons installer et configurer openssl pour générer les certificats SSL. Voici les étapes à suivre :

1. **Installation de openssl** :

   Assurez-vous d'avoir les droits d'administration (root) sur votre serveur et exécutez les commandes suivantes pour installer Certbot :

   ```bash
   $ sudo apt-get update
   $ sudo apt-get install openssl
   ```
 **Génération des certificats SSL (Auto Signé) :**
  Une fois openssl installé, exécutez la commande suivante pour générer les certificats SSL :  
  Basic Syntaxe:
  ```bash
   $ sudo openssl req -x509 -newkey rsa:2048 -keyout mykey.key -out mycert.pem -days 365 -nodes -subj "/C=US/ST=New York/L=New York/O=My Organization/CN=localhost /emailAddress=admin@example.com"'
   ```
   
   *Activé le module SSL : *
   ```bash
   $ sudo a2enmod ssl
   ```
   Desactivé l'ancienne config par defaut SSL :
   ```bash
   $ sudo a2dissite default-ssl.conf 
   ```
   Activé la nouvelle configuration VirtualHost integrant la partie SSL :
   ```bash
   $ sudo a2ensite http_445.conf
   ```
   
   
   
   
  
 
 
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

<VirtualHost *:443>
    # Définit le VirtualHost pour le port 443.
    ServerName localhost
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

    
</VirtualHost>
```
