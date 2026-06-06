# P0 Daycare — CIPHER World

Live monitoring dashboard for Patient Zero (P0), a from-scratch language model.
Static site deployed on Netlify; live data is proxied to the training droplet.

- **index.html** — the dashboard (CIPHER tiger + dojo/lab/den scenes, live stats)
- **_redirects / netlify.toml** — proxy `/api/*` to the droplet (24.144.111.138)
  server-side, so the HTTPS page can read the HTTP training APIs with no
  mixed-content or CORS issues.

The dashboard uses relative `/api/...` paths; Netlify proxies them to:
- `/api/status` → droplet `:8001` (live training status)
- `/api/op/*`   → droplet `:8002` (operator bus)

Approvals are handled in Slack (tap-to-approve), not in this page.
