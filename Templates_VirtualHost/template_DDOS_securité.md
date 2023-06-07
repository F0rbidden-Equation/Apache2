## Modèle 5 : Protection contre les attaques DDoS avec le module mod_qos

Ce modèle utilise le module mod_qos pour protéger votre serveur Apache2 contre les attaques DDoS (Distributed Denial of Service). Le module mod_qos permet de limiter la bande passante, le nombre de connexions et d'autres paramètres afin de réduire l'impact des attaques DDoS.
### ModEvasive (Protection contre les attaques par force brute et DDoS) Apache2
Pour installer le module ModEvasive :
```bash
sudo apt-get install libapache2-mod-evasive
sudo apt-get install libapache2-mod-qos
```
```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
    
    # Activer le module mod_qos
    <IfModule mod_qos.c>
        # Configuration des règles de protection contre les attaques DDoS
        QS_SrvMaxConnPerIP 100
        QS_SrvMaxRequestRate 100
        QS_SrvMaxBandwidth 1000000
    </IfModule>
    
    # Autres directives de configuration spécifiques à mod_qos
    
</VirtualHost>
