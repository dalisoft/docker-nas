# docker-nas

Docker compose file which runs all of my apps which running at my NAS for daily usage

## Prepare

- Install `docker`, `docker-compose` on your server

## Services included

- [Portainer CE](https://portainer.io)
- [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)
- [OpenSpeedTest](https://openspeedtest.com)
- [Homebridge](https://homebridge.io)
- [qBittorrent](https://www.qbittorrent.org)
- [Plex](https://www.plex.tv)
- [Sonarr](https://sonarr.tv)
- [Radarr](https://radarr.video)
- [Tailscale](https://tailscale.com)
- [S3 Server](https://s3-server.readthedocs.io)

## Installation & Running

- Install docker and docker-compose
- Prepare `.env` by example of `.env.example`
- Run `docker-compose up -d`

## Links

- [AV1 Plex tvOS](https://github.com/currifi/plex_av1_tvos)
