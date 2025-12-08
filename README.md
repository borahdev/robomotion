# Robomotion Production Deployment

Production setup for Robomotion with Docker Compose.

## Setup

1. Copy environment template:
   ```bash
   cp .env.example .env
   ```

2. Edit `.env` with your Robomotion credentials

3. Deploy:
   ```bash
   docker compose up -d
   ```

## Environment Variables

Required variables (enforced by Docker Compose):
- `ROBOMOTION_EMAIL`: Your Robomotion account email
- `ROBOMOTION_WORKSPACE`: Your workspace domain
- `ROBOMOTION_ROBOT_ID`: Your robot ID
- `ROBOMOTION_ROBOT_TOKEN`: Your robot token

## Management

- View logs: `docker compose logs -f`
- Stop: `docker compose down`
- Restart: `docker compose restart`
- Update: `docker compose pull && docker compose up -d`

## Components

- **robomotion**: Main Robomotion container
- **sqlite**: Alpine Linux container for SQLite database
- **redis**: Redis Alpine container for caching and queuing
- Data persists in:
  - Docker volume `robomotion_config` for Robomotion configuration
  - Local directory `./robomotion/` for files and downloads