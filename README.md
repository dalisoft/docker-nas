# docker-nas

Docker compose file which runs all of my apps which running at my NAS for daily usage

## Services included

- [OpenSpeedTest](https://openspeedtest.com)
- [qBittorrent](https://www.qbittorrent.org)
- [Plex](https://www.plex.tv)
- [Homebridge](https://homebridge.io)
- [S3 Server](https://s3-server.readthedocs.io)
- [tailscale](https://tailscale.com)

## Installation & Running

- Install docker and docker-compose
- Prepare `.env` by example of `.env.example`
- Run `docker-compose up -d`
