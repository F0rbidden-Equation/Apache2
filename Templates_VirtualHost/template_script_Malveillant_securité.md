## Modèle 9 : Protection contre les attaques par scripts malveillants avec le module mod_cgi

Ce modèle utilise le module mod_cgi pour renforcer la sécurité des scripts CGI (Common Gateway Interface) exécutés sur votre serveur Apache2. Il comprend des directives visant à limiter les vulnérabilités potentielles associées à l'exécution de scripts CGI.
###  Protection contre les attaques par scripts malveillants avec le module mod_cgi
Pour installer le module mod_cgi  :
```bash
sudo apt-get install libapache2-mod-cgi
```
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Désactiver l'exécution des scripts CGI dans le répertoire racine
    <Directory /var/www/html>
        Options -ExecCGI
        AddHandler cgi-script .cgi .pl
        Require all granted
    </Directory>
    
    # Limiter les permissions d'exécution des scripts CGI dans d'autres répertoires
    <Directory /var/www/cgi-bin>
        Options +ExecCGI -Indexes
        AllowOverride None
        Require all granted
    </Directory>
    
    # Autres directives de configuration spécifiques à mod_cgi
    
</VirtualHost>
