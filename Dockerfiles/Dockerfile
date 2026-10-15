# Use the official Python image
FROM mcr.microsoft.com/devcontainers/python:3.12-bookworm

# --- System packages ----------------------------------------------------------
# Tesseract (optional OCR) – remove if not needed.
RUN apt-get update && apt-get install -y --no-install-recommends \
    tesseract-ocr \
    && rm -rf /var/lib/apt/lists/*

# --- Poetry --no-cache-dir ------------------------------------------------------------------
RUN pip install --no-cache-dir poetry

# Tell Poetry to create the venv inside <project-root>
ENV POETRY_VIRTUALENVS_IN_PROJECT=true
# ---------- Make the venv automatically priority ----------
ENV PATH="/workspace/.venv/bin:$PATH"

# Default command – editable in dev‑container settings or docker‑compose.
CMD ["sleep", "infinity"]
