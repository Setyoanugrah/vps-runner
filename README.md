# vps-runner

Ephemeral Ubuntu box on GitHub Actions, reachable over Tailscale.

- Runs on `workflow_dispatch`, every 6 hours, and on push to `main`.
- Joins the tailnet as `runzzx1`.
- SSH user: `runzzx1` (password from repo secret `SSH_PASSWORD`).
- Max job lifetime: 355 minutes (GitHub hard cap is 6h).

## Secrets

| Secret | Value |
| --- | --- |
| `TS_AUTHKEY` | Tailscale auth key (reusable + ephemeral recommended) |
| `SSH_PASSWORD` | password for the `runzzx1` user |

## Use

Actions -> vps-runner -> Run workflow. Then read the job summary for the Tailscale IP:

```
ssh runzzx1@<tailscale-ip>
```

## Notes

- The key must be **reusable**, otherwise only the first run can join the tailnet.
- Mark it **ephemeral** in the Tailscale admin console so dead nodes are removed
  and the `runzzx1` name stays free.
- Each run gets a fresh machine: nothing persists between sessions.
