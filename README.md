# docker-nas

Docker compose file which runs all of my apps which running at my NAS for daily usage

## Prepare

- Install `docker`, `docker-compose` on your server

## Services included

| Service                                                                         | Pro | Full | Power | Light |
| ------------------------------------------------------------------------------- | --- | ---- | ----- | ----- |
| [nginx-proxy-manager](https://github.com/NginxProxyManager/nginx-proxy-manager) | +   | +    | +     | +     |
| [qBittorrent](https://www.qbittorrent.org)                                      | +   | +    | +     | +     |
| [Plex](https://www.plex.tv)                                                     | +   | +    | +     | +     |
| [Sonarr](https://sonarr.tv)                                                     | +   | +    | +     | +     |
| [Radarr](https://radarr.video)                                                  | +   | +    | +     | +     |
| [Overseerr](https://overseerr.dev)                                              | +   | +    | +     | +     |
| [Jackett](https://github.com/Jackett/Jackett)                                   | +   | +    | +     | +     |
| [TAUTULLI](https://tautulli.com)                                                | +   | +    | +     | +     |
| [Portainer CE](https://portainer.io)                                            | +   | +    | +     | -     |
| [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)                      | +   | +    | +     | -     |
| [OpenSpeedTest](https://openspeedtest.com)                                      | +   | +    | +     | -     |
| [Homebridge](https://homebridge.io)                                             | +   | +    | +     | -     |
| [Tailscale](https://tailscale.com)                                              | +   | +    | +     | -     |
| [Zenko CloudServer](https://github.com/scality/cloudserver)                     | +   | +    |       | -     |
| [RSSHub](https://github.com/DIYgod/RSSHub)                                      | +   | +    | -     | -     |
| [huginn](https://github.com/huginn/huginn)                                      | +   | +    | -     | -     |
| [Searxng](https://github.com/searxng/searxng)                                   | +   | +    | -     |       |
| [OpenWebUI](https://github.com/open-webui/open-webui)                           | +   | +    | -     | -     |
| [OpenHands](https://github.com/All-Hands-AI/OpenHands)                          | +   | -    | -     | -     |
| [Perplexica](https://github.com/ItzCrazyKns/Perplexica)                         | +   | -    | -     | -     |
| [Bolt](https://github.com/stackblitz-labs/bolt.diy)                             | +   | -    | -     | -     |
| [Webcrumbs](https://github.com/webcrumbs-community/webcrumbs)                   | +   | -    | -     | -     |

### Estimated resources

> 1 vCPU isn't 1 physical core, it's like 1 core of hyper-threaded (2) core

| Service                                                                         | vCPU | RAM   | Disk             |
| ------------------------------------------------------------------------------- | ---- | ----- | ---------------- |
| [nginx-proxy-manager](https://github.com/NginxProxyManager/nginx-proxy-manager) | 0.5  | 0.5G  | 1G               |
| [Portainer CE](https://portainer.io)                                            | 1    | 1G    | 1G-              |
| [qBittorrent](https://www.qbittorrent.org)                                      | 2    | 1G    | 1G               |
| [Plex](https://www.plex.tv)                                                     | 2    | 2G    | 2G + Storage     |
| [Sonarr](https://sonarr.tv)                                                     | 0.5  | 0.5G  | 1G               |
| [Radarr](https://radarr.video)                                                  | 0.5  | 0.5G  | 1G               |
| [Overseerr](https://overseerr.dev)                                              | 0.5  | 0.5G  | 1G               |
| [Jackett](https://github.com/Jackett/Jackett)                                   | 0.5  | 0.5G  | 1G               |
| [TAUTULLI](https://tautulli.com)                                                | 0.5  | 0.5G  | 1G               |
| [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome)                      | 1    | 1G    | 1G-              |
| [OpenSpeedTest](https://openspeedtest.com)                                      | 0.5  | 0.5G  | 1G               |
| [Homebridge](https://homebridge.io)                                             | 1    | 1G    | 1G               |
| [Tailscale](https://tailscale.com)                                              | 0.5  | 0.5G  | 0.5G             |
| [Zenko CloudServer](https://github.com/scality/cloudserver)                     | 0.5  | 0.5G  | 1G + Storage-    |
| [OpenWebUI](https://github.com/open-webui/open-webui)                           | 1    | 1G-   | 1G               |
| [Searxng](https://github.com/searxng/searxng)                                   | 2    | 2G-   | 2G               |
| [RSSHub](https://github.com/DIYgod/RSSHub)                                      | 0.5  | 1G    | 1G               |
| [huginn](https://github.com/huginn/huginn)                                      | 0.5  | 1G    | 1G               |
| [OpenHands](https://github.com/All-Hands-AI/OpenHands)                          | 2    | 2G    | 1G               |
| [Perplexica](https://github.com/ItzCrazyKns/Perplexica)                         | 1    | 1G    | 1G               |
| [Bolt](https://github.com/stackblitz-labs/bolt.diy)                             | 2    | 2G    | 1G               |
| [Webcrumbs](https://github.com/webcrumbs-community/webcrumbs)                   | 1    | 1G    | 1G               |
|                                                                                 |      |       |                  |
| Total                                                                           | 22.5 | 22 GB | ~24 GB + Storage |

## Installation & Running

- Install docker and docker-compose
- Prepare `.env` by example of `.env.example`
- Run `docker-compose up -d`

## Setup

> Most of setup configurations for Raspberry Pi

### Mount SMB Share

#### Via `sudo` for once

- <https://askubuntu.com/a/662803> (SMB Credentials)
- <https://help.ubuntu.com/community/MountWindowsSharesPermanently> (SMB Credentials)
- <https://gist.github.com/giordanocardillo/05a89065ff0843c6da116993e8f16913> (SMB Credentials)
- <https://ubuntu.com/server/docs/how-to-mount-cifs-shares-permanently> (SMB + Mount)
- <https://raspberrypi.stackexchange.com/a/33052>
- <https://askubuntu.com/a/1227429> (CIFS temporarily mount)

```sh
sudo mount.cifs //192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared -o rw,user=username,password=xyzf,nounix,sec=ntlmssp,file_mode=0777,dir_mode=0777
# or
sudo mount.cifs //192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared -o user=username,password=xyzf,uid=1000,gid=1000,vers=3.0,nounix
```

and you can test via command `sudo mount -a`

#### Permanent mounting

- <https://askubuntu.com/a/662803> (SMB Credentials)
- <https://help.ubuntu.com/community/MountWindowsSharesPermanently> (SMB Credentials)
- <https://gist.github.com/giordanocardillo/05a89065ff0843c6da116993e8f16913> (SMB Credentials)
- <https://ubuntu.com/server/docs/how-to-mount-cifs-shares-permanently> (SMB + Mount)
- <https://askubuntu.com/a/1341879> (SMB/CIFS + Mount permanent mount)
- <https://askubuntu.com/a/1372876> (Explanation)

Append following line into at end of `/etc/stab`

`//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,noauto,x-systemd.automount`

You can edit `/etc/fstab` file by `sudo nano /etc/fstab`, then **reboot** your device.

After reboot, check your path or run manually check via `sudo mount -a`

#### Docker mount wait

##### Guides / Tutorials

- <https://www.reddit.com/r/docker/comments/ke3twe/comment/jxwtzyu>
- <https://stackoverflow.com/questions/31746182/docker-compose-wait-for-container-x-before-starting-y>
  | [Docker Service Edit](https://unix.stackexchange.com/a/571353/657638)

##### Documentation links

- <https://docs.docker.com/reference/compose-file/services/#healthcheck>
- <https://docs.docker.com/compose/how-tos/startup-order>

##### Possible fixes

- <https://askubuntu.com/a/1295943> (`fstab` trick)
  | [Docker Service Edit](https://unix.stackexchange.com/a/571353/657638)

##### Solution 1

Follow [here](https://github.com/openmediavault/openmediavault/issues/458#issuecomment-533892859)

TLDR:

```diff
[Unit]
-After=network-online.target docker.socket firewalld.service containerd.service time-set.target
+After=network-online.target docker.socket firewalld.service containerd.service time-set.target local-fs.target
```

Try `sudo nano /etc/systemd/system/multi-user.target.wants/docker.service` (this path for Debian Raspberry) if above solution did not work

##### Solution 2

Follow [here](https://www.reddit.com/r/selfhosted/comments/pmt7af/comment/hckfzuh)

TLDR:

```diff
[Unit]
-Requires=docker.socket
+Requires=docker.socket <your mount name>.mount
```

##### Solution 3

Follow [here](https://askubuntu.com/a/1374584)

TLDR:

```diff
-//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,noauto
+//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,noauto,x-systemd.automount
```

##### Solution 4

Follow [here](https://askubuntu.com/a/1372876)

TLDR:

```diff
-//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,noauto,x-systemd.automount
+//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix,noauto,x-systemd.automount,x-systemd.idle-timeout=60,x-systemd.mount-timeout=30
```

## Links

| [AV1 Plex tvOS](https://github.com/currifi/plex_av1_tvos)
