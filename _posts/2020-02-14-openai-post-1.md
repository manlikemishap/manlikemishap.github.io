---
title: 'Getting Started @OpenAI'
date: 2020-02-14
permalink: /posts/2020/02/openai-post-1/
tags:
  - openai
---

Hey everyone, I'm Pamela Mishkin (an anagram of Manlike Mishap)!

I've spent the last few years working between the public and private sectors trying to understand how we can offer citizens and consumers better services with new technology. I’ll spend the next four months at OpenAI reflecting on potential pitfalls and hazards of these systems. In particular, I will focus on learning how safe language models are defined and built.

At a technical level, I'm interested in how models make decisions and how we interpret these decisions. I’m also interested in how we make building, employing, and interacting with models accessible to the wider population. At a policy and organizational level, I'm interested in how OpenAI frames "safety" as an opportunity for more interesting and exciting research. I’ve seen companies where policy and engineering have an antagonistic relationship, framed as regulation keeping us from doing the most interesting or groundbreaking work. I prefer to take the approach that policy introduces interesting constraints to engineering problems. This approach suggests a framework where standards, norms, and models can develop symbiotically rather than in response to each other.

I’ll post to this blog every two weeks about what I’m learning. I spent the first two weeks reading the literature on a broad array of topics related to language models. I’m hoping to spend the next two weeks implementing some of the things I’ve learned about this week. From there, I’ll move into metrics for understanding disinformation/misinformation and fairness/bias. I’m not sure what’s after that, but worst comes to worst, am sure GPT-2 can fill in something for me.

As this is just an introduction post, I’ll provide a general outline of some of what I’ve thought about this week. This post is hopefully more speculative and less technical than future ones will be, so stick with us, please.


Attention and visualization
----
In order to build a system you have to understand it. I’m starting this program with little to no understanding of deep learning for natural language processing. A lot of the sub-topics I’m interested in center around asking “why is this model making this decision” and then, given that, “how do we change this decision.” Attention architectures -- I’m told -- are the state-of-the-art right now in NLP, but there’s a lot of work to be done in understanding what they’re doing under the hood. These papers were suggested to me by my mentor [Alec](https://twitter.com/alecrad?lang=en) as an introduction to visualization and understanding of self-attention architectures.

-   [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473)
-   [What Does BERT Look At? An Analysis of BERT's Attention](https://arxiv.org/abs/1906.04341)
-   [Visualizing and Measuring the Geometry of BERT](https://arxiv.org/abs/1906.02715)
-   [Language, trees, and geometry in neural networks](https://pair-code.github.io/interpretability/bert-tree/) is a great blog post explaining the above paper, probably my favorite thing I read this week
-   [Is Attention Interpretable?](https://arxiv.org/abs/1906.03731)
-   [Attention is not Explanation](https://arxiv.org/abs/1902.10186)
-   In my next blog post I’m hoping to play around with [this library for BERT visualizations](https://github.com/jessevig/bertviz), in particular am curious about attention in one-liner jokes
-   Fellow scholar [Andre Carrera](https://blog.lambdo.com/introduction-openai/) also sent along the following papers that I’m hoping to peruse next week:
	-   [Learning Neural Templates for Text Generation](https://www.aclweb.org/anthology/D18-1356/)
	-   [Turing-NLG: A 17-billion-parameter language model by Microsoft](https://www.microsoft.com/en-us/research/blog/turing-nlg-a-17-billion-parameter-language-model-by-microsoft/)
	-   [The Illustrated Transformer](http://jalammar.github.io/illustrated-transformer/)
    -   [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
    -   [Learning Neural Templates for Text Generation](https://www.aclweb.org/anthology/D18-1356/)
    

Bias
-----
The scholars program is aimed specifically at members of underrepresented groups in deep learning. Examples of the dangers of building and deploying machine learning models built and assessed by non-diverse teams are ubiquitous and troubling. Technology is often heralded as a force for good in the world, but in practice can reinforce bias and exclusion everywhere from loan approval to hiring to criminal sentencing. As we put more and more decision making into the “hands” of machine learning, we risk exacerbating and intensifying the impacts of societal biases.

The question of how to understand the bias of a system is better understood for some protected classes than others. I was fortunate enough to spend a summer thinking about gender representation in the [media](https://mediacloud.org/) with [Nate Matias](https://natematias.com/) and looked at gendered participation in the New York Times comment section for my senior thesis. In the years since, more work has been done in understanding word-embedding level gender biases. I haven’t thought through in detail how this research could be extended to other protected classes or what the correct response is to bias mitigation, but I know a lot of people at OpenAI have and am excited to learn more from them.

-   [Identifying and Reducing Gender Bias in Word-Level Language Models](https://arxiv.org/abs/1904.03035)
-   [Man is to Computer Programmer as Woman is to Homemaker? Debiasing Word Embeddings](https://arxiv.org/abs/1607.06520)
-   [AI Fairness 360: An Extensible Toolkit for Detecting, Understanding, and Mitigating Unwanted Algorithmic Bias](https://arxiv.org/abs/1810.01943)
  

Humor
----
In high school I desperately wanted to become a comedy writer. The only problem was that I wasn’t very funny. This was one of the first things that got me interested in NLP -- if I could teach a computer to write jokes for me, I could achieve my dreams of becoming Tina Fey.

It’s clear that a mastery and understanding of humor will be a requirement of true “natural” language systems. Humor may be related to how we [express intelligence](https://www.inc.com/betsy-mikel/1-unusually-hilarious-trait-smart-people-have-in-common.html), [persuade audiences](https://repository.upenn.edu/cgi/viewcontent.cgi?referer=https://www.google.com/&httpsredir=1&article=1060&context=mapp_capstone), and even [flirt](https://www.jstor.org/stable/348256?origin=crossref&seq=1#page_scan_tab_contents). I want to understand how we build a sense of humor into language models, and I want to use humor to present AI research to a general audience.

Further, I am curious how humor correlates with other areas where language models could be better. For instance, one hypothesis I want to dig into a bit over the next few months is that I think there’s a strong connection between the ways humorous language patterns and purposeful disinformation or misinformation deviate from the norm. While I’m not sure what role humor will play in my final project, I’ve found these papers quite fun and they’ll inform some of the toy projects I’ll work on next week.

-   [Pun Generation with Surprise](https://arxiv.org/abs/1904.06828)