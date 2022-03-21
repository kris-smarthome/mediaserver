# Media
Docker compose file for a torrent based download server. Includes Tautulli for PLex monitoring if required. Tiny proxy is enabled by default on port 8888 if routing traffic across the VPN from any other container or host if needed, when using the proxy for containers in this stack, the container name can be used. Remember to create the inside_network and set environment variables before bringing up the stack.

This stack expects a base directory structure at the root of your media folder/drive which is set in the .env folder i.e MEDIADIR=/mnt/media. Create the following structure before bringing the stack up.

- $MEDIADIR/app_data
- $MEDIADIR/app_data/downloads
- $MEDIADIR/app_data/downloads/complete
- $MEDIADIR/app_data/downloads/incomplete
- $MEDIADIR/movies
- $MEDIADIR/tv

Create networks:
```
sudo docker network create inside_network
```

Set the following variables in the .env file, examples are given in square brackets:
- PUID [the PUID of your user account] 
- PGID [the PGID of your user account] 
- TZ ["Europe/London"]
- DOCKERDIR ["/home/user/docker"]

-  LOCAL_NETWORK [Networks allowed to access the web UI in CIDR format: i.e. 192.168.1.0/24]
- TRANSMISSION_USERNAME [anythingyoulike]
- TRANSMISSION_PASSWORD [anythingyoulike]
- MEDIADIR [The root path of your media source, see above note]

VPN configuration is documented here: https://haugene.github.io/docker-transmission-openvpn/
- VPN_PROVIDER
- VPN_CONFIG
- VPN_USERNAME
- VPN_PASSWORD

View the PUID and PGID for the current user using the ```id``` command.

Bring up the stack:
```
sudo docker-compose -p media up -d
```

Applications included with this stack:
- [9000]  Transmission web UI
- [8888]  Tinyproxy
- [9001]  Jackett
- [9002]  Radarr
- [9003]  Sonarr
- [9004]  Tautulli

Additional applications:
- [10000] Portainer agent

## Post installation
No post installation tasks will be covered in this repository.
