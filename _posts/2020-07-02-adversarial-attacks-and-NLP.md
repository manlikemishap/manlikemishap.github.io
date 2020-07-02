---
title: 'Adversarial Attacks and NLP'
date: 2020-03-20
permalink: /posts/2020/03/universal-adversarial-triggers/
tags:
  - openai
---

This is an updated version of a [March blog post](https://manlikemishap.github.io/posts/2020/03/universal-adversarial-triggers/) with some more details on what I presented for the conclusion of the OpenAI Scholars program. Mostly, I've added a brief results section. If you're interested in collaborating further on this please reach out!

Growing up, I knew that saying to my sister that Meg Cabot wasn't the greatest author to ever live would cause her to yell at me. I knew this because I had pretty strong knowledge of *my* sister and *her* particular quirks. Saying this to other older sisters would probably yield mixed results. Criticizing Meg Cabot was, in this case, a **non-universal** trigger. It works on some older sisters, but not all.

I can however hypothesize that pulling the hair of $any$ older sister $anywhere$ would probably get the perpetrator yelled at. We refer to this as a **universal** trigger. In this post I'll walkthrough work by [Wallace, et. al. (2019)](https://arxiv.org/pdf/1908.07125.pdf) defining and finding **universal adversarial triggers** for language models. For those who prefer to follow along in code, reach out to me for the Colab notebook. For those who prefer to follow along in pictures of Tigger, stay right where you are.

Some familiarity with GPT-2 and language models may be helpful. But all you really have to know is that given some input sequence of words $\mathbf{t}$, GPT-2 will spit out some output sequence of words $y$. For example, given sequence $\mathbf{t}=$`I pulled my sister's hair so she`, GPT-2 may return $y=$`yelled at me`. Note that in learning about what tokens were expected after $\mathbf{t}$, GPT-2 also "learned" something about the relationship between sisters. Interesting, eh?

You can try it out with [HuggingFace's Write with Transformer](https://transformer.huggingface.co/doc/gpt2-large), though the above trigger/response pair is not guaranteed.

## The good, the bad, and the trigger

![Image result for tigger illustration original](https://upload.wikimedia.org/wikipedia/en/3/34/Pooh_meets_Tigger%2C_illustration_by_EH_Shepard.gif)

### What's the point?

This is a question I've struggled with a bit, since the threat model for where and how a trigger would be used is a bit unclear. 

The clearest use of a universal trigger is that we may not have access to the target model or the particular input at run-time. Because universal attacks do not require white-box access and work on any input, they can be easily distributed even without technical knowledge -- if someone discovers a trigger that works on GPT-2, it can be easily published to Reddit. And, there's some evidence that a trigger [might apply to other models as well](https://arxiv.org/abs/1705.09554). 

This is concerning, but there are easier ways to generate and to distribute hate-speech. Rather than thinking in terms of how an adversarial actor might use a trigger, I want to motivate this work by focusing on how triggers can be employed as interpretability and evaluation tools to better understand a model and potential adversarial threats posed. 

In other words, identifying and understanding how a model responds to particular triggers is mostly a good way of stress-testing how our model responds to local perturbations. Adding a six token string to the end of any Shakespeare play shouldn't result in hate speech (even if the play is The Merchant of Venice). We should understand triggers as demonstrations of a failure state.

### What makes a good (bad) trigger

If we allow ourselves to use a very long trigger we can probably make this task pretty easy: throw a ton of racist language in, we're likely to get racist language out. However, shorter triggers will force us to be a bit more clever and stealthy. What if I can give you any paragraph of perfectly innocuous language, and then by just attaching three words at the end GPT-2 will return racist output?

This potentially goes beyond length. If we can write language that makes more sense or has a higher readability and likelihood score, it will feel stealthier when attached to other input.

## Finding the trigger

![Image result for tigger hiding](https://pbs.twimg.com/media/EGQGlSGWsAUCg55.jpg)

We want to learn a trigger ($\mathbf{t}_{adv}$) for *ANY* input ($\mathbf{t}\sim\mathcal{T}$), not just a specific one. And we'll do this assuming we have access to the model ($f$) and its loss function ($\mathcal{L}$), that will cause the model to generate text similar to a pre-determined set of targets ($\mathcal{Y}$). 

Wallace, et al. find that they can leave out optimizing over $\mathcal{T}$ entirely and achieve similar results, so we start from that point.

### The HotFlip Attack

How do we iterate over every possible $\mathbf{t}_{adv}$? The simple answer is, we can't. While adversarial attack methods from computer vision rely on the existence of a continuous feature space to come up with attacks, tokens are discrete. As an approximation, the paper instead uses the HotFlip ([Ebrahimi et al., 2018](https://arxiv.org/pdf/1712.06751.pdf)) approach, approximating the effect of replacing a token using its gradient.  

Starting with the first token in our sequence, we seek to minimize the loss for the target prediction over batches of examples. Going token by token, if we can replace the given token with something that decreases the loss, we do.

### Improvements

The above is the approach taken by the paper. This yields triggers that are quite non-sensical, because the tokens in the triggers are not constrained by anything we know makes good language. This means the triggers are not stealthy, because even if we concatenate them with reasonable language, it's immediately evident that they themselves are out of place.

To prevent this, we try limiting our sampling to tokens predicted by GPT-2.

## A handful of results

We replicated the original paper's results, showing the method works in attacking sentiment analysis, question-answering, natural language inference, and language generation.

In addition, we found that triggers transferred to GPT-3, albeit with slightly decreased accuracy. We showed that on both GPT-2 and GPT-3, triggers optimized for targeting one protected class often generated text biased or hateful across a different protected dimension. For example, triggers optimized to generate racist and sexist speech produced language that was homophobic and ablist.

Finally, we found that triggers exist for other topics (we looked in particular at vaccines and Brexit), though found that they were slightly less potent in tone and content.

## Future work

There's a lot of interesting work to be done on things like
1. Understanding how triggers point to larger model vulnerabilities
2. Using triggers as tools for interpretability
3. Employing HotFlip techniques to find optimal task descriptions for few-shot learning
