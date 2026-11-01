## 👋 Welcome to formbricks 🚀

The open-source feedback and survey platform for product teams

## 📋 Description

The open-source feedback and survey platform for product teams

## 🚀 Services

- **app**: formbricks/formbricks:latest

### Infrastructure Components

- **formbricks-db**: Postgres database
- **formbricks-redis**: Redis cache

## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/formbricks/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/formbricks" ~/.local/srv/docker/formbricks
cd ~/.local/srv/docker/formbricks
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr
```bash
composemgr install formbricks
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
BASE_HOST_NAME=formbricks.example.com
APP_SECRET_KEY=replace-with-a-random-password
APP_SECRET_TOKEN_64=replace-with-a-random-password
SECURE_SECRET=replace-with-a-random-password
DB_USER_PASS=replace-with-a-random-password
```

See `docker-compose.yaml` for complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64177` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

## 🌐 Access

- **Web Interface**: http://172.17.0.1:64177

## 📂 Volumes

- `./volumes/data/formbricks` - Uploaded survey assets
- `./volumes/db/postgres/formbricks` - Database data
- `./volumes/cache/redis/formbricks` - Redis cache data

## 🔐 Security

- Set `APP_SECRET_KEY`, `APP_SECRET_TOKEN_64` and `SECURE_SECRET` to strong
  random values before the first start
- `ENCRYPTION_KEY` must be a 64-character hex string; generate one with
  `openssl rand -hex 32`
- Formbricks sends survey invitations; configure a real SMTP relay
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose --env-file .env logs -f app
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
