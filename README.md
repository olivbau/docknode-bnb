# Docknode BNB

## Metrics

- `https://yourdomain.com:9101/metrics`

## Install

0. VPS config (optional)

```bash
apt update
apt upgrade -y
apt install -y git screen
# apt update && apt upgrade -y && apt install -y git screen
# install docker https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
```

1. Clone the repository

```bash
git clone https://github.com/olivbau/docknode-bnb.git && cd docknode-bnb
```

2. Configure environement variables

```bash
cp .env.example .env

# Generate users passwords for basic auth
docker run --rm caddy:2-alpine caddy hash-password --plaintext 'password'

# Set users and passwords for basic auth
# Set the host
nano .env
```

3. Setup UFW

```bash
ufw allow ssh && ufw deny 8545
ufw enable
```

4. Download snapshot (optional)

```bash
screen -R snapshot
```

5. Run

```bash
docker compose pull
docker compose up -d
docker logs -f docknode-bnb-fullnode-1 --since 5m
docker compose down
```
