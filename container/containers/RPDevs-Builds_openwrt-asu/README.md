# OpenWrt Attended Sysupgrade (ASU) Server Stack

The OpenWrt Attended Sysupgrade (ASU) service enables on-demand custom firmware sysupgrade binary generation using cached OpenWrt **ImageBuilder** containers.

## 🚀 Deployment Instructions

### Host Volume Preparation
```bash
sudo mkdir -p /mnt/data/openwrt-asu/public/store /mnt/data/openwrt-asu/redis-data
sudo chown -R 1000:1000 /mnt/data/openwrt-asu
```

### Launch Stack
```bash
docker compose up -d
```

## 🌐 Ingress Integration

- **Internal LAN (Nginx Proxy Manager)**:
  - Domain: `asu.rpdevs.local` / `sysupgrade.rpdevs.local`
  - Target: `http://192.168.1.x:8000`
- **External WAN (Cloudflare Tunnel)**:
  - Domain: `https://asu.rpdevs.com`

## 📡 API Endpoints

- `GET /api/v2/`: API Health Check & Info
- `POST /api/v2/build`: Submit ImageBuilder Sysupgrade Request
- `GET /api/v2/status/{request_hash}`: Check Build Status & Download Links
