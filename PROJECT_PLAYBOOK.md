# Earth HQ — Project Playbook

## Project Name
Earth HQ

## Current Production Version
v1.8

## Current Production URL
https://mecha-task.jessie95908.workers.dev

## Deployment Status
Active

## Last Successful Deployment
2026-06-05

## GitHub Repository
[jessie95908-cmyk/mecha-task](https://github.com/jessie95908-cmyk/mecha-task)

## Deployment Method
GitHub → Cloudflare Auto Deploy

Pushing `main` branch to GitHub automatically triggers Cloudflare deployment to the production URL above.

## Standard Deployment Workflow

1. Update `index.html`
2. `git add .`
3. `git commit -m "describe the change"`
4. `git push origin main`
5. Wait for Cloudflare auto deployment (typically 1–2 minutes)

## Rules

- **Patch-only workflow**: make the smallest possible change to fix the specific issue.
- **Do not rewrite the whole project**.
- **Do not create a new GitHub repository**.
- **Do not create a new Cloudflare project**.
- **Do not create a new URL**: the production URL above must remain unchanged.
