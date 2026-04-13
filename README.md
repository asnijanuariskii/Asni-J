# Project

Full-stack application scaffolded with the Kiro Project Template.

## Structure

- `backend/` — API server source code
- `frontend/` — Web app source code
- `tests/` — All tests (backend, frontend, integration, e2e, security, uiux)
- `docs/` — Documentation, OpenAPI spec, decision log
- `infra/` — Docker, Nginx, deploy scripts
- `.kiro/` — Sub-agents, steering, hooks, specs

## Getting Started

1. Install dependencies for backend and frontend
2. Configure environment variables (see `.env.example` files)
3. Configure MCP servers in `~/.kiro/settings/mcp.json`
4. Start developing with Kiro IDE

## Deployment

Push to `main` branch → auto-commit hook → pull on VM → rebuild → restart containers.

See `docs/` and `.kiro/steering/deployment.md` for details.
