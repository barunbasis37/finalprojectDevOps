# CI/CD Setup Documentation

## Overview
This document describes the Continuous Integration and Continuous Deployment (CI/CD)
architecture for the finch-frontend and finch-backend applications using GitHub Actions.

## CI/CD Tool
- GitHub Actions

## Pipeline Architecture
Each application has an independent pipeline:
- Source Checkout
- Dependency Installation
- Linting
- Testing
- Build
- Docker Image Creation
- Push to Container Registry

## Frontend Pipeline Stages
1. Code checkout
2. Node.js setup
3. Dependency installation
4. ESLint checks
5. Unit tests
6. Production build
7. Docker image build
8. Docker image push

## Backend Pipeline Stages
1. Code checkout
2. Node.js setup
3. Dependency installation
4. ESLint checks
5. Unit & integration tests
6. Docker image build
7. Docker image push

## Triggering the Pipelines
Pipelines trigger automatically on:
- Push to `main` branch
- Pull requests to `main`
- Changes limited to frontend or backend directories

## Monitoring the Pipelines
1. Navigate to the GitHub repository
2. Click on the "Actions" tab
3. Select the workflow run
4. View job logs and execution status

## Container Registry
- Docker Hub
- Images are tagged with:
  - `latest`
  - Git commit SHA for traceability

## Benefits
- Automated quality checks
- Consistent build artifacts
- Immutable Docker images
- Scalable foundation for Kubernetes deployment
