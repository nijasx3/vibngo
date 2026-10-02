# VibnGo

Point d’entrée du projet VibnGo. Ce dépôt regroupe les différents services de
l’application sous forme de sous-modules Git :

- **Front-end** : `services/front`
- **Back-end** : `services/back`
- **Service IA** : `services/ai`

## Prérequis

- [Git](https://git-scm.com/)
- [Docker](https://docs.docker.com/get-docker/) et Docker Compose, pour
  l’orchestration des services

Les dépendances propres à chaque service sont documentées dans leurs dépôts
respectifs.

## Récupérer le projet

Clonez le dépôt avec ses sous-modules :

```bash
git clone --recurse-submodules https://github.com/nijasx3/vibngo.git
cd vibngo
```

Si le dépôt a déjà été cloné sans les sous-modules :

```bash
git submodule update --init --recursive
```

Pour récupérer les dernières versions des sous-modules référencées par leurs
dépôts distants :

```bash
git submodule update --remote --merge
```

> **Important :** ne faites jamais de commit directement dans ce dépôt
> wrapper. Toute modification doit être commitée dans le dépôt correspondant
> au service concerné (`services/front`, `services/back` ou `services/ai`).

## Configuration

Copiez le fichier d’exemple des variables d’environnement :

```bash
cp .env.example .env
```

Les variables disponibles sont :

| Variable | Description | Valeur par défaut |
| --- | --- | --- |
| `DB_NAME` | Nom de la base de données | `app_db` |
| `DB_USER` | Utilisateur de la base de données | `app_user` |
| `DB_PASSWORD` | Mot de passe de la base de données | `secret` |

Ne versionnez pas le fichier `.env` et remplacez les valeurs par défaut avant
un déploiement.

## Lancer les services

Le fichier `docker-compose.yml` contient actuellement le squelette de
l’orchestration (base de données, service IA, back-end et front-end). Les blocs
de services étant commentés, aucun conteneur n’est lancé automatiquement à ce
stade.

Une fois les services activés dans `docker-compose.yml`, la commande prévue
pour démarrer l’ensemble est :

```bash
docker compose up --build
```

Les ports prévus par la configuration sont :

- Front-end : `http://localhost:3000`
- Back-end : `http://localhost:8000`
- Service IA : `http://localhost:5000`

## Structure du dépôt

```text
.
├── docker-compose.yml
├── .env.example
├── services/
│   ├── ai/       # Sous-module du service IA
│   ├── back/     # Sous-module du back-end
│   └── front/    # Sous-module du front-end
└── README.md
```

## Dépôts des services

- [vibngo-front](https://github.com/nijasx3/vibngo-front)
- [vibngo_back](https://github.com/misterwhite44/vibngo_back)
- [VibnGo-ai-service](https://github.com/benoista/VibnGo-ai-service)
