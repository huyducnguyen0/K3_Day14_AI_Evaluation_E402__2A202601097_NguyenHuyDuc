# Complete AI Evaluation Lab Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Complete every required code, dataset, benchmark, and written deliverable for the AI evaluation lab.

**Architecture:** Keep `template.py` as the reusable core, `domain_assistant.py` as the RAG system under evaluation, and `evaluate_answers.py` as artifact I/O. Author evidence-backed dataset records before generating and evaluating real answers.

**Tech Stack:** Python 3.11, pytest, OpenAI Python SDK, python-dotenv, JSON, Markdown.

## Global Constraints

- Do not expose or commit `.env` or an API key.
- Preserve the provided public APIs in `template.py` and artifact schemas.
- Use exact excerpts from `data/student_services` as golden evidence.
- Do not count retrieval metrics in `EvalResult.overall_score()`.

---

### Task 1: Complete and verify the evaluation core

**Files:**
- Modify: `template.py`
- Test: `tests/test_solution.py`
- Create: `solution/solution.py`

- [ ] Run `pytest tests/ -q` to confirm the provided suite fails against the starter TODOs.
- [ ] Implement the dataclasses, answer/retrieval metrics, LLM judge, benchmark runner, regression analysis, and failure analysis API as described by each method's docstring.
- [ ] Run `pytest tests/ -q` until all 42 tests pass.
- [ ] Copy the verified core to `solution/solution.py`.

### Task 2: Build and validate the golden dataset

**Files:**
- Modify: `golden_dataset.json`
- Read: `data/student_services/*.md`

- [ ] Extract policy facts and literal evidence from every corpus document.
- [ ] Replace all placeholder records with 5 easy, 7 medium, 5 hard, and 3 adversarial cases.
- [ ] Run `python validate_golden_dataset.py` and fix every reported schema, provenance, coverage, or distribution violation.

### Task 3: Generate and evaluate a real benchmark

**Files:**
- Create: `artifacts/actual_answers.json`
- Create: `artifacts/benchmark_results.json`

- [ ] Confirm `OPENAI_API_KEY` is configured without printing it.
- [ ] Run `python domain_assistant.py` to generate saved RAG answers.
- [ ] Run `python evaluate_answers.py` to create the benchmark artifact.
- [ ] Inspect both JSON artifacts for the expected number of records and no errors.

### Task 4: Finish the written submission

**Files:**
- Modify: `exercises.md`
- Modify: `reflection.md`

- [ ] Fill the warm-up and rubric sections with concise, domain-specific answers.
- [ ] Transfer actual benchmark metrics and the three lowest-scoring cases into Exercise 3.2.
- [ ] Complete failure clustering, 5 Whys, improvement log, and regression strategy from benchmark evidence.
- [ ] Run the final test and validator commands and report their output.
