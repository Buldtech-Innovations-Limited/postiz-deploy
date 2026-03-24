# Postiz Deploy

Dokploy-ready Postiz deployment using the upstream prebuilt image and the required Temporal dynamic config.

## Files

- `docker-compose.yml`
- `dynamicconfig/development-sql.yaml`
- `.env.example`

## Dokploy Setup

Create a Compose app from this repo and set these environment variables:

- `POSTIZ_HOST`
- `JWT_SECRET`
- `DB_USER`
- `DB_PASSWORD`
- `DB_NAME`
- `YOUTUBE_CLIENT_ID`
- `YOUTUBE_CLIENT_SECRET`

## Notes

- This repo expects Dokploy's standard external `dokploy-network` to exist.
- Routing is managed directly in `docker-compose.yml` through Traefik labels.
- Leave the Dokploy `Domains` tab empty for this stack to avoid duplicate label generation.
- If you want to pin Postiz later, replace `ghcr.io/gitroomhq/postiz-app:latest` with a versioned tag.
