---
layout: post
title: Lab meeting - Ben LeBrun
date: 2021-11-09
published: true
inline: false
---

This week's lab meeting will feature a talk by [**Ben LeBrun**](/people/lebrun.benjamin).

- **{{ page.date | date: '%A, %B %-d' }}**, **15:00–16:00** (Montréal time, UTC-4).
- Meetings are via Zoom. If you would like to attend the talk but have not yet signed up for the MCQLL meetings this semester, please send an email to [mcqllmeetings@gmail.com](mailto:mcqllmeetings@gmail.com).

#### Abstract

> A heavy-tail of rare events accounts for a significant amount of the total probability mass of distributions in language (Baayen, 2001). Standard language modeling metrics such as perplexity quantify language model (LM) performance in aggregate. As a result, we have relatively little understanding of whether neural LMs accurately estimate the probability of sequences in this heavy-tail of rare events. In this talk, I will present a controlled evaluation scheme which uses generative models trained on natural data as artificial languages from which we can exactly compute sequence probabilities. Training LMs on generations from these artificial languages, we compare the sequence-level probability estimates given by LMs to the true probabilities in the target language. Our experiments reveal that LSTM and Transformer language models (i) systematically underestimate the probability of sequences drawn from the target language, and (ii) do so more severely for less-probable sequences. Investigating where this probability mass went, (iii) we find that LMs tend to overestimate the probability of ill formed (perturbed) sequences. In addition, we find that this underestimation behaviour (iv) is weakened, but not eliminated by greater amounts of training data, and (v) is exacerbated for target distributions with lower entropy.
