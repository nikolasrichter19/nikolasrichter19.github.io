---
layout: default
title: "The Easiest Case"
---

[← Inference](./)

<small>INFERENCE · INTERLUDE 1</small>

# The Easiest Case

### What the Riemann Proof Says About Superintelligence, and What It Does Not

*Nikolas Richter · Published 24 November 2026*

## Preliminary note

“Inference” is a series of essays on where artificial intelligence is heading and what that means for work and learning. This interlude interrupts the series because a proof of the Riemann Hypothesis announced on 20 November bears on the series’ guiding question. My own system, the subject of [Part 1](part-01.html), is an AI operating system made of text files in which the agent Claude Code works with me. The Riemann Hypothesis is a statement about the zeros of the Riemann zeta function, which governs how the prime numbers are distributed among the natural numbers. Bernhard Riemann formulated it in 1859. The Clay Mathematics Institute counts it among the seven Millennium Prize Problems and offers a prize of one million dollars for the solution of each [1]. Lean is a programming language in which mathematical proofs can be written down so that a computer checks every step. Numbers in square brackets refer to the sources listed at the end.

## Introduction

On 20 November the mathematician Levent Alpöge, who works for the AI company Anthropic, wrote that he believed he and the company’s model Claude had found a proof of the Riemann Hypothesis [2]. Two days later Alexandr Wang, Meta’s chief AI officer, published an essay titled “Superintelligence is Arriving” [3]. His conclusion is that once a model solves the hardest problem in mathematics, intelligence is no longer the bottleneck. What models still lack in order to far surpass the best humans in nearly every field is what he calls “domain-specific know-how, plumbing, and experimentation”. He considers AI research much less intellectually demanding than the Riemann Hypothesis, which is why, he argues, models will soon become superhuman at improving themselves.

On the substance, I largely agree with Wang. He recalls December 2024, when models began to ace the AIME, a mathematics competition for teenagers [3]; not quite two years later comes the claim of a proof of the Riemann Hypothesis. Anyone who has followed that stretch can hardly dismiss the claim as an outlier, and I consider it likely that raw intelligence is no longer the bottleneck in mathematics. His essay, however, leaves open a question that I consider as important as the one about intelligence itself. How would we recognise a superintelligence in a field that has no checker like Lean?

My thesis is that the Riemann case is so convincing precisely because mathematics is one of the few fields in which a machine can confirm a result before a human understands it. In almost every other field, reality does the checking, and it answers slowly. There it will be considerably harder to establish that a system is superintelligent, even if such a system already exists, because its results, too, must be checked before anyone can trust them. Human work is therefore shifting towards checking and evaluation.

I first describe what is known about the proof, then why mathematics is the easiest case, and finally why superintelligence is much harder to recognise outside mathematics. After that I draw a consequence for my own system. An objection and my reply are followed by a conclusion.

## 1. A proof no human can fully read

Alpöge’s note runs to four pages. He writes that the method extends further and also settles the generalised version of the hypothesis, and that he and Claude have formalised the arguments without assumptions [2]. He has published only the Lean code. A detailed version in ordinary language, which he says he had generated for his own amusement, runs to more than 250,000 pages; he calls such a document unreadable [2]. He concedes that he is presenting the world with a complete argument before he has mastered the surrounding mathematics himself. For the parts in which Claude is the expert and he is not, he says he is paraphrasing a summary that might make no sense; the Lean code, he writes, should suffice to clarify everything [2].

This does not yet confirm the proof. The Clay Mathematics Institute does not list the problem among the solved ones [1]. According to Nature, the Fields medallist James Maynard suspects that the proof will turn out to be correct and expects that it would then surely count among the absolute pinnacles of mathematical results, provided it is also understood [4]. The number theorist Andrew Granville, by contrast, calls the note garbled and attributes its timing to the fall in the share price of Anthropic, which had gone public a few days earlier [4]. Alpöge rejects this reading in the note itself [2]. Also on 20 November, the Stanford mathematician Ravi Vakil made public a rival, entirely human-written proof by Alessandro Maria Masullo [4].

Whether the proof is correct can be established by a program, once humans have made sure that the statement in Lean really expresses the hypothesis and nothing weaker. No one, its discoverer included, has yet set out why it is correct. Checking and understanding come apart here, and only checking can be handed to a machine; the understanding on which Maynard makes his judgement conditional, and which Alpöge intends to supply in a proper write-up, remains work for humans [2, 4].

## 2. Why mathematics is the easiest case

A precursor shows how a loop of generating and checking works in mathematics. In August Anthropic reported that an unreleased research model had failed to prove the hypothesis but had improved a long-standing bound along the way. The proportion of zeros known to lie on the critical line rose from 41.6 to 67.2 percent [5]. Around 60 sub-agents ran thousands of numerical checks against known zeros and refereed one another’s work, and the result was a formal proof in Lean that the standard checking tool accepts [5]. In mathematics a model can discard a great many ideas in a short time, because every idea receives an answer at once.

That immediate answer is the exception. Elsewhere in his essay, Wang himself names what other fields additionally require, namely “experimentation, data, and feedback loops” [3]. I would give this list more weight than he does, because it describes the checker that mathematics comes with for free and that other fields must first build at great cost. In medicine this checker is the clinical trial, and years often lie between a plausible hypothesis and its confirmation in patients. On the stock market, the market does the checking, and it gives each answer only once, under conditions that do not repeat. A personal decision is judged by the life that follows it. In all these cases a model can generate hypotheses at machine speed, but they are confirmed at the speed of reality.

The same applies to AI research. Whether a model has improved after a change shows up in training runs, which are expensive, and in tests, which only approximate what they are meant to measure. I have observed this in my own, much smaller system when it was supposed to improve its own rules. Generating variants took minutes; fresh cases on which they could be measured honestly accumulated only over weeks.

The progress of a field therefore depends not only on how clever the model is but also on how quickly and how strictly the field can check results. Mathematics checks immediately and exactly, and that is why it is the first place where we see what models can do.

## 3. How we would recognise superintelligence

Calling a system superintelligent means claiming that its results are better than those of the best humans. Someone has to verify that claim. In mathematics a program does it: a proof that Lean accepts is correct whether or not a human understands it, provided the statement in Lean captures the hypothesis. That is why a mathematician like Alpöge can trust a result whose details, by his own account, he has not mastered.

Other fields lack this route. Suppose a model proposes a cancer therapy that works better than anything doctors prescribe today. At the moment it is proposed, it cannot be told apart from a proposal that merely sounds convincing. Only a clinical trial can show that, and a trial needs patients, time and a comparison. Until then, the model’s superiority is a hypothesis like any other. The stock market is similar. If a model beats the market for a year, that may be skill or luck, and the two can be told apart only over many years and many decisions.

A further difficulty grows with the models’ ability. The further a system surpasses humans, the less they can judge its answers by understanding them. An error that no one notices then looks exactly like a correct answer that no one can follow. The usual tests help only so far, because whoever writes a test must know the right answers. For questions to which no human yet knows the answer, there is no answer key, except where the result, like a proof or a program, can be checked by machine. Wang speaks of a superintelligence that is a thousand times smarter and more capable than humans in every field [3]. How such a factor of a thousand would be measured, he does not say, and outside mathematics I would not know how either.

Superintelligence could therefore not be announced on a single day in these fields. The evidence for it builds up result by result, at the speed at which reality answers. Even if it existed, checking would still be necessary, because anyone who entrusts it with a decision about a treatment, an investment or a rule must first know how good its past judgements were, and only someone who has checked them knows that.

## 4. What I conclude for my own system

If checking is the scarce part, I should practise it where I am the expert myself, that is, in my own decisions. On 23 November I counted. Since July I have recorded eleven decisions in my system, ten of them with a section listing their assumptions and four with a date on which I intend to review them. Only two assumptions name a threshold at which they can fail, and both concern the system itself, such as an improvement of at least ten points in a fixed test. Not a single assumption states a probability. “I will use the touchscreen in everyday life” can be neither confirmed nor refuted as long as it remains open what “use” means and by when. The only assumptions that could be refuted, then, were the two that a program could have checked as well.

The next component follows from this. From now on, every assumption is to become a forecast at the moment of deciding, with a deadline, a probability and a criterion by which it counts as failed, recorded twice, with my probability and with the agent’s. On the due date, a checker that has not seen the original conversation will deliver the verdict. Across many cases this will yield a measure of how well calibrated my probabilities are; meteorology scores forecasts of this kind with the Brier score, which Glenn Brier proposed in 1950 [6]. As a by-product, the same measure will show whether the agent judges better than I do; in miniature, that is the question of section 3.

## 5. Objection and reply

One might object that slow feedback is merely a transition. Models could soon plan experiments themselves, in simulations or automated laboratories, and the loops of the other fields would then speed up just as those of mathematics have. For some fields this is true, and here Wang is probably right. Wherever an experiment can be automated, the gap will narrow. A simulation, however, is itself only an approximation of reality and no better than its calibration against it, and some answers cannot be accelerated. Whether a treatment improves five-year survival becomes clear after five years, and whether a decision was right only in its consequences. The gap therefore shrinks without disappearing.

On one point I agree with Wang without reservation. He warns against a “handover” of society to AI and calls it lazy thinking to treat superintelligence as inevitable and to ask only how to build it safely [3]. Control over a system whose results one can no longer read begins with the ability to check those results. Anyone who wants humans to gain rather than lose agency in this process must take checking and evaluation more seriously than before.

## 6. Conclusion

If the proof holds, a machine has found it in one of the few fields in which a machine can also check the result. Wang may be right that intelligence will soon be the bottleneck in hardly any field. In the other fields, however, it will be considerably harder to verify that a system is superintelligent than to build it, because each of its answers must first hold up against reality. I therefore consider it likely that human work is shifting towards checking and evaluation; whether that will mainly mean building new checking tools or exercising judgement itself cannot be said today. Part 1 of this series conjectured a shift from building to checking. The Riemann case shows this shift where it reaches furthest, because in mathematics the checking of the proof has largely been handed to the machine, and understanding is what remains for humans.

This text has limits. The proof has not yet been confirmed, and my own figures come from a single system. The argument, however, does not depend on the proof, because the result from August already shows how quickly a loop advances when its checker answers at once, and how little that says about fields in which it does not.

## References

1. Clay Mathematics Institute: Riemann Hypothesis, Millennium Prize Problems, accessed 23 November 2026. [claymath.org](https://www.claymath.org/millennium/riemann-hypothesis/)

2. Alpöge, L.: untitled note on a proof of the Riemann Hypothesis, four pages, 20 November 2026. [alpo.ge](https://alpo.ge/remark.pdf)

3. Wang, A.: Superintelligence is Arriving, article on X, 22 November 2026. [x.com](https://x.com/alexandr_wang/status/2124636606959345776)

4. Castelvecchi, D.: Mathematicians astounded by AI and human-written proofs of iconic Riemann hypothesis, Nature, 20 November 2026, updated 23 November 2026. [nature.com](https://www.nature.com/articles/d41586-026-03812-7)

5. Anthropic: Riemann zeta, research post, 10 August 2026, updated 13 August 2026. [anthropic.com](https://www.anthropic.com/research/riemann-zeta)

6. Brier, G. W.: Verification of forecasts expressed in terms of probability, Monthly Weather Review 78 (1), 1950, pp. 1–3. [doi.org](https://doi.org/10.1175/1520-0493%281950%29078%3C0001:VOFEIT%3E2.0.CO;2)

All other figures come from the author’s own measurements within his system, as of 23 November 2026.

---

[← All parts](./)
