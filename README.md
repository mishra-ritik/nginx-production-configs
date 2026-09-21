# Nginx Production Configs

Ready-to-adapt Nginx configurations for common deployment setups. Every file is a complete `nginx.conf`, so it can be validated and dropped in directly.

## What's inside

| Folder | Use case | Highlights |
|---|---|---|
| `reverse-proxy/` | Put Nginx in front of an app | Proxy headers, WebSocket support, gzip, rate limiting, security headers, health endpoint |
| `https-letsencrypt/` | TLS termination | HTTP to HTTPS redirect, ACME challenge path, TLS 1.2/1.3, HSTS, OCSP stapling, www to apex redirect |
| `load-balancer/` | Multiple app instances | `least_conn`, passive health checks, backup server, retry on failure |
| `static-spa/` | React / Vue / Angular | Long-lived asset caching, no-cache `index.html`, SPA fallback, multi-stage Dockerfile |

## Validate a config

```bash
docker run --rm \
  -v "$PWD/reverse-proxy/nginx.conf:/etc/nginx/nginx.conf:ro" \
  nginx:1.27-alpine nginx -t
```

Notes: `https-letsencrypt/` needs real certificates at the paths in the file before `nginx -t` will pass. The sample upstreams point to `127.0.0.1` ports; change them to your app or container names.

## Work with me

I'm a DevOps engineer (AWS, Docker, Terraform, CI/CD). I can set up and harden Nginx for your stack, configure HTTPS, and containerize your app.

See also: [docker-production-templates](https://github.com/mishra-ritik/docker-production-templates)
