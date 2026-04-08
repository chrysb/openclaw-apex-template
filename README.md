# AlphaClaw Apex Template

Template repo for AlphaClaw-managed Apex and Foundry instances.

This repo is the deploy artifact for managed updates:

- Foundry provisions instances from a pinned git ref in this repo
- Apex checks for updates by comparing the instance's current ref to the newest released ref
- Updating an instance means fetching this repo, checking out the target tag, and recreating the Docker services

## Files

- `Dockerfile`: AlphaClaw runtime image
- `docker-compose.yml`: managed instance compose stack
- `package.json`: pinned AlphaClaw and OpenClaw versions
- `package-lock.json`: generated lockfile for the pinned release

## Release Flow

This repo is intended to be generated from the AlphaClaw release tooling in:

- `/Users/chrysbader/Projects/alphaclaw/scripts/release-managed.mjs`

Railway, Render, and Apex template repos should all be updated from the same AlphaClaw release inputs.

## Notes

- Mutable host files such as `.env`, Caddy config, and app data are not stored in this repo
- Managed instances mount those files from host-owned paths during provisioning and update
- Tags are the release boundary; avoid deploying arbitrary branch heads for managed instances
