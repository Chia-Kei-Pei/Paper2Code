# Tech Stack

## Core Language & Runtime

- **Python 3.10+** — all pipeline code runs in Python
- **Conda / pip** — dependency management via `requirements.txt`

## LLM API Layer

- **OpenAI Python SDK (`openai` >= 1.65.4)** — used by all pipeline stages to call chat completion endpoints
- **OpenRouter** — primary API provider. OpenAI-compatible, so no SDK change is needed; only `base_url` and `api_key` differ.
- **Model**: configurable via `--gpt_version` / `GPT_VERSION`. Free/open models on OpenRouter (e.g., Gemma 4) are the primary target.

## Pipeline Stages (unchanged)

| Stage | Script | Purpose |
|-------|--------|---------|
| Preprocess | `0_pdf_process.py` | Cleans raw PDF JSON |
| Planning | `1_planning.py` | Generates overall plan, architecture, task list, config |
| Config extraction | `1.1_extract_config.py` | Extracts `planning_config.yaml` |
| Analysis | `2_analyzing.py` | Analyzes each file component |
| Coding | `3_coding.py` | Generates code for each file |
| Debugging | `4_debugging.py` | Iterative fix loop (optional) |

## Key Configuration

- **`OPENAI_API_KEY`** — set to the OpenRouter API key
- **`OPENAI_BASE_URL`** — set to `https://openrouter.ai/api/v1`
- **`GPT_VERSION`** — any model ID from OpenRouter (e.g., `google/gemma-4-9b-it`)

These are consumed by an updated `OpenAI(api_key=..., base_url=...)` client initialization across all pipeline files.

## Cost Tracking

- `utils.py` contains a `cal_cost()` function with a static price dictionary.
- For non-OpenAI (e.g., OpenRouter/free) models, cost tracking will gracefully return zero rather than crashing.

## Scripts

- `scripts/run.sh` — bash script for OpenAI API (example paper)
- `scripts/run_latex.sh` — bash script for LaTeX input
- `scripts/run_openrouter.sh` — bash script for OpenRouter (to be created)

## Dependencies

```
openai>=1.65.4
tiktoken>=0.9.0
```

vLLM and transformers are optional (only needed if running local open-source models without OpenRouter).
