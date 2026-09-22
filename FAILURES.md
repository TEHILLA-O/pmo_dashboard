# Failure modes, fixes, and results

Honest engineering notes for this project. Nothing here is invented for polish.

## What can go wrong

- **Vercel picking the Python/Streamlit side instead of the Next static export.** Impact: failed or wrong deploy. Mitigation: root `vercel.json` builds `web/` and publishes `web/out`; docs say set Framework Preset to Other if needed.
- **Assuming Vercel edits are durable.** Impact: lost project edits after refresh on another browser. Mitigation: Data/Admin writes **localStorage** only; ship changes for everyone via `scripts/export_bundle_json.py` + commit `web/data/bundle.json`.
- **Streamlit and Next diverging.** Impact: two truths for portfolio metrics. Mitigation: shared Python export pipeline feeds the Next bundle; Streamlit marked legacy.
- **Sample data mistaken for a live PMO feed.** Impact: executive misread. Mitigation: README states bundled/sample data and reset control.

## What went wrong

**No recorded production incident in this repo yet.** Commit history shows iterative UI feature work (home overview, milestones CRUD, resources) rather than outage reports. Repo README even references a historical `pmo-dashbard` spelling for the GitHub remote.

## How it was resolved

- Next.js 14 app under `web/` is the recommended path; Streamlit remains optional/local/Docker.
- Export script regenerates `bundle.json` from the same sample pipeline utilities.

## Results

- Successful demo: `cd web && npm install && npm run dev` (or Vercel deploy of static export).
- Live demo URL in repo metadata. No SLA or portfolio KPI accuracy claims beyond the sample charts you see locally.
