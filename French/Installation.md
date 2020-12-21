# Installation
Trois types d'installations sont possibles : 

* Via les paquets rpm.
* Via les paquets deb.
* Via les sources

## Via les paquets rpms
 
Cette procédure est la même pour toutes les distributions basées sur l'environnement RedHat.

En tout premier lieux il vous faut installer le repository EPEL :

```bash 
dnf install -y epel-release
dnf install -y 'dnf-command(config-manager)'
dnf config-manager --set-enabled extras -y
dnf config-manager --set-enabled PowerTools
 ```

Installer le serveur de dépôts de vscan :

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
systemctl enable mariadb --now
``` 

Configurer mariadb : 

```bash
mysql_secure_installation
```

Importer la base de données de vscan: 

```bash
mysql -u root -p << /opt/db/vscan.sql
```

Configurer la base de données dans vscan : 

```bash 
vi /etc/vscan_server/server.conf
```


Tester vscan: 

```bash
vscan
```


