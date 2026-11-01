# PMO dashboard web app

The Next.js 14 front end of the PMO Portfolio Intelligence Dashboard. It builds to a static site in `out/` and reads its data from `data/bundle.json`.

```bash
npm ci
npm run lint
npm run build   # static export to out/
npm run dev     # development server; open the address it prints
```

| Path | What it is |
| --- | --- |
| `app/` | one folder per page (executive, portfolio, risk, resources, prioritization, milestones, weekly, predictive, admin) |
| `components/` | charts, panels and the dashboard shell |
| `contexts/portfolio-context.tsx` | loads the bundle and keeps browser edits in localStorage |
| `lib/` | types, metrics, health and export helpers |
| `data/bundle.json` | sample data written by `scripts/export_bundle_json.py` in the repo root |

See the [main README](../README.md) for how the data is generated, deployment and limitations.
