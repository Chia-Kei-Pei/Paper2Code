# Mission

## Why

PaperCoder is a multi-agent LLM system that transforms scientific machine learning papers into runnable code repositories. It follows a three-stage pipeline — planning, analysis, and code generation — each handled by specialized LLM agents. The system was introduced in the Paper2Code paper (ICLR 2026) and outperforms strong baselines on both the Paper2Code and PaperBench benchmarks.

This repository is a fork focused on making PaperCoder runnable through **OpenRouter** (OpenAI-compatible API) using **cost-effective or free models**, removing the dependency on paid OpenAI API keys while preserving the original pipeline's quality and fidelity.

## Goals

1. **OpenRouter compatibility** — Route all LLM calls through OpenRouter's OpenAI-compatible endpoint so any model available on OpenRouter can be used (paid or free).
2. **Model-agnostic cost tracking** — Make the cost-calculation utility gracefully handle models not in OpenAI's pricing table.
3. **Preserve original pipeline fidelity** — No changes to the core planning/analysis/coding logic, prompts, or output structure.

## Non-goals

- Modifying the core Paper2Code pipeline logic (planning, analysis, code generation stages)
- Adding new features beyond OpenRouter/API compatibility
- Changing the evaluation pipeline (`eval.py`)
- Supporting models that are not OpenAI-API-compatible

## Scope

- **In scope**: configuration, client initialization, run scripts, cost tracking
- **Out of scope**: prompt engineering, agent logic, output format, evaluation
