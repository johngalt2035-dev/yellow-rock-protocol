# Docker Deployment Guide

Yellow Rock Protocol is a set of text templates — there is nothing to build or compile. In a Docker deployment, the protocol templates are **volume-mounted** into the OpenClaw gateway container alongside [Yellow Rock Memory](https://github.com/johngalt2035-dev/yellow-rock-memory).

## Architecture

```
┌─────────────────────────────────────────────────┐
│  Docker Host                                    │
│                                                 │
│  ┌───────────────────┐  ┌────────────────────┐  │
│  │ openclaw-gateway   │  │ yellow-rock-memory │  │
│  │ :18789             │──│ :9077              │  │
│  │                    │  │ SQLite + forensics  │  │
│  │  /workspace/       │  └────────────────────┘  │
│  │   yellow-rock-     │                          │
│  │   protocol/        │  Volume mount (read-only)│
│  │   templates/ ◄─────┼── ./templates/           │
│  └───────────────────┘                           │
└─────────────────────────────────────────────────┘
```

## Quick Start

```bash
# Clone both repos side by side
git clone https://github.com/johngalt2035-dev/yellow-rock-protocol.git
git clone https://github.com/johngalt2035-dev/yellow-rock-memory.git

# Deploy the full stack from the memory repo
cd yellow-rock-memory
cp .env.example .env
# Edit .env — set GRM_API_KEY, GRM_PRINCIPAL_ID, OPENCLAW_GATEWAY_TOKEN, XAI_API_KEY
docker compose -f docker-compose.full.yml up -d
```

See [Yellow Rock Memory DOCKER.md](https://github.com/johngalt2035-dev/yellow-rock-memory/blob/main/DOCKER.md) for full-stack compose configuration and environment variable reference.

## Volume Mount

The protocol templates are mounted read-only into the OpenClaw workspace:

```yaml
# In docker-compose.full.yml (lives in yellow-rock-memory repo)
services:
  openclaw:
    volumes:
      - ../yellow-rock-protocol/templates:/home/node/.openclaw/workspace/yellow-rock-protocol:ro
```

This makes all templates available to OpenClaw agents at `/home/node/.openclaw/workspace/yellow-rock-protocol/`.

## Updating Templates

Because templates are bind-mounted from the host, updates are instant:

```bash
cd yellow-rock-protocol
git pull    # Templates are immediately available inside the container
```

No container restart needed.

## Container Runtime (macOS)

Docker requires a Linux VM on macOS. Recommended:

| Runtime | Install | Notes |
|---|---|---|
| **OrbStack** (recommended) | `brew install orbstack` | Lightweight, fast, no VM download |
| Docker Desktop | [docker.com](https://www.docker.com/products/docker-desktop/) | Official, commercial license required |
| Colima | `brew install colima docker` | Free, downloads ~600MB VM on first start |

## Without Docker

If you don't need containerized deployment, just clone and use the templates directly. See [INSTALL.md](INSTALL.md) for platform-specific instructions.
