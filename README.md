
# Minidlna in docker container


Fork from crocandr. Thanks!


## Build

```
docker build -t damufo/minidlna:latest .
```

## Setting general configuration
```
git clone https://github.com/damufo/docker-minidlna.git
cd docker-minidlna
cp sample.env .env
nano .env
```

## Description for .env file variables

```
MINIDLNA_SRVNAME: name of de minidlna server

MINIDLNA_FOLDER_AUDIO: folder to set minidlna config file
MINIDLNA_FOLDER_VIDEO: folder to set minidlna config file
MINIDLNA_FOLDER_IMAGE: folder to set minidlna config file

MINIDLNA_VOLUME_AUDIO: folder host to mount as volume
MINIDLNA_VOLUME_VIDEO: folder host to mount as volume
MINIDLNA_VOLUME_IMAGE: folder host to mount as volume

# MINIDLNA_IFACE: when exist more one interface, uncoment this line and set iface name, example: eth0.
```
IMPORTANT! when exist more one interface, uncomment line that start as '#- SSDP_IFACE...' in docker-compose.yml

## Start container

```
docker compose start -d
docker compose logs -f
```

## Known errors

Container always restarts and `SSDP service start problem` message in the container logs.
Check the 1900 UDP port on your docker host (example: `ss -lntpu | grep -i 1900` ) maybe already in use.
Stop another UPNP service, like Jellyfin/Plex/Emby server to free up this port and try again.

