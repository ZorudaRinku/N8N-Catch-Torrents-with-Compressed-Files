# N8N Catch Torrents with Compressed Files

Catches grabbed torrents that end up having .rar files and blacklists them in Radarr/Sonarr and searches to replace them.

---

## Setup

- Create new Webhook connection in Radarr and Sonarr (as POST, On Grab, pointed to the webhook provided at start of n8n workflow)
- Replace all HTTP Requests (🌐 icon) nodes URL fields pointed to their respective services (qbittorrent, radarr, sonarr)
- Replace credentials on all HTTP Request nodes (qBittorrent does not require auth if you've configured the Qbt WebUI to not ask for credentials when on current network)
- Configure [discord notifications](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.discord/) if wanted, otherwise delete the node

## Why

Radarr/Sonarr use hardlinks to link the content from torrents over to media management services like Jellyfin. If the media downloaded is compressed into .rar files, it must be manually decompressed, then cannot be hardlinked over to Jellyfin. Radarr and Sonarr also cannot see what the files are in the torrent (as this is not provided until after the download has begun)
