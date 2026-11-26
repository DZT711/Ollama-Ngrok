# Ollama-Ngrok Project Rules

Apply these rules to changes in this directory.

## Secrets and configuration

- Never place Ngrok tokens or other credentials in notebooks, source, outputs, or documentation.
- Load `NGROK_AUTHTOKEN` from a local `.env`; retain support for `NGROK_TOKEN` only for backward compatibility.
- Keep `.env` ignored and keep `.env.example` limited to placeholders.
- In Colab, document that `.env` must be uploaded or mounted before the notebook runs.

## Notebook behavior

- Preserve the existing interactive manager notebooks and their commands.
- For automated setup, install or update Ollama at runtime and use the official Ollama library as the source of model discovery.
- Resolve a newest model dynamically at runtime; do not hard-code a supposedly newest model version.
- Keep every available model in the catalogue discoverable. Use pagination to manage fetch and display costs, and keep later pages reachable until the source is exhausted. Do not impose a fixed total model or page cap for performance. If fetching stops early, label the results as partial.
- Do not bulk-download catalogue models. Pull only a model the user explicitly selected or the documented single bootstrap model.
- Describe model-agent compatibility as a configurable heuristic unless it is verified by a specific runtime capability check.

## Change and validation rules

- Make the smallest scoped change that satisfies the request.
- Preserve `.ipynb` JSON structure and validate it after edits.
- Compile each changed Python code cell after normalizing Jupyter shell-magics when necessary.
- Do not run model downloads, Ngrok tunnel creation, or other paid/external side effects unless the user explicitly asks to execute them.
