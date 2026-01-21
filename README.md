# Formbricks

A self-hosted formbricks application.

## Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/formbricks/main/docker-compose.yaml" | docker compose -f - up -d
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/formbricks" ~/.local/srv/docker/formbricks
cd ~/.local/srv/docker/formbricks
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install formbricks
```

## Configuration

See docker-compose.yaml for environment variables and configuration options.

## Documentation

Check the official project documentation for detailed setup and usage information.
