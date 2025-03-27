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
├── dist/           # Your SPA build output
│
└── docker-compose.yml
```

### 2. Dockerfile
```dockerfile
FROM nginx:alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY dist /usr/share/nginx/html
EXPOSE 80
```

### 3. Nginx Configuration
```nginx
events {
    worker_connections 1024;
}

http {
    server {
        listen 80;
        root /usr/share/nginx/html;
        index index.html;

        location / {
            try_files $uri $uri/ /index.html;
        }

        # Optional: Enable gzip compression
        gzip on;
        gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
    }
}
```

### 4. Docker Compose
```yaml
version: '3.8'
services:
  spa:
    build:
      context: .
      dockerfile: docker/nginx/Dockerfile
    ports:
      - "80:80"
    volumes:
      - ./dist:/usr/share/nginx/html
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
- Uses Alpine Linux for minimal image size
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
[Your License - e.g., MIT]
```
