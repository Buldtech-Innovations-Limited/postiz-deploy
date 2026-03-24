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
- `LINKEDIN_CLIENT_ID`
- `LINKEDIN_CLIENT_SECRET`
- `TIKTOK_CLIENT_ID`
- `TIKTOK_CLIENT_SECRET`
- `YOUTUBE_CLIENT_ID`
- `YOUTUBE_CLIENT_SECRET`

## Notes

- This repo expects Dokploy's standard external `dokploy-network` to exist.
- Routing is managed directly in `docker-compose.yml` through Traefik labels.
- Leave the Dokploy `Domains` tab empty for this stack to avoid duplicate label generation.
- `postiz-app` is pinned to `ghcr.io/gitroomhq/postiz-app:v2.21.0` for predictable redeploys.
- Upgrade Postiz intentionally by changing that tag to a reviewed upstream release.
- `postiz-app` uses an explicit Swarm rolling update policy and healthcheck so redeploys are start-first and can roll back more safely.
- Rotate `JWT_SECRET` and `YOUTUBE_CLIENT_SECRET` in Dokploy after the earlier credential exposure.
