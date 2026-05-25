# PROJECT_MAP - cnalks.cn

`cnalks.cn` is the personal homepage and top-level project directory. It is not
the source of truth for every product detail; each project keeps its own
deployment notes in its own repository.

## Repository Roles

| Project | Repository | Production Role | Branch Rule |
| --- | --- | --- | --- |
| Personal homepage | `CNalks/cnalks.cn` | Root site and project directory | `main` is production. |
| ai4health full platform | `CNalks/ai4health` | Monitoring and early-warning frontend | `main` is production platform. |
| ai4health single-page lite | `CNalks/ai4health/apps/single-page` | Lite public dashboard | Managed inside `ai4health/main`. |
| AI Lab backend | `CNalks/AI_lab` | Time-series analysis, forecast, alert API | `main` is Aliyun public line; `deploy/tianyi` is Tianyi-specific. |

## URL Contract

| URL | Owner | Deployment Contract |
| --- | --- | --- |
| `https://www.cnalks.cn/` | `cnalks.cn` | Static homepage. |
| `https://www.cnalks.cn/ai4health/` | `ai4health` | Full frontend entry. |
| `https://www.cnalks.cn/ai4health/single/` | `ai4health/apps/single-page` | Lite single-page entry. |
| `https://www.cnalks.cn/api/*` | `AI_lab` | Reverse proxy to backend API. |
| `https://www.cnalks.cn/health` | `AI_lab` | Backend health check when routed through proxy. |
| `https://www.cnalks.cn/docs` | `AI_lab` | Backend API docs when exposed. |

## Non-Goals

- Do not serve `/api/*` from the static homepage.
- Do not copy the full ai4health frontend into this repository.
- Do not treat `ai4health_single` as a formal GitHub repository name.
- Do not merge Tianyi-only backend changes into `AI_lab/main` without review.

## Local Development

```bash
npm install
npm run dev
npm run build
```

The build output is `dist/` and can be served as a static site.
