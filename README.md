# miso-site

Personal site and portfolio.

**Live:** [miso-site](https://miso-site.onrender.com/)

## Status

Core infrastructure is live and deployed. Site content and the admin panel are still being built.

- [x] Next.js + TypeScript app scaffolded
- [x] Dockerised and deployed to Render
- [x] GitHub Actions CI (lint + build) gating merges to `main`
- [ ] Site content (home, about, project case studies)
- [ ] Admin panel with authenticated content editing

## Tech stack

| Layer | Choice |
|---|---|
| Framework | Next.js (React + TypeScript) |
| Styling | Tailwind CSS |
| Database | Supabase (Postgres + client SDK) |
| Containerization | Docker |
| Hosting | Render (Docker-based Web Service) |
| CI | GitHub Actions (lint, build) |

## Getting started

```bash
git clone https://github.com/sofieothilie/miso-site.git
cd miso-site
npm install
npm run dev
```

App runs at `http://localhost:3000`.

### Environment variables

Copy `.env.example` to `.env.local` and fill in your Supabase project values (found in Supabase dashboard > Project Settings > API):

```
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=
```


## Deployment

The app is containerized and deployed to [Render](https://render.com) as a Docker-based Web Service.

- **Dockerfile:** [`docker/Dockerfile`](./docker/Dockerfile)
- **Build context:** repo root (`.`)
- Render auto-deploys on every push to `main`

To build and run the image locally:

```bash
docker build -f docker/Dockerfile -t miso-site .
docker run -p 3000:3000 miso-site
```

## CI/CD

[`.github/workflows/ci.yml`](./.github/workflows/ci.yml) runs on every push and pull request against `main`:

1. Install dependencies
2. Lint
3. Build

`main` is protected by a GitHub ruleset requiring this check to pass before changes are merged.

## Roadmap

**Admin panel** — content (site copy, project write-ups, blog posts) will be editable through an authenticated `/admin` panel instead of direct repo edits, using Supabase Auth or Auth.js for login. This will introduce these additional environment variables:

```
SUPABASE_SERVICE_ROLE_KEY=   # server-side only, for writes that bypass RLS
AUTH_SECRET=                 # if using Auth.js instead of Supabase Auth directly
```
**Some breakable easter egg

# Micro services

## Simple browser game

Implement a simple browser game which allows users to interact smoothly with the game. Needs to apply cookies to persist across sessions. No log in, on purpose. Microservice?

## Some AI implementation

Some AI implementation, e.g. chatbot. 

## Some statistical site

Some data visualisation. Large database. Load dynamically.
Allow people to call from it, as an API

