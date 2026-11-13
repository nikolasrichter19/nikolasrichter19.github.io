---
layout: default
title: Nikolas Richter
---

<p class="tagline">Finance · AI · Medicine</p>

<p class="intro">I work at the intersection of finance, AI and medicine: business studies in progress, three years of medical school behind me, and an agent system I designed, built and run every day.</p>

## Projects

### AIOS

<p class="meta">Self-built agent harness on Claude Code · since June 2026</p>

A system of my own agents with a verification layer around them: scheduled cloud agents, sub-agents that check each other's work, and a self-improvement loop that has to beat a held-out test before anything changes.

<details markdown="1">
<summary>Architecture and results</summary>

- **Agents.** Scheduled cloud agents, among them a daily briefing with 117 consecutive runs as of November 2026, plus specialised sub-agents: parallel researchers, a fact-checker that verifies every load-bearing claim at its primary source, and reviewers that never see the session they judge, running on a different model than the one that produced the work.
- **Harness.** Cloud runs push only to isolated branches; a deterministic merge accepts exactly one file per run and rejects anything else. Policy lives in deterministic pre-tool-call hooks rather than in prompts, and the hook configuration protects itself from the agent.
- **Evals.** Daily output is scored against ground truth reconstructed from git history: 88% coverage, no regressions across 384 cases. The guardrails were red-teamed by an agent that saw only the written policy, never the code.
- **Genesis.** A self-improvement loop: variants are generated, scored on a training split and judged exactly once on a held-out split against a bar fixed in advance. The weekly cloud version learns from my own corrections, replays them against each variant and lets a blind judge decide. Nothing merges without my approval. First run: +42 points on the held-out split; why that number overstates what the loop learned is the subject of the next essay.

</details>

## Thoughts

### [Inference](inference/)

<p class="meta">Essay series · since November 2026</p>

Where AI is heading and what that means for work and learning, argued from my own measurements rather than from announcements. The parts alternate between reports from practice and applications in finance and medicine.

1. [A Six-Day Lead: Four Months with a Self-Built AI Operating System](inference/part-01.html) · 13 November 2026
