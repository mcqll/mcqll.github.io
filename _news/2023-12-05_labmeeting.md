---
layout: post
title: Lab meeting - Austin Kraft and Amirhossein Kazemnejad
date: 2023-12-05
published: true
inline: false
---

At this week's MCQLL meeting, [**Austin Kraft**](https://austinwkraft.github.io/about/) will
be presenting **[[Small language] corpus] problems**, and [**Amirhossein Kazemnejad**](https://mila.quebec/en/person/amirhossein-kazemnejad/) will
be presenting **Enhancing Length Generalization in Transformers: The Role of Positional Encoding**.

_This is the last lab meeting of the Fall semester.  See you in Winter 2024!_

> __When:__ 
> : {{ page.date | date: '%A, %B %-d' }}, 15:00--16:00 (Montréal time, UTC-5)
>
> __Where:__  
> : MCQLL meetings this semester are in hybrid format.  We will meet in-person
> in room 117 of the McGill Linguistics Department, [1085
> Dr-Penfield](https://maps.mcgill.ca/?cmp=1&txt=EN&id=Penfield1085). If you'd
> like to attend virtually, the Zoom link is
> [here](https://mcgill.zoom.us/j/85321158610).


All are welcome to attend.

-  __Speaker:__
    : Austin Kraft

    __Title:__
    : [[Small language] corpus] problems

    __Abstract:__ 
    : > This presentation describes an in-progress collaboration to build a corpus of Semarangan Javanese (a.k.a. Peranakan Javanese; Cole et al. 2007) of Semarang, Central Java, Indonesia. In pursuing the empirical focus of the project—documenting anaphoric expressions like reflexive pronouns—the project has brought to the fore nontrivial design choices about how to represent a language that is underdocumented in corpora (Anand, Chung & Wagers 2020). As a case study from the Semarangan Javanese project, I discuss how existing part-of-speech tagsets might not neatly map to part-of-speech categories in the language, with consequences for how grammatical structure can be encoded in and retrieved from the corpus.
    >
    > I situate these challenges within an early-stage typology of "small language corpus problems”: conceptual and technological issues that are made acutely relevant when creating a corpus for a small language. I compare the design needs of corpora for small languages with those of small corpora for extensively documented languages, such as a corpus of English dedicated solely to a niche discourse type or subject matter (Koester 2022). Alongside the Semarangan Javanese project, my ongoing literature review aims to identify and categorize common challenges in corpus-building for small languages.


-  __Speaker:__
    : Amirhossein Kazemnejad

    __Title:__
    : Enhancing Length Generalization in Transformers: The Role of Positional Encoding

    __Abstract:__ 
    : > The advent of Long-Context Language Models (LLMs) has unlocked numerous advantages, including extended in-context learning, prolonged text generation capabilities, and an increased number of conversational turns. Such advancements have only recently become feasible, largely due to engineering breakthroughs like flash attention, which allow the processing of extensive sequences within memory constraints. Traditionally, Transformer models, however, have been limited in their ability to generalize beyond the context sizes encountered during training. In our NeurIPS 2023 paper, we delve into an empirical investigation of prevalent Positional Encodings to scrutinize their impact on length extrapolation. Furthermore, we propose and examine the possibility of removing positional encoding altogether from the standard decoder-only Transformer. This exploration encompasses both theoretical and practical analyses. Our findings not only provide critical insights but also lay the groundwork for the evolution of Transformer architectures in next-generation LLMs.