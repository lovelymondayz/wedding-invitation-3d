# wedding-invitation-3d

A single-page 3D wedding invitation. One self-contained `index.html` — no
build step, no backend, no database.

**Stack:** vanilla HTML/CSS/JS, three.js r128, GSAP 3.12.5 + ScrollTrigger.
All third-party assets are vendored under `vendor/`, so the page renders with
no external network access.

> This project is intentionally HTML-only. The fleet `CONSTITUTION.md` stack
> rules (Go + Gin + pgx + PostgreSQL + React/TS/Tailwind) do not apply here.

## Run

```bash
docker compose up -d --force-recreate
# http://localhost:3012
```

Any static file server pointed at this directory works too:

```bash
python3 -m http.server 3012
```

## Edit the content

Everything editable lives in the `CONFIG` object at the top of the `<script>`
block in `index.html` — names, date, time, venue, address, and the four
chapter headings/stories.

## Deploy

```bash
docker compose build --no-cache
docker compose up -d --force-recreate
```

## Files

```
index.html          the whole page (markup + styles + scene)
vendor/             three.js, GSAP, ScrollTrigger, self-hosted fonts
nginx.conf          static hosting + cache headers
Dockerfile          nginx:alpine, no build stage
docker-compose.yml  single service on host port 3012
```
