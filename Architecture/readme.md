## Chapitre 2 : Architecture des fichiers et configurations par défaut

Dans ce chapitre, nous allons explorer l'architecture des fichiers d'Apache2 et nous familiariser avec les fichiers de configuration par défaut du serveur.

Lorsque vous installez Apache2, les fichiers de configuration se trouvent généralement dans le répertoire `/etc/apache2`. Voici quelques fichiers et répertoires clés que vous devez connaître :

- **`/etc/apache2/apache2.conf`** : Ce fichier contient la configuration globale d'Apache2. Vous pouvez y définir des directives qui s'appliquent à l'ensemble du serveur.

- **`/etc/apache2/sites-available/`** : Ce répertoire contient les fichiers de configuration des différents hôtes virtuels (sites web) hébergés par Apache2. Chaque fichier correspond à un hôte virtuel et contient des directives spécifiques à ce site.

- **`/etc/apache2/sites-enabled/`** : Ce répertoire contient des liens symboliques vers les fichiers de configuration des hôtes virtuels activés. Ces fichiers sont généralement créés en activant un hôte virtuel à l'aide de la commande `a2ensite`.

- **`/etc/apache2/mods-available/`** : Ce répertoire contient les fichiers de configuration des modules disponibles dans Apache2. Chaque module peut être activé ou désactivé à l'aide de liens symboliques dans le répertoire `mods-enabled`.

- **`/etc/apache2/mods-enabled/`** : Ce répertoire contient des liens symboliques vers les fichiers de configuration des modules activés. Les modules activés sont généralement gérés à l'aide des commandes `a2enmod` et `a2dismod`.

- **`/etc/apache2/conf-available/`** : Ce répertoire contient les fichiers de configuration supplémentaires qui peuvent être inclus dans la configuration globale d'Apache2. Ces fichiers peuvent être activés à l'aide de liens symboliques dans le répertoire `conf-enabled`.

- **`/etc/apache2/conf-enabled/`** : Ce répertoire contient des liens symboliques vers les fichiers de configuration activés. Ces fichiers sont généralement créés en activant des fichiers de configuration à l'aide de la commande `a2enconf`.

Maintenant que vous avez une idée de l'architecture des fichiers dans Apache2, voyons quelques fichiers de configuration par défaut importants :

- **`default-ssl.conf`** : Ce fichier se trouve dans le répertoire `/etc/apache2/sites-available/` et contient la configuration par défaut pour les sites web sécurisés (HTTPS). Il définit les directives de base pour la configuration SSL et peut être utilisé comme point de départ pour la configuration des sites sécurisés.
