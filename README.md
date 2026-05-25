# cnalks.cn

Personal homepage and project entry for `cnalks.cn`.

This repository owns the root website only. It must not serve or shadow the
production API proxy under `/api/*` or the ai4health application routes under
`/ai4health/*`.

## Commands

```bash
npm install
npm run dev
npm run build
npm run preview
```

## Routing Contract

| Path | Owner | Notes |
| --- | --- | --- |
| `/` | `CNalks/cnalks.cn` | Personal homepage and project directory. |
| `/ai4health/` | `CNalks/ai4health` | Full monitoring and early-warning platform. |
| `/ai4health/single/` | `CNalks/ai4health` | Single-page lite dashboard under `apps/single-page/`. |
| `/api/*` | `CNalks/AI_lab` | Public backend API proxy. |

See [PROJECT_MAP.md](PROJECT_MAP.md) and [DEPLOYMENT.md](DEPLOYMENT.md).
