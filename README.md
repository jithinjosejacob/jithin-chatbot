---
title: jithin-chatbot-space
app_file: app.py
sdk: gradio
sdk_version: 6.2.0
python_version: "3.11"
---

Deployed to https://huggingface.co/spaces/jithinjacob2011/jithin-chatbot-space

Create at .venv virtual python environment

Create a .env file with below keys
HF_TOKEN
pushover_user
pushover_token

### Local Setup ###

Create pyproject.toml to build uv dependancies - uv init --no-readme --no-workspace

# Install dependencies

uv sync

# Run the app

uv run python app.py