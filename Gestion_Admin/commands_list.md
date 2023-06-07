## Liste de Commandes pour Apache2 sur Linux
Demmarrer Apache2
```bash
     sudo service apache2 start
```
Arreter Apache2
```bash
     sudo service apache2 stop
```

Redemarrer Apache2
```bash
     sudo service apache2 start
```

Verifier l'etat du webserver apache2
```bash
     sudo service apache2 status 
```
Activé les modules d'ecriture 
```bash
     sudo a2enmod 
```
Desactivé les modules d'ecriture

```bash
     sudo a2dismod
```
Verfié la configuration virtualhost apache2 
```bash
     sudo apache2ctl configtest
```
## Gestion et Informations Log fichiers Apache2 sur Linux
Consulté les dernieres lignes du fichier "error.log"
```bash
     sudo tail -f /var/log/apache2/error.log
```
Consulté les dernieres lignes du fichier "Access.log"
```bash
sudo tail -f /var/log/apache2/error.log
```
## Administration des connexions clients sur  Apache2 sur Linux (IPtables)
Bannir l'access d'un client a partir de l'adresse ip  
```bash
sudo iptables -A INPUT -a ip_adress -j DROP
```
Debannir l'access d'un client a partir de l'adresse ip
```bash
sudo iptables -D INPUT -a ip_adress -j DROP
```
Consulter la listes des ip adress bannies 
```bash
sudo iptables -L INPUT -v -n
```

