# Partner-chain Dependencies Docker

This allows easy orchestration of partner-chain dependency services.

## System requirements

- Install [Docker-Compose](https://docs.docker.com/compose/install/)

## Usage

1. Clone repo

3. Modify paths in `.env` file if desired 

2. Navigate to `.yml` file and `docker-compose up`

```shell
docker-compose up -d
```

🚀 That's it.

## Useful queries 

### Cardano-db-sync

Login into psql shell: 

```
docker exec -it db-sync-postgres psql -U postgres -d cexplorer
```

or 

```
psql -h localhost -U postgres -d cexplorer -p 5432
```

Query Cardano-db-sync sync percentage:

```
select 100 * (extract(epoch from (max(time) at time zone 'UTC')) - extract(epoch from (min(time) at time zone 'UTC'))) / (extract(epoch from (now() at time zone 'UTC')) - extract(epoch from (min(time) at time zone 'UTC'))) as sync_percent from block;
```

### Ogmios

Query Ogmios healthcheck:

```
curl -s localhost:1337/health | jq '.'
```