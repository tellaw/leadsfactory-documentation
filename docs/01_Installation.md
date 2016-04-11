# Introducccction

Un projet Lead’s factory se présente avec deux éléments :

- Une archive des fichiers du serveur.
- Un Dump de la base SQL

# Pré-requis

Une version récente de Java pour le module segmentation marketing de la lead’s factory : https://www.elastic.co/guide/en/elasticsearch/guide/current/_installing_elasticsearch.html

- PHP 5.5 minimum
- MySQL 4 minimum

# Les fichiers

Les fichiers sont à copier dans le VHost applicatif. Il faut s’assurer que les droits sont positionnés en www-data et 775.


# Le Dump
Le dump doit etre importé dans votre base MySQL

```
mysql –h 127.0.0.1 –u root –p  <mabase> > <mon_fichier_sql>
```

mabase : Nom de la base de données sur votre serveur. Cette base doit etre en UTF8_Unicode_CI.
mon_fichier_sql : Fichier SQL à importer

# ElasticSearch

ElasticSearch se trouve dans le dossier install de la lead’s.

https://github.com/tellaw/leadsfactory/tree/master/Install

Pour Installer ElasticSearch :
- Le dezipper dans le dossier de destination.
- Lui donner les droits souhaités (vous pouvez lui attribuer www-data) via un chown
- Dezipper et copier head et gui dans un dossier plugins à la racine (le créer si il n’existe pas).
- Copier le script de lancement automatique (elasticsearch) en prenant soin d’adapter le chemin avec celui ou vous avez installé ElasticSearch.

```
ES_HOME=/var/www/elasticsearch-1.7.1
```

## Fixez ses droits :

```
sudo chmod 0755 /etc/init.d/elasticsearch
```

## Ajoutez le au lancement automatique

sudo update-rc.d elasticsearch defaults
Executez un lancement manuel /etc/init.d/elasticsearch start

# Kibana

- Le dezipper dans le dossier de destination (l’archive se trouve dans le dossier Install de la leads)..
- Lui donner les droits souhaités (vous pouvez lui attribuer www-data) via un chown
- Copier le script de lancement automatique (kibana) en prenant soin d’adapter le chemin avec celui ou vous avez installé ElasticSearch.

```
DAEMON=/var/www/kibana-4.1.1-linux-x64/bin/$NAME
```

## Fixez ses droits :

```
sudo chmod 0755 /etc/init.d/kibana
```

- Ajoutez le au lancement automatique
- sudo update-rc.d kibana defaults
- Executez un lancement manuel /etc/init.d/kibana start

# La Crontab
Configurer la crontab suivante pour l’utilisateur www-data :

```
>crontab –u www-data -e

*/5 * * * * cd /data/apps/leads-factory/current;php app/console leadsfactory:crontasks:run > /data/apps/leads-factory/shared/app/logs/cron-leadsfactory.log
```

Pensez à adapter les chemins de cette crontab avec le chemin de votre installation.

# Paramétrage de la licence
La licence (fichier PHP), doit être déposée dans un dossier « licence/licence.php » à partir de la racine du projet.