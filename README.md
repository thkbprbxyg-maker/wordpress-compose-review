# WordPress + MariaDB (Docker Compose)

This repository provides a minimal Docker Compose setup to run **WordPress** with a **MariaDB** database.
It is designed to be simple, reproducible, and safe regarding secrets: **no passwords/tokens are stored in the repository**.

## Table of Contents
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

1. Repository clone.
```bash
git clone git@github.com:thkbprbxyg-maker/wordpress-compose-review.git
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
   - WordPress
   - MariaDB

4. Open WordPress in your browser
```bash
http://<your_ip>:8080
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


## Configuration

Configuration is handled via a .env file.
```bash
cp .env.example .env
```

Adjust the values inside .env (ports, credentials, blog name, etc.).
The .env file is not committed to the repository.

Start / Stop

Start containers:
```bash
docker compose up -d
```
Check status:
```bash
docker compose ps
```
Stop containers:
```bash
docker compose down
```


## Persistence

Data is persisted using Docker volumes:
	•	MariaDB: database data is retained
	•	WordPress uploads: media and content persist

Restarting containers will not remove data.


##Logs

View logs:
```bash
docker compose logs
```
Follow logs for a specific service:
```bash
docker compose logs -f wordpress
docker compose logs -f db
```


## Reset Everything

Warning: This will remove ALL data (database & uploads)
```bash
docker compose down -v
```


## Security Notes
- No secrets are stored in the repository
-	Credentials are defined only in .env
-	.env is excluded via .gitignore
-	For production use:
-	Use strong passwords
-	Add a reverse proxy with HTTPS
-	Do not expose ports publicly


## Testing Checklist
-	`docker compose up -d` runs without errors
-	WordPress is reachable at http://<your_ip>:<PORT>
-	Login works using .env credentials
-	Restart keeps data intact
-	`docker compose down -v` fully resets the environment


## Troubleshooting

Port already in use
```bash
ERROR: bind: address already in use
```
→ Change WORDPRESS_HOST_PORT in .env.

Database startup delay
→ MariaDB may take a few seconds; WordPress will retry automatically.

Broken setup 
```bash
docker compose down -v
docker compose up -d
```


## Quickstart Note (Recommended)

The Quickstart section should begin with:
```bash
git clone https://github.com/thkbprbxyg-maker/wordpress-compose-review.git
cd wordpress-compose-review
```
Then continue with the .env setup.








