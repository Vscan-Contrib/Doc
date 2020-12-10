# Installation
Deux types d'installations sont possibles : 

* Via les paquets rpm.
* Via les paquets deb.
* Via les sources

## Via les paquets rpms
 
Cette procédure est la même pour toutes les distributions de types redhat likes.
En tout premier lieux il vous faut installer epel :

```bash 
yum install epel
 ```

Installer le serveur de dépôt de vscan :

```bash 
curl -s https://packagecloud.io/install/repositories/Drasrax/vscan/script.rpm.sh | sudo bash
```

Votre version ainsi que votre distribution seront détectées par ce script.

Installer vscan: 

Tapez la commande suivante : 

```bash 
yum install vscan vscan-server
``` 

Installer mariadb : 

```bash 
yum install mariadb-server 
```

Démarrer le service mariadb : 

```bash 
systemctl start mariadb
systemctl enable mariadb
``` 

Configurer mariadb : 

```bash
mysql_secure_installation
```

Importer la base de donnée de vscan: 

```bash
mysql -u root -p << /opt/db/vscan.sql
```

Configurer la base de donnée dans vscan : 

```bash 
vi /etc/vscan_server/server.conf
```


Tester vscan: 

```bash
vscan
```


