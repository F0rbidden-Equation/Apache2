## Chapitre 3 : Installation d'Apache2 sur Linux

Dans ce chapitre, nous allons vous guider à travers le processus d'installation d'Apache2 sur un système Linux. Les instructions peuvent varier légèrement en fonction de la distribution Linux que vous utilisez, mais les principes généraux restent les mêmes.

Voici les étapes à suivre pour installer Apache2 :

1. **Mise à jour du système** : Avant d'installer Apache2, il est recommandé de mettre à jour votre système pour vous assurer que vous disposez des dernières mises à jour de sécurité. Vous pouvez utiliser les commandes suivantes pour mettre à jour le système selon votre distribution :

   - **Debian/Ubuntu** :
     ```bash
     sudo apt update
     sudo apt upgrade
     ```

   - **CentOS/Fedora** :
     ```bash
     sudo dnf update
     ```

2. **Installation d'Apache2** : Une fois votre système à jour, vous pouvez installer Apache2 à l'aide de votre gestionnaire de paquets. Utilisez les commandes suivantes selon votre distribution :

   - **Debian/Ubuntu** :
     ```bash
     sudo apt install apache2
     ```

   - **CentOS/Fedora** :
     ```bash
     sudo dnf install httpd
     ```

3. **Démarrage du service Apache2** : Une fois l'installation terminée, vous pouvez démarrer le service Apache2. Utilisez la commande suivante selon votre distribution :

   - **Debian/Ubuntu** :
     ```bash
     sudo systemctl start apache2
     ```

   - **CentOS/Fedora** :
     ```bash
     sudo systemctl start httpd
     ```

4. **Vérification de l'installation** : Vous pouvez maintenant vérifier si Apache2 est correctement installé et fonctionne. Ouvrez un navigateur web et accédez à l'adresse suivante :
5. **http://localhost/**
