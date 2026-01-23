# WordPress + MariaDB (Docker Compose)

## Overview
This repository provides a minimal Docker Compose setup to run **WordPress** with a **MariaDB** database.
It is designed to be simple, reproducible, and safe regarding secrets: **no passwords/tokens are stored in the repository**.

## Table of Contents
- [Overview](#overview)
- [Repository Contents](#repository-contents)
- [Prerequisites](#prerequisites)
- [Quickstart](#quickstart)
- [Usage](#usage)
  - [Configuration](#configuration)
  - [Start / Stop](#start--stop)
  - [Persistence](#persistence)
  - [Logs](#logs)
  - [Reset Everything](#reset-everything)
- [Security Notes](#security-notes)
- [Testing Checklist](#testing-checklist)
- [Troubleshooting](#troubleshooting)



## Repository Contents
- `docker-compose.yaml` — Defines two services: `wordpress` and `db`, plus volumes and a shared network.
- `.env.example` — Example environment file (copy to `.env` and adjust values).
- `.gitignore` — Ensures `.env` and other irrelevant files are not committed.
- `README.md` — Documentation for setup and usage.

## Prerequisites
- Docker Engine + Docker Compose plugin installed
- A machine reachable via HTTP on the configured port (default: `8080`)

## Quickstart

1. Repository klonen1.
```bash
git clone https://github.com/thkbprbxyg-maker/wordpress-compose.git
cd wordpress-compose
  ```

2. Copy the example env file:
   ```bash
   cp .env.example .env
   ```

3. Start the containers
   ```bash
   docker compose up -d
   ```
   This will start:
	•	WordPress
	•	MariaDB

4. Open WordPress in your browser
```bash
http://localhost:8080
```
Login credentials are defined in your .env file.

5. Stop the containers
```bash
docker compose down
```
6. (Optional) Reset everything
  This will remove all data (database & uploads).
```bash
docker compose down -v
```
