# Commandes utiles à l'installation de aapanel 

Mettre à jour le système.

```bash
sudo apt-get update && apt-get upgrade
```
Allez sur [aapanel](https://www.aapanel.com/new/download.html) et copier/coller, dans votre terminal, la commande d'installation correspondant à votre distribution Linux. Une fois ceci fait, l'installation de aapanel commence, cela peut prendre plusieurs minutes. Ne fermer surtout pas votre terminal pendant l'installation.

Dès que l'installation se termine aapanel vous affiche les liens ainsi que les identifiants de connexion sous ce format.

```bash
==================================================================
Congratulations! Installed successfully!
==================================================================
aaPanel Internet Address: http://130.150.243.175:7800/ec532e38
aaPanel Internal Address: http://192.168.0.0:7800/ec532e38
username: 9djsmvdu
password: 029483f3
Warning:
If you cannot access the panel,
release the following port (7800|888|80|443|20|21) in the security group
==================================================================
Time consumed: 6 Minute!
```

Cependant comme indiqué le pare-feu bloque l'accès au panel nous allons donc installez firewalld.

```bash
sudo apt install firewalld
```

Ensuite ajoutez les règles de pare-feu suivantes.

```bash
sudo firewall-cmd --permanent --zone=public --add-port=7800/tcp
sudo firewall-cmd --permanent --zone=public --add-port=888/tcp
sudo firewall-cmd --permanent --zone=public --add-port=80/tcp
sudo firewall-cmd --permanent --zone=public --add-port=443/tcp
sudo firewall-cmd --permanent --zone=public --add-port=20/tcp
sudo firewall-cmd --permanent --zone=public --add-port=21/tcp
```

Maintenant appliquez les modifications en rechargeant le pare-feu.

```bash
sudo firewall-cmd --reload
```
firewalld pouvant interférer avec le pare-feu de aapanel, il est préférable de le désinstaller par la suite.

```bash
sudo apt purge --auto-remove firewalld
```

### Voilà ! Vous pouvez maintenant accéder à votre interface aapanel 👍

Commande root linux.

```bash
sudo -i
```
Commande de gestion aapanel (A faire en root)
```bash
bt
```

# Commandes utiles à la configuration de django sur aapanel

```bash
/www/wwwroot/VOTRE-NOM-DE-PROJET/VOTRE-ENVIRONNEMENT-VIRTUEL/bin/python3 manage.py
```

Accédez au dossier du projet.

```bash
cd /www/wwwroot/DjangoBlog
```
Faire les migrations.

```bash
/www/wwwroot/DjangoBlog/d69daf27a976191694137ec21fa87ff9_venv/bin/python3 manage.py migrate
```

```bash
/www/wwwroot/DjangoBlog/d69daf27a976191694137ec21fa87ff9_venv/bin/python3 manage.py makemigrations
```
Créer un compte superuser pour django admin.

```bash
/www/wwwroot/DjangoBlog/d69daf27a976191694137ec21fa87ff9_venv/bin/python3 manage.py createsuperuser
```
Collecter les fichiers statiques (CSS, JS, PDF et images).

```bash
/www/wwwroot/DjangoBlog/d69daf27a976191694137ec21fa87ff9_venv/bin/python3 manage.py collectstatic
```
