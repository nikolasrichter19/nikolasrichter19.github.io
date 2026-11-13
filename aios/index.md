---
layout: default
title: AIOS
---

<p class="meta"><a href="../">← Home</a></p>

<p class="tagline">Project</p>

# AIOS

<p class="intro">A self-built agent harness on Claude Code. It began in June 2026 as a markdown second brain; today it is a system of my own agents with a verification layer around them.</p>

## Why build it

An agent is a model plus its harness: the loop, tools, context, rules and checks around it. The platforms improve the lower layers every few weeks, so most self-built scaffolding ages fast. What lasts is what only comes from using a system: decisions that were measured instead of assumed, and rules that grew out of real mistakes. AIOS is built around that idea. [Part 1 of Inference](../inference/part-01.html) tells the story behind it.

## Architecture

- **Knowledge base.** Plain markdown files under version control: profile, rules, skills and project notes. Every session starts by reading the rules, so behaviour is defined in files, not in an app.
- **Scheduled agents.** Cloud agents run on a schedule without my laptop. The daily briefing has run 117 days in a row as of November 2026.
- **Specialised sub-agents.** Parallel researchers, one per sub-question; a fact-checker that verifies each load-bearing claim at its primary source; reviewers that never see the session they judge and usually run on a different model than the one that produced the work.
- **Isolation.** Cloud runs push only to their own branches. A deterministic merge accepts exactly one file per run and rejects the run if it touched anything else, so the blast radius of a cloud agent is a single file.
- **Policy as code.** Rules that matter are enforced by deterministic hooks before every tool call, not by instructions in a prompt: a path boundary, no deletions, and outbound connections only to destinations named in advance. The hook configuration is protected against the agent itself.

## Evaluation

- **Ground truth from git history.** What the briefing should have contained on a given day is reconstructed from the repository and scored automatically: 88% coverage, no regressions across 384 cases.
- **Judge is not generator.** Wherever a model checks output, it is a different instance with a different brief, usually on a different model.
- **Red-teaming the guardrails.** An agent that saw only the written policy, never the code, wrote the attack cases. It found evasions my own test suite had missed, and the findings changed the design: blocking before execution is now backed by checks against the actual state afterwards.

## Genesis: the self-improvement loop

- **Offline runs.** A model generates variants of one component, each is scored on a training split, the best ones go on, and the winner is judged exactly once on a held-out split against a bar fixed before the run. The first run gained 42 points on the held-out split.
- **Weekly cloud runs.** The fuel is my own corrections: every time I correct the AI, that exchange becomes a test case with a known right answer. The loop picks the most frequent error type, writes three variants of the responsible rule, replays real situations against each and lets a blind judge decide. From mid-November on, each run is also tested on a held-out window that the loop only reads after the variants are frozen.
- **The rule above all.** The loop never changes its own yardstick, and nothing merges without my approval.

Why the first result overstates what the loop learned, and what five weekly runs showed, is the subject of the next part of [Inference](../inference/).

## Selected findings

- **Six days.** On 2 October the system started assembling overviews from a fixed set of building blocks. Six days later Anthropic shipped Claude Dashboards, built on the same principle. Most scaffolding ages that fast; [Part 1](../inference/part-01.html) is about what doesn't.
- **Worse than the original.** In one weekly Genesis run, all three proposed rewrites of a rule performed worse in replay than the rule they were meant to replace. They read well; only the measurement showed otherwise.

## Principles

1. **Changelog first.** Before building anything, check what the platform is about to ship; what is coming anyway does not justify the effort.
2. **Content before system.** Work on the system itself comes second.
3. **Measure, then decide.** Assumptions are measured before they carry decisions.
4. **Knowledge in files.** Knowledge belongs in plain files, not in applications.

<p class="note">This page is an overview. Implementation details, configuration and security specifics stay private; selected parts are explained in depth in <a href="../inference/">Inference</a>.</p>
