# vps-runner

One job, one output: **credentials for `runzzx1`**.

Every run:
1. joins the tailnet as `runzzx1`;
2. creates the `runzzx1` user with a **fresh random password**;
3. publishes `host / user / password / login` to the job summary and to
   `ntfy.sh/rzx1-9f2c7b7a`;
4. stays alive ~5h45m.

## Read the credentials

```bash
curl -s "https://ntfy.sh/rzx1-9f2c7b7a/json?poll=1" | tail -1
```

or: Actions -> latest run -> job `runzzx1` -> Summary.

## Login

```bash
ssh runzzx1@<host>
```

## Secret

| Secret | Value |
| --- | --- |
| `TS_AUTHKEY` | Tailscale auth key (reusable + ephemeral) |

Nothing else is configured. Password is generated per session and never stored.
