# Homelab External Monitoring Stack

**Deployed on:** Hostinger VPS (72.62.48.62)
**Purpose:** External monitoring and alerting for homelab infrastructure
**Status:** 🟢 Production

## Services

- **Uptime Kuma** (Port 3001) - Service monitoring
- **ntfy** (Port 8080) - Push notifications
- **Dozzle** (Port 8888) - Docker log viewer
- **Tailscale** (Native) - VPN mesh to homelab

## Quick Start

```bash
# View services
docker compose ps

# View logs
docker compose logs

# Restart all
docker compose restart

# Update images
docker compose pull && docker compose up -d
```

## Documentation

See homelab repository for complete documentation:
- VPS-Deployment-Runbook.md
- uptime-kuma-setup.md
- ntfy-mobile-setup.md

## Deployment

```bash
# Deploy stack
docker compose up -d

# Check health
docker compose ps
docker stats --no-stream
```

## Backup

```bash
# Backup data
tar -czf backup-$(date +%Y%m%d).tar.gz \
  uptime-kuma/data \
  ntfy/config \
  docker-compose.yml

# Copy to homelab
scp backup-*.tar.gz truenas:/mnt/secondary-pool/backups/vps/
```

## Maintenance

**Weekly:**
- Check Uptime Kuma alerts
- Verify ntfy notifications working

**Monthly:**
- Update Docker images
- Check disk usage
- Review logs

---

**Maintained by:** DnaMes
**Last updated:** 2025-12-14
