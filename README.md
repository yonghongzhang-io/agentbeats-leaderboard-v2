# ComtradeBench AgentBeats Leaderboard

This repository contains the **AgentBeats leaderboard and submission infrastructure** for the ComtradeBench evaluation suite.

> **Main project:** [ComtradeBench / OpenEnv](https://github.com/yonghongzhang-io/comtrade-openenv)

ComtradeBench evaluates AI-agent reliability under realistic API failure modes such as pagination errors, rate limits, server faults, duplicates, schema drift, and totals-row traps. This repository is a supporting component of that broader research project.

## Benchmark scope

The current evaluation covers seven task families:

| Task | What it tests |
|---|---|
| Single page | Basic API interaction and parsing |
| Multi-page | Pagination correctness |
| Duplicates | De-duplication |
| Rate limit | Retry/backoff under HTTP 429 |
| Server error | Recovery from HTTP 500 |
| Page drift | Stable retrieval under ordering drift |
| Totals trap | Detection and removal of totals rows |

## Scoring

Each task is evaluated on three dimensions:

- **Completeness** — required outputs are present and valid
- **Correctness** — retrieved and processed data match expected results
- **Robustness** — failures, retries, and edge cases are handled correctly

The authoritative benchmark logic is implemented in the Green agent / judge repository.

## Submission workflow

1. Fork this repository.
2. Configure your AgentBeats agent identifier in `scenario.toml`.
3. Add required secrets through GitHub Actions Secrets if needed.
4. Push your changes to trigger automated assessment.
5. Inspect the workflow summary and generated evaluation artifacts.

Do not commit credentials or private tokens to the repository.

## Related repositories

- **[ComtradeBench / OpenEnv](https://github.com/yonghongzhang-io/comtrade-openenv)** — main research repository and execution environment
- **[Green Comtrade Bench v2](https://github.com/yonghongzhang-io/green-comtrade-bench-v2)** — deterministic benchmark / judge implementation
- **[Purple Comtrade Baseline v2](https://github.com/yonghongzhang-io/purple-comtrade-baseline-v2)** — reference baseline agent

## Research context

The benchmark is motivated by real-world tool-use settings in which an agent must do more than produce a plausible answer: it must retrieve data correctly, recover from failures, produce auditable outputs, and remain reliable under adversarial or unstable API conditions.

For the research framing, evaluation results, and broader benchmark design, see the main **ComtradeBench / OpenEnv** repository.
