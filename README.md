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


| Service                         | Rôle principal |
|----------------------------------|----------------|
| `init`                           | Initialise les volumes/config au démarrage |
| `bootloader`                     | Applique les migrations de base de données |
| `db`                             | Base de données PostgreSQL pour Airbyte |
| `worker`                         | Exécute les synchronisations de données |
| `server`                         | API centrale d’Airbyte (backend) |
| `webapp`                         | Interface utilisateur web |
| `airbyte-temporal`              | Orchestrateur de workflows (Temporal) |
| `airbyte-cron`                  | Planifie les tâches régulières |
| `airbyte-connector-builder-server` | Outil pour construire des connecteurs personnalisés |


| Action                                                    | Pourquoi c’est nécessaire                                                         |
| --------------------------------------------------------- | --------------------------------------------------------------------------------- |
| ✅ Créer des dossiers comme `/tmp/airbyte_local/workspace` | Airbyte a besoin de stocker des fichiers (logs, configs, state…) sur le disque.   |
| 🔐 Définir les bons droits (`chmod`, `chown`)             | Certains conteneurs (comme `worker`) peuvent échouer s'ils ne peuvent pas écrire. |
| 🏗️ Vérifier que certains volumes sont montés             | Pour s'assurer que le reste du système fonctionnera sans surprise.                |
| 🧪 Lancer des checks de dépendance (DB, Temporal)         | Pour éviter que le système ne crashe plus tard de manière silencieuse.            |

| Élément                     | Ce que tu apprends 🧠                               | Ce qu’il faut faire ✅                                 |
| --------------------------- | --------------------------------------------------- | ----------------------------------------------------- |
| `env: can't execute 'bash'` | Certains containers n'ont **que `sh`, pas `bash`**  | Remplace `#!/bin/bash` par `#!/bin/sh`                |
| Entrypoint                  | Tu peux exécuter des commandes shell même sans bash | Utilise `/bin/sh -c` dans l’entrypoint Docker Compose |
| Images minimalistes         | Certaines images ne contiennent que l’essentiel     | Adapter tes scripts et outils à l’environnement léger |

à partir de cette discussion: https://github.com/airbytehq/airbyte/discussions/40599
je peux dire que il y a pas un support entre docker et airbyte et maintenant les projets sont plus lancer avec le kubernets donc je vois pas trop l'utilité de continuer ce projet dans le but est d'apprendre
