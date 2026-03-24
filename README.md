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
- `DOKPLOY_NETWORK`

For the domain in Dokploy UI:

- Service: `postiz-app`
- Host: `socials.buldtech.com`
- Path: `/`
- Internal Path: `/`
- Container Port: `5000`
- HTTPS: enabled

## Notes

- This repo expects Dokploy to provide the external project network name through `DOKPLOY_NETWORK`.
- Do not add manual Traefik labels in the compose if Dokploy is managing the domain in the UI.
- If you want to pin Postiz later, replace `ghcr.io/gitroomhq/postiz-app:latest` with a versioned tag.
