# EdgeEver Persistent Storage Configuration Guide

This guide covers configuring persistent storage for EdgeEver to ensure your notes, media, and application data survive container restarts and updates.

## Overview

EdgeEver uses Docker volumes to persist data. The main data directory (`/data`) contains:
- **SQLite database**: All notes, notebooks, and metadata
- **Attachments & media**: Images, files, and embedded content
- **Application state**: User sessions, caches, and configuration

## Volume Structure

```
/data/
├── database.db          # SQLite database with all notes and metadata
├── media/               # Attachments, images, and embedded files
├── backups/             # Backup archives and exports
└── cache/               # Temporary cache (can be safely cleared)
```

## Docker Compose Setup (Recommended)

The provided `compose.yaml` includes three persistent volumes by default:

### 1. Main Data Volume (`edgeever-data`)
```yaml
edgeever-data:/data
```
- Stores the SQLite database, media, and application state
- Managed by Docker; persists across container restarts
- Use this for typical deployments

### 2. Media Volume (Optional, Recommended for Large Libraries)
```yaml
edgeever-media:/data/media
```
- Separates media/attachment storage from the main database
- Enables easier backup and restore of large media libraries
- Simplifies scaling if using remote S3 storage later
- Useful if your note library grows beyond 10,000+ items with many attachments

### 3. Backups Volume (Optional)
```yaml
edgeever-backups:/data/backups
```
- Dedicated space for backup archives and exports
- Keeps backups separate from live data
- Recommended for production deployments

## Host-Mounted Storage (Alternative)

To store data directly on your server's filesystem instead of Docker volumes, uncomment the alternative `volumes` section in `compose.yaml`:

```yaml
volumes:
  - ./data:/data                    # All data in ./data directory
  - ./media:/data/media             # Attachments in ./media subdirectory
  - ./backups:/data/backups         # Backups in ./backups subdirectory
```

Benefits:
- Direct filesystem access for backups and management
- Easier to inspect and troubleshoot file-level issues
- Compatible with standard Linux file permissions and ownership
- Simple to integrate with NAS or network storage

### Setup Steps for Host-Mounted Storage

1. **Create directories on your server**:
   ```bash
   mkdir -p data media backups
   chmod 755 data media backups
   ```

2. **Update `compose.yaml`**: Replace the `volumes:` section under the `edgeever` service with:
   ```yaml
   volumes:
     - ./data:/data
     - ./media:/data/media
     - ./backups:/data/backups
   ```

3. **Start the container**:
   ```bash
   docker compose up -d
   ```

4. **Verify**:
   ```bash
   ls -la data/
   # Should see: database.db, media/, backups/, cache/
   ```

## Running with Docker (Simplified)

If you prefer not to use `docker-compose`, run EdgeEver directly with volumes:

```bash
# Create named volumes
docker volume create edgeever-data

# Run the container
docker run -d \
  --name edgeever \
  --restart unless-stopped \
  -p 4000:4000 \
  -e EDGE_EVER_AUTH_PASSWORD="your-secure-password-here" \
  -v edgeever-data:/data \
  edgeever:latest
```

Or with host-mounted storage:

```bash
mkdir -p ./edgeever-data
docker run -d \
  --name edgeever \
  --restart unless-stopped \
  -p 4000:4000 \
  -e EDGE_EVER_AUTH_PASSWORD="your-secure-password-here" \
  -v ./edgeever-data:/data \
  edgeever:latest
```

## Backup and Recovery

### Backup Your Data

**Using Docker Compose volumes**:
```bash
# Create a compressed backup of all data
docker run --rm \
  -v edgeever-data:/data \
  -v $(pwd):/backup \
  alpine tar czf /backup/edgeever-backup.tar.gz -C / data
```

**Using host-mounted storage**:
```bash
# Simple file copy
tar czf edgeever-backup.tar.gz data/ media/ backups/
```

### Restore from Backup

**Extract to Docker volume**:
```bash
docker run --rm \
  -v edgeever-data:/data \
  -v $(pwd):/backup \
  alpine tar xzf /backup/edgeever-backup.tar.gz -C /
```

**Extract to host directory**:
```bash
tar xzf edgeever-backup.tar.gz
```

## Storage Scaling

### Small Libraries (< 5,000 notes)
- Use single `edgeever-data` volume
- Minimal separate media volume needed
- Estimated size: 50MB–500MB

### Medium Libraries (5,000–50,000 notes with images)
- Recommended: Separate `edgeever-media` volume
- Easier backup/restore management
- Estimated size: 500MB–5GB

### Large Libraries (> 50,000 notes or extensive media)
- Use separate media volume
- Consider remote S3-compatible storage (see "Advanced Object Storage" in main README)
- Monitor disk space and add storage as needed
- Estimated size: 5GB–100GB+

## Environment Variables for Storage

Set these in `.env` or via `docker compose` to customize storage behavior:

```env
# Data directory location (inside container—do not change)
EDGE_EVER_DATA_DIR=/data

# Optional: Remote S3-compatible storage for attachments
# EDGE_EVER_S3_BUCKET=my-bucket
# EDGE_EVER_S3_REGION=us-east-1
# EDGE_EVER_S3_ACCESS_KEY=...
# EDGE_EVER_S3_SECRET_KEY=...
```

Configure remote storage via the EdgeEver UI: **Settings → Advanced → OSS object storage**.

## Monitoring Storage

### Check volume usage:
```bash
docker system df
```

### View volume details:
```bash
docker volume inspect edgeever-data
```

### Monitor disk space during runtime:
```bash
docker exec edgeever du -sh /data/*
```

### Container resource limits:
To prevent uncontrolled disk growth, set memory limits in `compose.yaml`:
```yaml
services:
  edgeever:
    mem_limit: 1g
    memswap_limit: 2g
```

## Troubleshooting

### No storage appears after restart
- Verify volume exists: `docker volume ls`
- Check volume mount: `docker inspect edgeever | grep -A 10 Mounts`
- Ensure correct path in `compose.yaml`

### Running out of disk space
- Check what's consuming space: `docker exec edgeever du -sh /data/*`
- Clean cache: `docker exec edgeever rm -rf /data/cache/*`
- Move media to external storage or remote S3

### Permission denied on host-mounted storage
- Fix permissions: `sudo chown -R 1000:1000 ./data`
- Container runs as user `bun` (UID 1000)

### Database corruption after power loss
- Stop container: `docker compose down`
- Restore from backup (see "Restore from Backup" above)
- Restart: `docker compose up -d`

## Best Practices

1. **Use named volumes or host-mounted storage**, not ephemeral containers
2. **Separate media into its own volume** for libraries > 5,000 notes
3. **Schedule regular backups** (weekly or daily)
4. **Monitor disk usage** and add storage proactively
5. **Test restore procedures** before relying on backups
6. **Document your storage setup** for team handovers
7. **Use `docker compose`** for easier management and reproducibility

## Next Steps

- See the main [README.md](README.md) for feature overview and deployment options
- Review [deploy-docker.md](deploy-docker.md) for advanced Docker configuration
- Check [self-hosting-architecture.md](self-hosting-architecture.md) for production setups
