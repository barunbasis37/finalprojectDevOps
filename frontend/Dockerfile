# ---------- Build Stage ----------
FROM node:18-alpine AS builder

WORKDIR /app

# Copy dependency manifests first (cache optimization)
COPY package*.json ./

RUN npm ci

# Copy application source
COPY . .

# Build production assets
RUN npm run build


# ---------- Runtime Stage ----------
FROM nginx:1.25-alpine

# Remove default nginx config
RUN rm /etc/nginx/conf.d/default.conf

# Copy custom nginx config (optional but recommended)
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Copy built assets from builder
COPY --from=builder /app/build /usr/share/nginx/html

# Security hardening
USER nginx

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
