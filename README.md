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
- [Overseerr](https://overseerr.dev)
- [Jackett](https://github.com/Jackett/Jackett)
- [TAUTULLI](https://tautulli.com)
- [Tailscale](https://tailscale.com)
- [Zenko CloudServer](https://github.com/scality/cloudserver)

## Installation & Running

- Install docker and docker-compose
- Prepare `.env` by example of `.env.example`
- Run `docker-compose up -d`

## Setup

> Most of setup configurations for Raspberry Pi

### Mount SMB Share

#### Via `sudo` for once

- <https://raspberrypi.stackexchange.com/a/33052>
- <https://askubuntu.com/a/1227429>

```sh
sudo mount.cifs //192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared -o rw,user=dalisoft,password=0000,nounix,sec=ntlmssp,file_mode=0777,dir_mode=0777
# or
sudo mount.cifs //192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared -o user=dalisoft,password=0000,uid=1000,gid=1000,vers=3.0,nounix
```

and you can test via command `sudo mount -a`

#### Permanent mounting

- <https://askubuntu.com/a/1341879>

Append following line into at end of `/etc/stab`

`//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix 0 0`

You can edit `/etc/fstab` file by `sudo nano /etc/fstab`, then **reboot** your device.

After reboot, please check with `sudo mount -a`

## Links

- [AV1 Plex tvOS](https://github.com/currifi/plex_av1_tvos)
