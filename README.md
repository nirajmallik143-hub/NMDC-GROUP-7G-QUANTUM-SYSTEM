# NMDC Operations Solve Desk (MVP)

A small, browser-based operations planning prototype. It lets a user describe an operational bottleneck, calculate a transparent heuristic priority score, see suggested evidence checks, save scenarios locally, and export saved scenarios as JSON.

## Run

No build step or package installation is required. Open `index.html` in a modern browser, or serve this directory with any static HTTP server, for example:

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

## How the score works

The relative priority score is a simple 0–100 weighted heuristic:

- Impact severity: 40% (severity 1–5)
- Estimated downtime: 30% (capped at 40 hours/week)
- Estimated cost impact: 30% (capped at AED 100,000/week)

High is 70–100, Medium is 40–69, and Low is 0–39. The score is not an operational forecast, financial valuation, safety assessment, or optimization result. Suggested checks are general prompts, not instructions to operate equipment. Verify all inputs and decisions with accountable domain experts.

## Data and security

Scenarios are stored in the browser's `localStorage` on the current device. They are not sent to a server and do not sync across devices. Do not enter personal, sensitive, confidential, or security-critical information. Clearing browser storage removes saved scenarios. Exported JSON files may contain the details you entered; store them appropriately.

## Scope and limitations

This is a frontend-only MVP, not a production enterprise system. It has no user accounts, shared database, backend API, live telemetry, integrations, or access controls. It does not use a quantum computer or claim to implement quantum optimization, post-quantum cryptography, encryption, or real-time NMDC data. All scenarios and sample values are user-provided; the sample is illustrative only.

A sensible next step is to validate the workflow and scoring rubric with the intended operations users, then decide on an approved backend, authentication model, data retention rules, and integrations before handling real company information.
