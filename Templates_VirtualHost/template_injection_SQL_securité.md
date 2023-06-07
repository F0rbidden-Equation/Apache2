## Modèle 7 : Protection contre les attaques par injection de code SQL avec le module mod_security

Ce modèle utilise le module mod_security pour protéger votre serveur Apache2 contre les attaques par injection de code SQL. Le module mod_security est un pare-feu d'application web qui surveille les requêtes HTTP et les filtre en fonction de règles de sécurité pour bloquer les attaques.
### ModSecurity
Pour installer le module ModSecurity pour Apache2 :
```bash
     sudo apt-get install libapache2-mod-security2
     sudo service apache2 restart
```
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module mod_security
    <IfModule mod_security.c>
        SecRuleEngine On
        
        # Configuration des règles de sécurité pour bloquer les attaques par injection de code SQL
        SecRule REQUEST_URI|ARGS|REQUEST_HEADERS "(?:\b(?:s(?:elect\b.+from|(?:trun|upd)ate)\b|\b(?:inser|delet)e\b.+into|union.+select)\b|drop\b(?:\s*(?:database|table|column)\s*|user\s*)\b|alter\b.+table\s*(?:user\s*|admin\s*)\b|\bcreate\b(?:\s*(?:database|table|index)\s*|user\s*)\b)\b)" \
        "phase:2,rev:'1',deny,id:'100001',log,msg:'Possible SQL injection attack'"
    </IfModule>
    
    # Autres directives de configuration spécifiques à mod_security
    
</VirtualHost>
