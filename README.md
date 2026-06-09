# demo-app

Go HTTP server pour la démo AI-Ops. Affiche une page de status qui reflète l'état de la connexion PostgreSQL.

## Status page

| État | Affichage |
|------|-----------|
| DB connectée | Page verte **HEALTHY** |
| DB injoignable | Page rouge **DEGRADED** (pulsante) + détail d'erreur |

Auto-refresh toutes les 3 secondes. Endpoint `/health` retourne 200/503.

## Image Docker

```
docker pull aurelops/ia-ops-demo-app:latest
```

Poussée automatiquement sur Docker Hub à chaque push sur `main` via GitHub Actions.

## Secrets GitHub requis

| Secret | Valeur |
|--------|--------|
| `DOCKERHUB_USERNAME` | Ton username Docker Hub |
| `DOCKERHUB_TOKEN` | Token d'accès Docker Hub (Read/Write) |

## Variables d'environnement

| Variable | Exemple | Description |
|----------|---------|-------------|
| `DATABASE_URL` | `postgres://app:s3cr3t@postgres:5432/appdb` | URL de connexion PostgreSQL |
| `PORT` | `8080` | Port HTTP (défaut: 8080) |
| `POD_NAME` | injecté par K8s | Affiché dans la page status |
| `POD_NAMESPACE` | injecté par K8s | Affiché dans la page status |

## Repo GitOps associé

Les manifests Kubernetes sont dans : https://github.com/aurelien-moreau/ia-ops-argo-app
