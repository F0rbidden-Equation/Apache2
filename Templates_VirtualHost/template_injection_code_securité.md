## Modèle 6 : Protection contre les attaques par injection de code avec le module mod_rewrite

Ce modèle utilise le module mod_rewrite pour protéger votre serveur Apache2 contre les attaques par injection de code, telles que les attaques XSS (Cross-Site Scripting) et les tentatives d'injection de SQL. Le module mod_rewrite permet de manipuler les URL et d'effectuer des redirections et des re-écritures d'URL afin de bloquer les attaques.
### ModSecurity (Protection contre les attaques par injection de code)
Pour installer le module ModSecurity :
```bash
sudo apt-get install libapache2-mod-security2
sudo apt-get install libapache2-mod-qos
```
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module mod_rewrite
    RewriteEngine On
    
    # Bloquer les tentatives d'injection de code
    RewriteCond %{QUERY_STRING} [a-zA-Z0-9_]=http:// [OR]
    RewriteCond %{QUERY_STRING} [a-zA-Z0-9_]=(\.\.//?)+ [OR]
    RewriteCond %{QUERY_STRING} [a-zA-Z0-9_]=/([a-z0-9_.]//?)+ [NC]
    RewriteRule ^(.*)$ - [F]
    
    # Autres règles de réécriture et de redirection spécifiques pour bloquer les attaques
    
</VirtualHost>
