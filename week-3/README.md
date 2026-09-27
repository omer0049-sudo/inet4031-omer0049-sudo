# Week 3, Containerizing the Incident Tracker

## What this does
Packages the Flask incident tracking app into a Docker image and runs it as a container, reachable on port 8080.

## Requirements
- Docker
- A `.env` file in `app/` (copy `app/.env.example` and fill in `FLASK_SECRET_KEY`)

## Build and run

## Verify
Or visit http://localhost:8080 in a browser.

## Known limitation
Data does not persist across `docker rm`, no volume is configured yet.
