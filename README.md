# Installation d'une suite ELK avec Docker

## Pré Requis
La suite est basée sur la dépendance avec Docker Compose. 
Il faut donc que vous installiez docker-compose sur votre serveur. 
Les instructions sont disponibles ici : https://docs.docker.com/compose/install

## Installation 

```
$> git clone https://github.com/faboo03/docker-elk.git /home/kibana
$> cd /home/kibana
```

Ensuite modifier le docker-compose.yml et mapper dans le docker filebeat tous les dossiers que vous voulez monitorer. 
Pour finir, lancer le docker 

```
$> docker-compose up -d
```

## Envoyer le template filebeat 
```
curl -XPUT 'http://localhost:9200/_template/filebeat' -d@src/filebeat.template.json
```

## Vider ElasticSearch
```
curl -XDELETE 'http://localhost:9200/filebeat-*'
```
