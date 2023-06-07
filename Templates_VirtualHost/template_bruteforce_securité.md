## Modèle 4 : Protection contre les attaques par force brute avec le module mod_evasive

Ce modèle utilise le module mod_evasive pour protéger votre serveur Apache2 contre les attaques par force brute, telles que les tentatives répétées de connexion échouées. Le module mod_evasive détecte ces attaques et bloque temporairement les adresses IP offensantes.
### ModEvasive
Pour installer le module mod_evasive pour Apache2 :
```bash
     sudo apt-get install libapache2-mod-evasive
```
Une fois l'installation terminée, ouvrez le fichier de configuration du module mod_evasive en utilisant votre éditeur de texte préféré. Par exemple :
```bash
     sudo nano /etc/apache2/mods-enabled/evasive.conf
```
Configurez les paramètres de mod_evasive selon vos besoins. Par exemple, vous pouvez spécifier le nombre maximal de requêtes par seconde, le délai d'attente entre les requêtes, etc.
Enregistrez les modifications et fermez le fichier de configuration.
Redémarrez Apache2 pour prendre en compte les modifications 
```bash
     sudo service apache2 restart
```
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module mod_evasive
    <IfModule mod_evasive24.c>
        DOSHashTableSize 3097
        DOSPageCount 2
        DOSSiteCount 50
        DOSPageInterval 1
        DOSSiteInterval 1
        DOSBlockingPeriod 10
        DOSEmailNotify you@example.com
        DOSSystemCommand "sudo /sbin/iptables -I INPUT -s %s -j DROP"
        DOSLogDir "/var/log/mod_evasive"
    </IfModule>
    
    # Autres directives de configuration spécifiques à mod_evasive
    
</VirtualHost>
