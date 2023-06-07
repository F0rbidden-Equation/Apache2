## Modèle 3 : Sécurité avancée avec en-têtes de sécurité

Ce modèle inclut la configuration des en-têtes de sécurité HTTP pour renforcer la sécurité du site web et prévenir les attaques telles que le détournement de clics, le chargement de contenu mixte et les attaques XSS.

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module headers
    <IfModule mod_headers.c>
        # Configuration des en-têtes de sécurité
        Header always set X-XSS-Protection "1; mode=block"
        Header always set X-Content-Type-Options "nosniff"
        Header always set Content-Security-Policy "default-src 'self'"
        Header always set X-Frame-Options "SAMEORIGIN"
        Header always set Referrer-Policy "same-origin"
        Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"
    </IfModule>
    
    # Autres directives de configuration spécifiques aux en-têtes de sécurité
    
</VirtualHost>
