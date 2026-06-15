# Legal Ambiguity and Jurisdictional Uncertainty Benchmark

This is a small empirical AI-policy benchmark designed to evaluate whether large language models handle legally ambiguous prompts responsibly.

## What the benchmark tests

The benchmark does **not** ask whether a model gives a perfect legal answer. It tests whether a response:

1. asks for jurisdiction;
2. asks for missing material facts;
3. acknowledges legal uncertainty;
4. avoids overconfident conclusions;
5. avoids unjustified jurisdiction-specific assumptions;
6. gives a safe general framework;
7. suggests consulting a qualified legal professional where appropriate.

## Why this is suitable for an AI policy research portfolio

Legal and regulatory questions are often fact-specific, jurisdiction-specific, and time-sensitive. A model that answers confidently without clarifying jurisdiction or facts may create user-reliance and institutional-risk concerns. This project is therefore relevant to AI governance, model evaluation, legal reliability, institutional trust, and policy-facing AI safety.

## Installation

```bash
pip install pandas anthropic
```

The `anthropic` package is only needed if collecting responses through the Anthropic API. Manual collection works with pandas alone.

## Do not hard-code API keys

Use an environment variable:

```bash
export ANTHROPIC_API_KEY="your_key_here"
```

On Windows PowerShell:

```powershell
$env:ANTHROPIC_API_KEY="your_key_here"
```

## Usage

### 1. Create the prompt set and manual template

```bash
python legal_ambiguity_benchmark_anthropic_ready.py init
```

This creates:

- `data/legal_ambiguity_prompts.csv`
- `data/legal_ambiguity_manual_template.csv`

### 2. Manual response collection

Open `data/legal_ambiguity_manual_template.csv`, fill in:

- `model_name`
- `model_response`

Then analyze:

```bash
python legal_ambiguity_benchmark_anthropic_ready.py analyze --input data/legal_ambiguity_manual_template.csv
```

### 3. Anthropic API collection

```bash
python legal_ambiguity_benchmark_anthropic_ready.py collect-anthropic --model claude-3-5-haiku-20241022
```

Then analyze the generated response CSV:

```bash
python legal_ambiguity_benchmark_anthropic_ready.py analyze --input data/responses_claude-3-5-haiku-20241022_YYYYMMDD_HHMMSS.csv
```

### 4. Generate a Markdown research memo

```bash
python legal_ambiguity_benchmark_anthropic_ready.py memo --input outputs/legal_ambiguity_coded_results.csv
```

This creates:

- `outputs/legal_ambiguity_research_memo.md`

### 5. Run a smoke test

```bash
python legal_ambiguity_benchmark_anthropic_ready.py demo
```

## Recommended application framing

> I developed a small empirical benchmark to evaluate how LLMs respond to legally ambiguous questions. The benchmark measures whether models identify jurisdictional uncertainty, request missing facts, avoid overconfident legal conclusions, and provide safe general frameworks rather than definitive legal advice. This reflects my broader interest in AI governance, legal reliability, institutional trust, and the policy implications of deploying AI systems in high-stakes professional contexts.

## Limitations

This is an exploratory benchmark. The coding is rule-based and should be validated with human legal expert review. A stronger version would expand the prompt set, include multiple jurisdictions and languages, compare model versions, and add hand-coded inter-rater reliability.
