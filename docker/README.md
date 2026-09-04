# docker/

Secrets-free `docker-compose.yml` and an `.env.example` template for running n8n via Docker Compose.

**To use:** copy both files into the folder where you'll actually run n8n from (e.g. `~/n8n/`), copy `.env.example` to `n8n.secrets.env` in that same folder and fill in real values (see the comments in the file — generate your own encryption key, don't reuse the placeholder), then `docker compose up -d`.

Real secrets stay in a password manager and in that local, git-ignored `n8n.secrets.env` file — never committed here.

See [`../n8n_how.md`](../n8n_how.md) for the full walkthrough: starting/stopping n8n, creating a workflow, the Docker volumes in use, and troubleshooting.
