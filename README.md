# Secure Code Completion with Obfuscation

This project explores **privacy-preserving techniques for code completion** by analyzing how different levels of code obfuscation affect both **utility** (quality of generated completions) and **privacy** (similarity to the original code).

The core research question is:
> How does code obfuscation impact the usefulness of large language models while reducing information leakage?

---

## Project Overview

The project implements an end-to-end experimental pipeline that includes:

- **AST-based code obfuscation**
  - Variable renaming
  - Comment removal
  - Docstring removal
- **Code completion generation** using CodeT5 models
- **Evaluation of generated completions**
  - Utility score (ROUGE-1 F1)
  - Privacy score (normalized Levenshtein distance)
- **Visualization** of the utility–privacy trade-off
- **Lightweight CI** for notebook build validation

All experiments are executed via a **Jupyter notebook**.

---

## Obfuscation Levels

The following obfuscation levels are used:

- **Original** — original, unobfuscated prompt
- **Low** — variable renaming only
- **Medium** — variable renaming + removal of comments and docstrings

Each level is evaluated independently.

---

## Models

The project focuses on **CodeT5** models from Salesforce:

- `Salesforce/codet5-small`
- `Salesforce/codet5-base`
- `Salesforce/codet5p-220m-py` (optional, heavier model)

Models are loaded via the Hugging Face `transformers` library.

---

## Evaluation Metrics

### Utility Score
- **ROUGE-1 F1**
- Measures lexical overlap between the generated completion and the canonical solution
- Chosen for robustness to variable renaming

### Privacy Score
- **Normalized Levenshtein distance**
- Measures similarity between original and obfuscated prompts
- Higher score indicates stronger obfuscation

---

## Dataset

- Dataset: HumanEval (OpenAI) — https://github.com/openai/human-eval
- Used to evaluate functional correctness and completion quality

---

## Installation

Create a virtual environment and install dependencies:

```bash
pip install -r requirements.txt
```

## Running the Project

Start Jupyter and open the notebook located in the project root:

```bash
jupyter notebook secure-code-completion.ipynb
```