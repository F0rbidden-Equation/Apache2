## Modèle 2 : Sécurité renforcée avec ModSecurity (WAF)

Ce modèle utilise le module ModSecurity pour renforcer la sécurité de votre serveur Apache2 en mettant en place un pare-feu d'application Web (WAF) pour détecter et bloquer les attaques Web courantes telles que les injections SQL, les attaques par script intersite (XSS), les tentatives de détournement de session, etc.

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module ModSecurity
    <IfModule mod_security2.c>
        SecRuleEngine On
    </IfModule>
    
    # Autres directives de configuration spécifiques à ModSecurity
    
</VirtualHost>
