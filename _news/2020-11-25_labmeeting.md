---
layout: post
title: Lab meeting - Kostuv Sinha
date: 2020-11-25
published: true
inline: false 
---

At this week's lab meeting, [**Koustuv Sinha**](/people/sinha.koustuv), will be presenting the paper [Measuring Systematic Generalization in Neural Proof Generation with Transformers](https://arxiv.org/abs/2009.14786) (to appear at NeurIPS 2020).

- **{{ page.date | date: '%A, %B %-d' }}**, **13:30–14:30** (Montréal time, UTC-4).
- Meetings are via Zoom. If you would like to attend the meeting but have not yet registered for this semester's MCQLL meetings, please do so at [this link](https://umontreal.zoom.us/meeting/register/tJElc--sqTgqGdawmDQZbO0Cvc7IOK5MLmae). If you have already registered, please join using the link you received in your confirmation email.

#### Abstract

<blockquote>
	We are interested in understanding how well Transformer language models (TLMs) can perform reasoning tasks when trained on knowledge encoded in the form of natural language. We investigate their systematic generalization abilities on a logical reasoning task in natural language, which involves reasoning over relationships between entities grounded in first-order logical proofs. Specifically, we perform soft theorem-proving by leveraging TLMs to generate natural language proofs. We test the generated proofs for logical consistency, along with the accuracy of the final inference. We observe length-generalization issues when evaluated on longer-than-trained sequences. However, we observe TLMs improve their generalization performance after being exposed to longer, exhaustive proofs. In addition, we discover that TLMs are able to generalize better using backward-chaining proofs compared to their forward-chaining counterparts, while they find it easier to generate forward chaining proofs. We observe that models that are not trained to generate proofs are better at generalizing to problems based on longer proofs. This suggests that Transformers have efficient internal reasoning strategies that are harder to interpret.These results highlight the systematic generalization behavior of TLMs in the context of logical reasoning, and we believe this work motivates deeper inspection of their underlying reasoning strategies.
</blockquote>

#### Bio

Koustuv Sinha is a third year PhD candidate at McGill University / Mila / Facebook AI Research, and is supervised by Joelle Pineau and Will Hamilton. His primary research interest lies in understanding systematic reasoning and generalization in discrete modalities, encompassing language understanding and graph-based reasoning.