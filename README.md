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

