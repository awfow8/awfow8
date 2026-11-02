## Hi there 👋

<!--
**awfow8/awfow8** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->


```mermaid
graphTD
    %% Styling
    classDef internet fill:#f9f,stroke:#333,stroke-width:2px;
    classDef security fill:#f96,stroke:#333,stroke-width:2px;
    classDef network fill:#9cf,stroke:#333,stroke-width:2px;
    classDef compute fill:#bbf,stroke:#333,stroke-width:2px;
    classDef storage fill:#fbc,stroke:#333,stroke-width:2px;
    classDef service fill:#9f9,stroke:#333,stroke-width:1px;

    %% Internet Layer
    WAN[🌐 Internet / ISP]:::internet

    %% Security & Routing Layer
    subgraph Edge [Edge & Security]
        Router[🛡️ Firewall / Router <br> e.g., pfSense / OPNsense]:::security
        ReverseProxy[Reverse Proxy <br> e.g., Nginx / Traefik / Caddy]:::security
    end

    %% Network Layer
    subgraph Switching [Core Network]
        Switch[🎛️ Core Managed Switch <br> VLANs configured]:::network
        VLAN10[VLAN 10: Management]:::network
        VLAN20[VLAN 20: Trusted LAN]:::network
        VLAN30[VLAN 30: IoT / Guest]:::network
        VLAN40[VLAN 40: DMZ / Public Services]:::network
    end

    %% Compute Layer
    subgraph Compute [Hypervisors & Bare Metal]
        PVE1[💻 Proxmox VE / ESXi Node 1]:::compute
        PVE2[💻 Proxmox VE / ESXi Node 2]:::compute
    end

    %% Storage Layer
    subgraph Storage_Layer [Storage]
        NAS[💾 NAS <br> e.g., TrueNAS / Unraid]:::storage
    end

    %% Services breakdown
    subgraph Containers_Node1 [VMs / Containers on Node 1]
        Docker1[🐳 Docker Engine]:::compute
        AdGuard[🚫 AdGuard / Pi-hole]:::service
        HomeAssistant[🏠 Home Assistant]:::service
        ArrSuite[🎬 Arr Suite <br> Radarr/Sonarr]:::service
    end

    subgraph Containers_Node2 [VMs / Containers on Node 2]
        Docker2[🐳 Docker Engine]:::compute
        Plex[🍿 Plex / Jellyfin]:::service
        Nextcloud[☁️ Nextcloud]:::service
        Vaultwarden[🔑 Vaultwarden]:::service
    end

    %% Connections
    WAN --> Router
    Router --> ReverseProxy
    Router --> Switch

    %% VLAN Mapping
    Switch --> VLAN10
    Switch --> VLAN20
    Switch --> VLAN30
    Switch --> VLAN40

    %% Physical to Compute
    VLAN10 --> PVE1
    VLAN10 --> PVE2
    VLAN10 --> NAS

    %% Compute to Services
    PVE1 --> Docker1
    Docker1 --> AdGuard
    Docker1 --> HomeAssistant
    Docker1 --> ArrSuite

    PVE2 --> Docker2
    Docker2 --> Plex
    Docker2 --> Nextcloud
    Docker2 --> Vaultwarden

    %% Storage Shares
    NAS -. NFS / SMB .-> ArrSuite
    NAS -. NFS / SMB .-> Plex
    NAS -. Backups .-> PVE1
    NAS -. Backups .-> PVE2
    
    %% Proxy routing
    ReverseProxy --> VLAN40
    VLAN40 --> Nextcloud
    VLAN40 --> Plex


