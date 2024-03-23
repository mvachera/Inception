# Utilisation de l'image de base Debian Buster
FROM debian:buster

# Mise à jour des dépôts de paquets et installation de MariaDB Server et MariaDB Client
RUN apt-get update \
    && apt-get install -y mariadb-server \
    mariadb-client

# Copie du fichier de configuration personnalisé 50-server.cnf dans le répertoire de configuration de MariaDB
COPY ./conf/50-server.cnf /etc/mysql/mariadb.conf.d/

# Copie du script d'initialisation init-mariadb.sh à la racine du système de fichiers et attribution des permissions d'exécution
COPY ./conf/init-mariadb.sh /
RUN chmod +x init-mariadb.sh

# Exposition du port 3306 utilisé par MariaDB pour les connexions
EXPOSE 3306

# Commande par défaut pour exécuter le script d'initialisation lors du lancement du conteneur
CMD ["/init-mariadb.sh"]