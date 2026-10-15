# LLMDemo

> A minimal, reproducible stack for experimenting with large language models (LLMs).

## Features
- **Docker / Dev‑Container**: Pre‑built environment with Python 3.12, Poetry, and the required packages.
- **FastAPI server** – a tiny example that forwards a prompt to the OpenAI API via LangChain.
- **Jupyter notebooks** for quick prototyping.
- **Poetry‑based dependency management** (OpenAI, LangChain, Tesseract, etc.).
- **VS Code extensions** pre‑installed in the dev‑container.

## Quick start – VS Code Dev‑Container
```bash
# 1. Open the repo in VS Code
code .

# 2. Reopen in a Dev‑Container
# Ctrl+Shift+P → Dev Containers: Rebuild and Reopen in Container

# 3. Let VS Code install the deps.  The container will be ready.
```

## Folder structure
```
## Folder structure
├─ .continue/
│   ├─ config.yaml
│   └─ mcpServers/
│       └─ mcp-servers.yaml
├─ Dockerfiles/
│   ├─ docker-compose.yml
│   └─ Dockerfile
├─ images/
│   └─ .gitkeep          # placeholder – add image‑build files here if needed
├─ notebooks/
│   └─ .gitkeep          # placeholder – put Jupyter notebooks here
├─ src/
│   └─ common/
│       ├─ __init__.py
│       └─ .gitkeep
├─ .devcontainer/
├─ .vscode/
├─ .pre-commit-config.yaml
├─ .dockerignore
├─ pyproject.toml
├─ poetry.lock
├─ README.md
```

## Extending
- Add new packages in `pyproject.toml` and run `poetry install`.
- Add new services to `docker-compose.yml` (e.g., a Pinecone database).
- Write new notebooks in `notebooks/`.

## Troubleshooting
- **"Interpreter not found"** – run `poetry install` in the container or add a `postStartCommand` that creates the virtual env.
- **Docker build hangs on `.venv`** – add `.venv` to `.dockerignore`.
- **Automatic virtual‑env activation** – VS Code uses the settings in ./.vscode/settings.json to source the venv whenever the container is reloaded or rebuilt.
{
  "terminal.integrated.shellArgs.linux": [
    "-c",
    "source .venv/bin/activate && exec bash"
  ]
}

## Contributing
1. Fork the repo.
2. Create a feature branch: `git checkout -b my-feature`.
3. Push and open a PR.

Happy LLM hacking!