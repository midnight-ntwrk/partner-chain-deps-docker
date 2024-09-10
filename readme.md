# Partnerchain Dependencies Docker

This allows easy orchestration of partnerchain dependency services.

```mermaid
graph TD
    A[Docker Compose] -->|Contains| B[Services]
    B --> C[cardano-node]
    B --> D[postgres]
    B --> E[db-sync]
    B --> F[ogmios]
    B --> G[kupo]

    C -->|Uses| H[ipc Volume]
    C -->|Uses| I[cardano-data Volume]
    D -->|Uses| J[postgres-data Volume]
    E -->|Uses| K[db-sync-data Volume]
    E -->|Depends On| D
    F -->|Uses| H
    F -->|Uses| L[ogmios-data Volume]
    F -->|Uses| M[config Volume]
    G -->|Uses| H
    G -->|Uses| N[kupo-dir Volume]
    G -->|Uses| M

    H[ipc] -->|Shared Volume| O[Shared IPC]
    I[cardano-data] -->|Data Volume| P[Cardano Data]
    J[postgres-data] -->|Data Volume| Q[Postgres Data]
    K[db-sync-data] -->|Data Volume| R[DB Sync Data]
    L[ogmios-data] -->|Data Volume| S[Ogmios Data]
    M[config] -->|Config Volume| T[Config Data]
    N[kupo-dir] -->|Data Volume| U[Kupo Data]
```

## Usage

1. Clone repo

2. Navigate to .yml file and `docker-compose up`

```shell
cd partnerchain-dependencies
docker-compose up -d
```

🚀 That's it.