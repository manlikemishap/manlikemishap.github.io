---
title: 'Getting Stuck @OpenAI'
date: 2020-02-28
permalink: /posts/2020/02/openai-post-2/
tags:
  - openai
---

Hi everyone! This blog post will be short since I’m not done with the one I wanted to write. That said, I’ll flesh out this one a bit more over the next week with code and math.

I spent this week working on implementing a machine-comprehension model to work on the CoQA dataset. Our approach uses bi-directional recurrent neural networks in which the input sequences are fed in forward and backward.

We used pytorch-lighting for this approach. A lot of the simplifications offered by the library actually made things more complicated at times as we tried to make our data fit into the library’s specifications. 

I worked remotely with another scholar implementing this, which was a really good way to test both of our understandings and take advantage of asking both of our mentors questions. It would have been nice if colab was a bit more collaborative though.
