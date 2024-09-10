# Partnerchain Dependencies Docker

This allows easy orchestration of partnerchain dependency services.

```mermaid
graph TD;

    subgraph Server
        subgraph Docker Host
            ipc[ipc] --> cardano-data[cardano-data]
        end

        subgraph Services
            cardano-node(cardano-node)
            db-sync(db-sync)
            ogmios(ogmios)
            kupo(kupo)
        end

        ipc -.-> cardano-node
        ipc -.-> db-sync
        ipc -.-> ogmios
        ipc -.-> kupo

        cardano-data --> cardano-node
        cardano-data --> db-sync
        cardano-data --> ogmios

        cardano-node -.-> db-sync
        cardano-node -.-> ogmios
        kupo -.-> ogmios
        kupo -.-> cardano-node
    end
```

## Usage

## Starting

1. Clone repo

2. Navigate to .yml file and `docker-compose up`

```shell
cd partnerchain-dependencies
docker-compose up
```

🚀 That's it.