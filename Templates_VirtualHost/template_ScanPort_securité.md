## Modèle 8 : Protection contre les attaques de scan de ports avec le module mod_antiloris

Ce modèle utilise le module mod_antiloris pour protéger votre serveur Apache2 contre les attaques de scan de ports. Le module mod_antiloris est conçu pour détecter et bloquer les tentatives d'établissement de connexion excessives, souvent utilisées dans les attaques de type DDoS.

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module mod_antiloris
    <IfModule mod_antiloris.c>
        DOSHashTableSize 3097
        DOSPageCount 2
        DOSSiteCount 50
        DOSPageInterval 1
        DOSSiteInterval 1
        DOSBlockingPeriod 10
        DOSLogDir /var/log/apache2/mod_evasive
    </IfModule>
    
    # Autres directives de configuration spécifiques à mod_antiloris
    
</VirtualHost>
