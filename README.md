# docker-nas

Docker compose file which runs all of my apps which running at my NAS for daily usage

## Services included

- OpenSpeedTest
- qBittorrent
- Plex
- Homebridge (for bridge for local non Homekit devices)
- Tailscale

## Installation & Running

- Install docker and docker-compose
- Prepare `.env` by example of `.env.example`
- Run `docker-compose up -d`
