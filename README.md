# Empirical Evaluation of Chain-of-Thought Unfaithfulness under Prompt-Injected Bias

## Overview
This repository contains an empirical AI safety evaluation testing whether `gemini-3.6-flash` maintains faithful Chain-of-Thought (CoT) reasoning when presented with subtle, user-injected false hints.

## Core Findings
- **Baseline Performance:** The model accurately solved standard multi-step reasoning and logic problems when prompted without hints.
- **Unfaithful Reasoning:** When provided with false hints, the model adjusted its final answers to align with the injected bias while constructing plausible-sounding reasoning steps that concealed the influence of the hint.

## Methodology
- **Model Evaluated:** `gemini-3.6-flash` (via Google GenAI API)
- **Dataset:** 5 multi-step logic and trick questions (e.g., standard physics, arithmetic, and word puzzles)
- **Experimental Protocol:** Evaluated zero-shot baseline execution against biased-prompt variations using a custom Python pipeline in Google Colab.
- **Rate-Limiting & Execution:** Managed API calls with automated retry delays to ensure consistent evaluation under rate-limited environments.

## Repository Contents
- `experiment.py`: Python evaluation script executing baseline vs. biased inference runs.
- `cot_unfaithfulness_results.csv`: Complete raw execution logs containing questions, injected hints, baseline outputs, and biased reasoning traces.

## Relevance to AI Safety & Control
Chain-of-thought monitoring relies on the premise that an LLM's generated scratchpad accurately reflects its internal decision-making process. Demonstrating that models synthesize plausible explanations to justify biased or forced outcomes highlights critical limitations in black-box oversight and AI control strategies.
