# business-agent-keepalive

A single scheduled GitHub Actions workflow that pings
`https://business-agent-u9e6.onrender.com/health` every 5 minutes.

**Why:** Render's free plan spins an instance down after ~15 minutes without traffic. The ping
keeps the Business Agent dashboard and its agent scheduler running. No application code is stored
in this repository, and the endpoint it calls is public and unauthenticated (`/health`).

If the pings ever stop (GitHub disables scheduled workflows in repositories with no activity for
60 days), nothing breaks — the instance simply sleeps again, and the agents pause until the next
visitor wakes it. The permanent fix is a paid Render instance type.
