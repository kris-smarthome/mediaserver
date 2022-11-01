# Media
### Updated 2022
Media stack, deploy as a Portainer stack. ENV variables can be set through the web interface or uploaded as a .ENV file. The following variables are required:

- PUID
- PGID
- TZ
- MEDIADIR # a location for downloads and media files
- VPN_PROVIDER
- VPN_USERNAME
- VPN_PASSWORD
- VPN_COUNTRY

### Updating containers
All containers are updated with Ouroboros with the exception of portainer-agent (I've found this to be problematic.) Containers can also be updated through Portainer.
