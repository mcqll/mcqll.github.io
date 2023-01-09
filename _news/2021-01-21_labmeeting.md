---
layout: post
title: Lab meeting - Koustuv Sinha
date: 2021-01-21
published: true
inline: false 
---

At this week's lab meeting [**Koustuv Sinha**](/people/sinha.koustuv) will give
a talk on existing large language models and their need (or lack thereof) to
learn syntax given the current training and evaluation methodologies.

- **{{ page.date | date: '%A, %B %-d' }}**, **13:30–14:30** (Montréal time, UTC-5).
- Meetings are via Zoom. If you are interested in attending any of the meetings
  this semester, please take a moment now to register at [this
  link](https://umontreal.zoom.us/meeting/register/tJItdu6rrj4vH9JbKXKlNpMbPPm8IUJdWP7Q).
  After approval, you will receive a confirmation email with the link to join.

#### Abstract

<blockquote> Natural Language Understanding has witnessed a watershed moment
	with the introduction of large pre-trained Transformer networks. These
	models achieve state-of-the-art on various tasks, notably including Natural
	Language Inference (NLI). Many studies have shown that the large
	representation space imbibed by the models encodes some syntactic and
	semantic information. However, to really "know syntax", a model must
	recognize when its input violates syntactic rules and calculate inferences
	accordingly. In this work, we find that state-of-the-art NLI models, such as
	RoBERTa and BART are invariant to, and sometimes even perform better on,
	examples with randomly reordered words. With iterative search, we are able
	to construct randomized versions of NLI test sets, which contain permuted
	hypothesis-premise pairs with the same words as the original, yet are
	classified with perfect accuracy by large pre-trained models, as well as
	pre-Transformer state-of-the-art encoders. We find the issue to be language
	and model invariant, and hence investigate the root cause. To partially
	alleviate this effect, we propose a simple training methodology. Our
	findings call into question the idea that our natural language understanding
	models, and the tasks used for measuring their progress, genuinely require a
	human-like understanding of syntax.
</blockquote>

#### Bio

Koustuv is a third year PhD student at Mila, co-supervised with Joelle Pineau
and Will Hamilton. His primarily research direction involves understanding
systematic generalization in natural language and graph structured data.
[Personal website here](https://www.cs.mcgill.ca/~ksinha4/).
