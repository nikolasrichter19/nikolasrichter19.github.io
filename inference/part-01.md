---
layout: default
title: "A Six-Day Lead"
---

[← Inference](./)

<small>INFERENCE · PART 1</small>

# A Six-Day Lead

### Four Months with a Self-Built AI Operating System

*Nikolas Richter · Published 13 November 2026 · Figures as of October 2026*

## Preliminary note

“Inference” is a series of essays on where artificial intelligence is heading and what that means for work and learning. The parts alternate between reports from my own practice and applications in finance and medicine, and each stands on its own. The name can be read in two ways: in AI, inference is the moment a trained model produces an answer; in everyday usage, it is the conclusion one draws from evidence.

Many people know AI as a chat window in which ChatGPT or Claude answers a question. Since 2025, such language models have increasingly been working as so-called agents. They read and write files on one’s own computer, run commands and carry out multi-step tasks largely on their own. Claude Code, a tool made by the AI company Anthropic, is one such agent, and it is the tool this essay is about.

Out of the box, an agent of this kind knows little about the person it works for or how that person works. Many users therefore keep a folder of plain text files in Markdown format that records who they are, which rules the agent should follow and how recurring tasks are done; the agent reads it at the start of every session. In videos and forums this goes by names such as “second brain” or “agentic OS”; here it is called an AI operating system. I began building one in June 2026, and this essay takes stock after four months.

The providers, however, develop their products quickly, and some of what individuals build for themselves soon appears as a finished feature. This essay asks which part of one’s own work survives that.

A few technical terms recur throughout. The platform is the provider’s offering, here Claude Code and Anthropic’s other products. The harness, or scaffolding, is everything built around the model so that it can work, from tools and rules to the interface. The context window is the amount of text a model takes into account at once when it answers; it is measured in tokens, short fragments of words. A skill is a stored set of instructions that the agent calls up when needed, and a sub-agent is a helper to which it hands a narrowly defined subtask. Finally, an embedding search finds texts by similarity of meaning rather than by matching words. Numbers in square brackets refer to the sources listed at the end.

## Introduction

This essay argues that the lasting value of a self-built AI system lies in what only arises from using it: decisions that were measured rather than assumed, and rules that grow out of one’s own mistakes. Its technical architecture, by contrast, is reproduced by the platforms themselves at ever shorter intervals.

My own system first shows the uncomfortable side of this thesis. After four months it contains a good 390,000 words about itself, meaning rules, test protocols and build plans, but only 177,000 about my university studies, which it was supposed to serve. On 28 September I decided that every new component would be used for a week before I built anything further; the next day I produced twenty versions. On 2 October I had Claude assemble overviews from a fixed set of building blocks for the first time, what I call the situation view, and six days later Anthropic introduced Claude Dashboards, a feature that applies the same principle to data platforms [1].

Behind this sequence lies a pattern that research has now begun to describe as well. A source-code study by Paul Barbaste and colleagues, submitted in July 2026, frames the subject as follows: an agent consists of the model and the harness, that is, everything that connects the model to the world through its loop, tools, context, safety measures and orchestration; the study compares eleven such harnesses at the level of their source code [2]. Much of this scaffolding is provisional, because whatever compensates for a weakness of the model or tool today will tomorrow be taken over by the model itself or by the platform it runs on. The pattern collection agentpatterns.ai therefore recommends, under the label “harness impermanence”, building scaffolding from the outset so that it can be removed with little effort [3]. The idea goes back to Richard Sutton’s 2019 essay “The Bitter Lesson”, which holds that general methods that scale with computation eventually prevail over built-in expert knowledge [4]; what is new is how short the half-life has become. In my case it was six days.

Against this background, I examine what endures in such a system once one subtracts what the platform provides anyway. I develop my answer in three steps. First, I describe how quickly the scaffolding ages. Second, I show that work on context, and its verification through measurement, cannot be outsourced. Third, I explain why rules that arise from one’s own mistakes form the most durable return. A natural objection and my reply are followed by the consequences I draw and a conclusion.

## 1. The scaffolding and its half-life

Since mid-June I have been working with Claude Code on a folder of Markdown files that I also read and edit in the note-taking app Obsidian. The roles became clear only over time. The folder is the actual system, since memory, rules, 40 skills and twelve specialised sub-agents all live there as plain files. Claude Code is the worker that reads, writes and carries out tasks within it, while a self-built web interface serves merely as a window onto this collection. An early rule followed from this: the interface holds no knowledge of its own, and everything that matters lives as a file in the folder.

It was in this interface that the half-life of scaffolding showed most clearly. Between 28 September and 2 October I shipped 57 versions, among them a lock screen, a calendar into which appointments could be entered directly, an overview page for the agents, and a voice assistant that answered fixed phrases after about 0.6 seconds instead of a little over two. At the end of that week stood the situation view. I type a sentence, Claude returns a construction plan made of fixed building blocks such as a metric, a table or a timeline, and a server checks this plan strictly against a schema before anything is displayed; the model could not ship free-form code. Claude Dashboards, introduced six days later, answers questions in natural language with a dashboard that updates as the underlying data changes [1]. It is designed for data platforms such as BigQuery or Snowflake rather than for a folder of notes, yet it applies the same principle as my situation view.

The same was true of a page on which I could answer waiting Claude sessions without switching to their terminal. Anthropic had already released an overview in May in which waiting sessions can be answered directly [5]; in other words, I rebuilt something that already existed. Other things I left alone in time. Claude Code ships parallel sessions in separate working copies on its own, and a tool built specifically for that purpose has since been discontinued [6]. Since August, running sessions can also message one another, and the desktop app resumes sessions started in the terminal with their full history [7]. Custom solutions in these areas would have become obsolete within weeks.

Comparison with other projects also shows how interchangeable the scaffolding is. Research I conducted at the end of September concluded that almost everyone is building the same cockpit: one screen for all agents, a token-usage meter, skills as buttons and a notes folder as memory. From version 8.8 onwards my interface followed exactly this picture, based on a template I had picked out for the purpose, and I built the agents page explicitly on the model of two YouTube channels. In early September the two directories of Claude Code plugins listed more than 2,500 entries between them, at least twenty of which correspond to my system at its core. Of the eighteen recommendations in the study mentioned above [2], my system meets thirteen, although some only because Claude Code already provides them.

## 2. What cannot be outsourced: context and measurement

No platform can decide which information belongs in the model’s context window at which moment. Anthropic describes this work as context engineering and offers as its guiding principle finding the smallest possible set of high-signal tokens that maximises the likelihood of the desired outcome [8]. Which tokens those are, however, depends on what is in one’s own folder and how one works with it; to that extent this work can be neither bought nor delegated. In my system it consisted above all of replacing assumptions with measurements. Three cases show this, two about context and one about security.

First, I had assumed that the many skills made up the largest share of the context every session loads before the first question is asked. According to an estimate based on file sizes in early September, however, roughly 92 percent went to the mandatory reading of rules and profile, and less than a tenth to the skills. The real measurement two weeks later was even clearer. An empty session alone came to about 17,200 tokens, and after the mandatory reading the total was about 73,300; the estimate had understated the mandatory reading by almost half, because the files are read in with line numbers. The lever therefore lies in the length of the rules rather than their number.

Second, I had developed a mechanism that retrieves the relevant rules for each request via embedding search and injects them. Even when Claude Opus, then Anthropic’s most capable model, rephrased every request beforehand, the method found commands in 86 percent of cases, but rules about behaviour and consequences in only 14 percent. Someone asking to merge two working copies talks about merging, not about what may then be sent to the server; yet the rule about that is precisely the one needed at that moment. Similarity of meaning finds the command, not its consequences. On 28 September I switched the mechanism off. Fittingly, if for code rather than rules, the study mentioned above notes that none of the eleven systems it examined retrieves code via embeddings [2].

Third, on 14 September I tested whether my safeguards would notice a command sending data to an external server. Neither a simple upload command nor a short Python call was detected, even though Python was on the list of commands allowed to run without confirmation. Since the following day, a dedicated block stops such commands unless the destination has been explicitly named.

## 3. Rules from mistakes

What lasts longest are rules that grew out of mistakes. Each of them is recorded in my system together with its occasion, so that it remains clear later why it exists.

In mid-September my agent inferred from the documentation which line had to appear in a configuration file and announced in the same breath how I would recognise success; it had never actually read the field in question. Since then the principle applies that reading documentation is no substitute for checking the mechanism. At the end of September it recommended that I download a local language model without checking whether its verbose reasoning could be switched off, which my use required, and the download turned out to be in vain. Since then the agent checks every instruction and every recommendation itself before it asks me to act. It could have caught both mistakes on its own; I noticed them only once they had cost me time.

A third rule concerns measurements. An evaluation had discarded seven variants of a calculation model, and only afterwards did it emerge that the same upper bound had been active in every one of them, as if seven engines had been compared under the same speed limit. The measurement therefore only answered whether a variant helps under this hidden constraint. Since then every measurement I cite comes with the question of whether what was being tested could have had any effect at all.

A platform could supply the wording of such rules, and some already sit in other people’s plugins. Which of them one’s own system needs, and where, only one’s own mistakes reveal. The attitude behind all three is captured in a sentence from the openly licensed plugin loop-and-gate-foundation by Shane Logsdon [9], which I adopted: “A checker that read the worker’s session isn’t checking, it’s agreeing.”

## 4. Objection and reply

One might object that such a system is primarily a learning project and therefore need not be judged by its immediate usefulness. The objection is partly right. I build the system in part to understand the technology behind it, and some of it I deliberately made larger than its use required. Scaffolding also buys time as long as models and platforms do not yet offer a capability, and whoever has built it understands the platform’s later features better than someone who merely uses them.

The objection holds, however, only as long as what is built solves a problem I have or teaches me something I cannot yet do, and in many places neither was true any longer. An audit on 4 September found that the checking script detected not a single error in 22 categories, because there was nothing in the collection to find. The inbox through which I had meant to capture thoughts on the go had lain idle for a month, and of the seventeen notes that had ever passed through it, around ten were tests. I had built tools against problems I did not have. For twenty versions in a single day, the learning argument is not enough.

## 5. Consequences

The rule of 28 September was right; I broke it because every new version is visible immediately, while the value of a week only shows after a week. Building rewards immediately; using rewards only with a delay. Four principles follow from this account, and I would set them from the start today. Before building anything, look at the platform’s changelogs, because what is foreseeably coming does not justify one’s own effort. Content takes precedence over work on the system itself, and a tool against a problem that does not yet exist waits until it does. Assumptions are measured before they carry decisions; each of the three cases above would have been decided wrongly without measurement. Finally, knowledge belongs in files, not in applications: because my interface never held knowledge of its own, it can be abandoned without loss as soon as the platform offers the same.

Little is needed to begin: a folder of Markdown files, a short rules file that Claude reads at every start, and a single routine that delivers concrete value every day. Everything else should be built only when a concrete problem calls for it.

## 6. Conclusion

The starting question was what endures in a self-built AI system once one subtracts what the platform provides anyway. The platform either already offered the visible building blocks, such as the situation view or the page for waiting sessions, or released a feature within weeks that covered their core; my lead on the situation view lasted six days. What remained is what arises from use: decisions that would have come out wrong without measurement, and rules that grew out of concrete errors. Both depend on one’s own material and one’s own mistakes.

Beyond my own system, this points to a shift that I record for now as a conjecture. The more scaffolding the platforms take over, the more alike individual systems become, and the more their return depends on which assumptions their users measure and which mistakes they turn into rules. For the guiding question of this series, where AI is heading and what that means for work and learning, this would mean that the value of one’s own work is shifting from building to checking.

This account has limits. It rests on a single system, built and used by one person over four months, and most of its figures come from my own measurements. It describes what happened in this case, not what holds in general; whether the pattern recurs in other tasks cannot be read from a single case.

The next part of this series turns to an AI system that is supposed to improve itself, and to the question of how to tell whether it actually got better.

## References

1. Anthropic: announcement of Claude Dashboards and Claude Motion, 8 October 2026. [claude.com](https://claude.com/resources/articles/dashboards-and-motion)

2. Barbaste, P., Darrigol, T., Vu, G. and Wiltberger, T.: source-code study of eleven agent harnesses, submitted 15 July 2026. [arXiv:2609.00006](https://arxiv.org/abs/2609.00006)

3. agentpatterns.ai: Harness Impermanence. Build Scaffolding To Be Deleted, as of 9 September 2026. [agentpatterns.ai](https://agentpatterns.ai/patterns/agent-design/harness-impermanence/)

4. Sutton, R.: The Bitter Lesson, 13 March 2019. [incompleteideas.net](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)

5. Anthropic: Agent view in Claude Code, 11 May 2026. [claude.com](https://claude.com/blog/agent-view-in-claude-code)

6. stravu: Crystal, GitHub repository, deprecated since February 2026. [github.com](https://github.com/stravu/crystal)

7. Anthropic: What's new in Claude Code, weeks 32 and 35, August 2026. [code.claude.com](https://code.claude.com/docs/en/whats-new)

8. Anthropic: Effective context engineering for AI agents, 29 September 2025. [anthropic.com](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

9. Logsdon, S.: loop-and-gate-foundation, Claude Code plugin, MIT licence. [github.com](https://github.com/slogsdon/loop-and-gate-foundation)

All other figures come from the author's own measurements and analyses within his system, as of October 2026.

---

[← All parts](./)
