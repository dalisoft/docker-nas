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
- <https://askubuntu.com/a/1295943> (`fstab` trick)

Append following line into at end of `/etc/stab`

`//192.168.100.32/Media /home/pi/Desktop/docker-nas/data/shared cifs credentials=/home/pi/.smbcredentials,uid=1000,gid=1000,vers=3.0,nounix 0 0`

You can edit `/etc/fstab` file by `sudo nano /etc/fstab`, then **reboot** your device.

After reboot, please check with `sudo mount -a`

#### Docker mount wait

- <https://www.reddit.com/r/docker/comments/ke3twe/comment/jxwtzyu>
- <https://stackoverflow.com/questions/31746182/docker-compose-wait-for-container-x-before-starting-y>
- <https://docs.docker.com/reference/compose-file/services/#healthcheck>
- <https://docs.docker.com/compose/how-tos/startup-order>
- <https://github.com/openmediavault/openmediavault/issues/458#issuecomment-533892859>
- <https://askubuntu.com/a/1295943> (`fstab` trick)

##### Solution 1

If that does not work, try doing this step.

Try `sudo nano /etc/systemd/system/multi-user.target.wants/docker.service` (this path for Debian Raspberry) and then

```diff
-After=network-online.target docker.socket firewalld.service containerd.service time-set.target
+After=network-online.target docker.socket firewalld.service containerd.service time-set.target local-fs.target
```

and this one too

```diff
+ExecStartPre=/bin/sudo mount -a
ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
```

##### Solution 2

Follow [here](https://www.reddit.com/r/selfhosted/comments/pmt7af/comment/hckfzuh)

##### Solution 3

Follow [here](https://askubuntu.com/a/1374584)

## Links

- [AV1 Plex tvOS](https://github.com/currifi/plex_av1_tvos)
- [Docker Service Edit](https://unix.stackexchange.com/a/571353/657638)
- [Mount fix #1](https://github.com/openmediavault/openmediavault/issues/458#issuecomment-533892859)
