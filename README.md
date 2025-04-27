# Modern Data Stack Project

Projet pédagogique de data engineering : ingestion de données avec Airbyte, transformation avec DBT, orchestration avec Airflow, visualisation avec Streamlit, stockage PostgreSQL.

But : apprendre les concepts clés du data engineering à travers un projet cohérent.

Étapes :
- Ingestion de données via Airbyte
- Stockage dans Postgres
- Transformation avec DBT
- Orchestration avec Airflow
- Visualisation avec Streamlit

# 📌 Airbyte - Présentation
Airbyte est une plateforme d'ingestion de données open-source qui s'inscrit dans le Modern Data Stack. Elle a été créée en 2020 pour répondre aux limites des solutions d'extraction propriétaires comme Fivetran, en offrant une alternative gratuite, flexible et modulaire. Son objectif est de simplifier l'extraction et le chargement (EL) des données depuis plus de 300 sources (APIs, bases de données, fichiers, etc.) vers de nombreuses destinations (Postgres, BigQuery, S3...). Airbyte est aujourd'hui utilisé par des milliers d’entreprises à travers le monde. Dans une architecture data, il intervient au début de la chaîne pour collecter les données brutes et les charger dans un data warehouse ou un data lake. Grâce à ses connecteurs standardisés, sa gestion des logs, et ses fonctionnalités comme le CDC (Change Data Capture), Airbyte permet d'apprendre les principes clés de l’ingestion de données, du monitoring et de la modularité dans une stack moderne.

Concept | Ce que tu viens d'apprendre
Microservices | Déployer plusieurs petits services indépendants
Variables d'environnement | Rendre une application configurable dynamiquement
Volumes Docker | Séparer la donnée du cycle de vie du container
Ports exposés | Permettre à l'extérieur d'accéder à des services internes
Dépendances entre services | Démarrer dans le bon ordre pour éviter des erreurs de connexion


Élément | Explication
Airbyte utilise Temporal | Airbyte se base sur un moteur de workflow distribué appelé Temporal.
airbyte-temporal est un service | Quand tu déploies Airbyte, il faut aussi démarrer un conteneur qui s’appelle airbyte-temporal.
DNS Docker interne | Quand tu fais docker-compose up, les conteneurs communiquent par nom (par ex airbyte-db, airbyte-server, airbyte-temporal).
Si le service manque... | Si airbyte-temporal n’existe pas ou n’est pas lancé, Airbyte-server ne trouve pas son "partenaire" et plante.


https://github.com/nialloriordan/airbyte-airflow-scraper/blob/master/docker-compose.airbyte.yaml

https://github.com/Ashwini9030/airbytedocs/blob/master/docker-compose.yaml


