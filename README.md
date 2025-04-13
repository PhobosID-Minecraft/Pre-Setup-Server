
# PhobosID's Pre-Build Server

This is a PaperMC 1.21.4 Build #224 Server, Pre-Build and Pre-Configurated for my Server needs. Hosted on Localhost and tunnelled using Playit.gg.

## Specifications

Below is the Specifications of the Server. It can roughly host 10 players at once.
- CPU: Intel Pentium G2030 (2 cores + 2 threads)
- RAM: TeamGroup 2x4GB DDR3-1333MHz
- Storage: TeamGroup GX2 SSD 120GB SATA
- OS: Linux Mint 20.3 Una
Whole PC is dedicated for this server to ensure smooth gameplay.

## How to Run

To Run the Server, use the pre-defined ``start.sh``. It uses Aikar's Flag to ensure optimized gameplay across server.

```bash
cd server && /bin/bash ./start.sh
```

To Automatically Run after Computer/Server Reboot, and Make it accessible using SSH, Follow these steps:

1. Create a new user for minecraft purposes without sudo authorities.
```bash
sudo adduser manager
```
2. Create Systemd Service for this Server
```bash
sudo nano /etc/systemd/system/minecraft.service
```
3. Paste this following in GNU Text Editor that have opened:
```txt
[Unit]
Description=Minecraft PaperMC Server
After=network.target

[Service]
User=manager
WorkingDirectory=/home/owner/server
ExecStart=/home/owner/server/start.sh
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```
4. Reload Systemd and Enable the Service
```
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable minecraft
```
5. Start the Server
```
sudo systemctl start minecraft
```
To check if it's really start
```
sudo systemctl status minecraft

```