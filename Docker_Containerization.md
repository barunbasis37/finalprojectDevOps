# Docker Containerization Documentation

## Overview
This document describes the Docker containerization strategy for the
finch-frontend and finch-backend applications.

The goal is to produce lightweight, secure, and production-ready images
that integrate seamlessly with CI/CD pipelines and Kubernetes.

---

## Dockerfile Design Principles

### 1. Multi-Stage Builds
- Separate build and runtime environments
- Reduce final image size
- Exclude development dependencies

### 2. Layer Caching Optimization
- Copy package.json before application source
- Enables faster rebuilds

### 3. Minimal Base Images
- node:18-alpine
- nginx:alpine

### 4. Security Hardening
- Non-root users in runtime containers
- Minimal attack surface
- No secrets baked into images

---

## Frontend Image
- Build stage compiles static assets
- Runtime stage serves assets using NGINX
- Exposes port 80

## Backend Image
- Node.js runtime
- Environment-based configuration
- Exposes port 5000

---

## .dockerignore Usage
- Excludes unnecessary files
- Reduces build context size
- Improves build performance
- Prevents sensitive files from leaking

---

## Local Development with Docker Compose

### Build and Start Services
```bash
docker-compose up --build
