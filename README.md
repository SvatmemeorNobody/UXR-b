# Hype-or-Truth: UXR-b Benchmark Suite

An un-cooked, absolute evaluation framework measuring raw visual layout replication, prompt specification compliance, and generation velocity.

## Repository Architecture

Download or reference these core configuration files to align your evaluation pipeline:
* `Rulebook.txt` — The strict baseline rules and disqualification parameters.
* `vllm_promptmaker.txt` — Translates core layout concepts into strict Detail Scale (D) values.
* `vllm_designmaker.txt` — System instructions forcing models to emit pure code output.
* `vllm_designjudge.txt` — The spatial layout evaluation engine prompt for the Judge AI.
* `run_benchmark.py` — The core execution script to automate inference and capture telemetry.

---

## Technical Specifications

The benchmark uses two evaluation models to establish a model's true performance curve:

1. **One-Config Test:** Isolates a single specific configuration tracking performance across the Prompt Detail Intensity ($D$ Scale) to find the exact boundary where a model's capability drops off.
2. **General Baseline Index:** An un-padded macro score showing the total average across all configuration parameters, styles, and community prompts.

---

## Quickstart Guide

### 1. Prerequisites
Install the official OpenAI/vLLM client framework to handle your local or remote api endpoints:
```bash
pip install openai
