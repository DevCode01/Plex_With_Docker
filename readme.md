
# Plex Configuration - Environment

The docker-compose.  yml file is designed to orchestrate a suite of media server applications.     
The primary *Purpose* of this setup is to manage and automate the download, organization, and streaming of media content, including movies, TV shows, and music to Plex.     
Each service in this configuration plays a specific role in the media management pipeline.    
Below is a detailed description of each service and its *Purpose*:

## Services Overview
**1.   expressvpn**    
*Purpose*:  Provides a VPN connection to ensure privacy and security for the entire media server setup.  
*Key Features*:  
Routes network traffic through ExpressVPN.  
Essential for maintaining anonymity while downloading or accessing media.  


**2.   flaresolverr**    
*Purpose*:  A proxy server to handle Cloudflare's anti-bot pages.  
*Key Features*:  
Helps bypass CAPTCHA and other browser verification mechanisms.  
*Ports*: **8191** 

**3.   qbittorrent**    
*Purpose*:  A BitTorrent client for downloading media.  
*Key Features*:  
Uses linuxserver/qbittorrent image.  
Configurable download paths for different types of media.  
*Ports*: **8090** 


**4.   xteve**  
*Purpose*:  An IPTV proxy server for managing and streaming live TV channels.  
*Key Features*:  
Manages IPTV playlists and EPG data.  
*Ports*: **34400** 


**5.   jackett**  
*Purpose*:  A proxy server for torrent indexers, enabling Sonarr and Radarr to search for torrents.  
*Key Features*:  
Interfaces with multiple torrent indexers.  
*Ports*: **9117** 


**6.   prowlarr**  
*Purpose*:  An indexer manager/proxy for managing and searching for torrents.  
*Key Features*:  
Acts as a central manager for indexers used by Sonarr, Radarr, and Lidarr.  
*Ports*: **9696** 


**7.   bazarr**  
*Purpose*:  Manages and downloads subtitles for media content.  
*Key Features*:  
Integrates with Sonarr and Radarr to provide subtitles.  
*Ports*: **6767** 


**8.   deluge**  
*Purpose*:  Another BitTorrent client for downloading media.  
*Key Features*:  
Provides an alternative to qBittorrent for torrent downloads.  
*Ports*: **8112** 

**9.   sonarr**  
*Purpose*:  Manages TV show libraries and automates downloading of TV episodes.  
*Key Features*:  
Searches for and organizes TV shows.  
*Ports*: **8989** 

**10.   overseerr**  
*Purpose*:  A request management and media discovery tool for Plex.  
*Key Features*:  
Allows users to request new media content.  
*Ports*: **5055** 

**11.   radarr**  
*Purpose*:  Manages movie libraries and automates downloading of movies.  
*Key Features*:  
Searches for and organizes movies.  
*Ports*: **7878** 

**12.   lidarr**  
*Purpose*:  Manages music libraries and automates downloading of music.  
*Key Features*:  
Searches for and organizes music albums.  
*Ports*: **8686** 

**13.   plex**  
*Purpose*:  A media server to stream media content to various devices.  
*Key Features*:  
Central hub for accessing and streaming media.  
*Ports*: **34400** 

**14.   influxdb**  
*Purpose*:  A time-series database to store monitoring data.  
*Key Features*:  
Stores metrics and logs for media server applications.  
*Ports*: **8086** 

**15.   varken**  
*Purpose*:  A monitoring tool that collects data from various media servers and stores it in InfluxDB.  
*Key Features*:  
Aggregates data for visualization.  

**16.   grafana**  
*Purpose*:  A visualization tool to create dashboards from InfluxDB data.  
*Key Features*:  
Provides graphical interfaces for monitoring media server metrics.  
*Ports*: **3000** 

**17.   tautulli**  
*Purpose*:  Monitors Plex usage and activity.  
*Key Features*:  
Tracks and reports on Plex server activity.  
*Ports*: **8181** 

**18.   sonarr-exporter**  
*Purpose*:  Exposes Sonarr metrics for Prometheus.  
*Key Features*:  
Provides monitoring data for Sonarr.  

**19.   radarr-exporter**  
*Purpose*:  Exposes Radarr metrics for Prometheus.  
*Key Features*:  
Provides monitoring data for Radarr.  

**20.   prowlarr-exporter**  
*Purpose*:  Exposes Prowlarr metrics for Prometheus.  
*Key Features*:  
Provides monitoring data for Prowlarr.  

**21.   telegraf**  
*Purpose*:  Collects metrics from various sources and sends them to InfluxDB.  
*Key Features*:  
Configured to monitor Docker containers.  

**22.   ombi**  
*Purpose*:  Allows users to request new content for Plex.  
*Key Features*:  
User-friendly interface for content requests.  
*Ports*: **3579** 


## Why I used some specific image version
I need to use theses image because I've a specific Grafana configuration who work only with influxbdb 1.8 and varken