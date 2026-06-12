# Roadmap

## Phase 1: OpenRouter Compatibility (current)

Make the entire pipeline work with OpenRouter by switching from the default OpenAI endpoint to any OpenAI-compatible provider.

**Tasks:**
- [ ] Add `base_url` parameter to `OpenAI()` client in all pipeline files (1_planning.py, 2_analyzing.py, 3_coding.py, 3.1_coding_sh.py, 4_debugging.py, eval.py, 1.2_rag_config.py)
- [ ] Make `cal_cost()` in `utils.py` gracefully handle unknown/third-party models (return zero cost instead of KeyError)
- [ ] Suppress `reasoning_effort` parameter for models that don't support it
- [ ] Create `scripts/run_openrouter.sh` — bash script with `OPENAI_BASE_URL` already set
- [ ] Update existing `run.sh` to document the `OPENAI_BASE_URL` env var option
- [ ] Verify end-to-end run with a free OpenRouter model (e.g., Gemma 4)

## Phase 2: Polish & Documentation

Solidify the fork's changes and make them easy to adopt.

**Tasks:**
- [ ] Document model compatibility notes in `tech-stack.md`
- [ ] Add troubleshooting section for common OpenRouter issues (rate limits, model unavailability, auth errors)
- [ ] Clean up commented-out code and stale model entries in `utils.py`
