# DEPLOYMENT - cnalks.cn

## Production Intent

`CNalks/cnalks.cn` owns only the root personal homepage. Production routing must
preserve ai4health and AI Lab routes before falling back to this static site.

Recommended route order:

1. `/api/*`, `/health`, `/docs` -> AI Lab backend.
2. `/ai4health/*` -> ai4health frontend/static directory.
3. `/` and static homepage assets -> this repository's `dist/`.

## Build

```bash
npm ci
npm run build
```

## Static Artifact

The homepage artifact is:

```text
dist/
  index.html
  _astro/
  favicon.svg
```

## Nginx Shape

```nginx
location /api/ {
  proxy_pass http://127.0.0.1:8000/api/;
}

location = /health {
  proxy_pass http://127.0.0.1:8000/health;
}

location /docs {
  proxy_pass http://127.0.0.1:8000/docs;
}

location /ai4health/ {
  alias /var/www/ai4health/;
  try_files $uri $uri/ /ai4health/index.html;
}

location / {
  root /var/www/cnalks.cn;
  try_files $uri $uri/ /index.html;
}
```

Adjust paths to match the actual host, but keep this route ownership order.
