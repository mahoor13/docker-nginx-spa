# Nginx Docker SPA Deployment

## Overview
This Docker configuration provides a lightweight, production-ready Nginx server specifically optimized for Single Page Applications (SPAs). Designed to support modern web frameworks like React, Vue, Angular, and Svelte, this setup ensures smooth client-side routing and optimal performance.

## Features
- 🚀 Lightweight Nginx alpine-based image
- 📦 SPA-friendly routing configuration
- 🔒 Secure default settings
- 💻 Easy configuration and customization
- 🌐 Support for multiple SPA frameworks

## Prerequisites
- Docker
- Docker Compose (recommended)
- Built SPA production files

## Quick Start

### 1. Project Structure
```
your-project/
│
├── docker/
│   └── nginx/
│       ├── Dockerfile
│       └── nginx.conf
│
├── dist/           # SPA build output
│
└── docker-compose.yml
```

### 2. Docker Compose
```yaml
services:
  spa:
    build:
      context: .
      dockerfile: docker/nginx/Dockerfile
    ports:
      - '80:80'
    volumes:
      - ./dist:/app
```

## Deployment Commands
```bash
# Build your SPA (e.g., React/Vue)
npm run build

# Build Docker image
docker-compose build

# Run container
docker-compose up -d
```

## Performance Optimization
- Uses Alpine Linux for minimal image size (final image is under 50Mb.)
- Enables gzip compression
- Configures proper caching headers
- Supports client-side routing

## Security Considerations
- Uses read-only, non-root Nginx image
- Minimal surface area for potential attacks
- Easy to integrate with SSL/TLS certificates

## Troubleshooting
- Ensure your SPA build files are in the `dist/` directory
- Check Docker logs: `docker-compose logs spa`
- Verify file permissions on build artifacts

## Contributing
Contributions, issues, and feature requests are welcome!

## License
[MIT]
```
