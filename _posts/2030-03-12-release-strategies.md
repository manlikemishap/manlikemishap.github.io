---
title: 'Release Strategies and Protocols'
date: 2020-03-13
permalink: /posts/2020/03/release-strategies/
tags:
- openai
---

### Why is it important to think carefully about your release strategy?

As much as language models have the potential for beneficial use, . 

Moreover, as many language models operate as "black boxes," it can be difficult to know exactly how a model will behave under all circumstances (). 

How will a model be stress-tested prior to release? 

### What are some options for how to release a model?

I've discussed the "staged release" of GPT-2 a bit above, particularly in contrast to the option of releasing the model all at once. I want to add one more option to the list: an "API" release strategy. 

Think about an old medieval manuscript. You can search and see images of it online, even read what's transcribed and different interpretations by different scholars, but the manuscript itself is held in temperature-controlled libraries, and direct access to the physical copy is limited to scholars with proven expertise by application only. You go through a metal detector when you enter and exit the room where the manuscript is kept.

Another example would be how we control restricted-access datasets, like census data. You can only access the data through particular machines...

We can imagine an analogous approach to releasing a language model: an API that gives us access to a restricted number of calls to the forward pass. Tokens would be meted out via a competitive application process and could be revoked for breaking Terms and Conditions.

The pro's of this are clear: we could ____. Moreover, by having a clear record of our userbase. It further protects IP. The con's are of course that by some definitions it interferes with an open-source science utopia. 

Below, I summarize the three release strategies reviewed. 

|  	| Def 	| Pros 	| Cons 	| Examples 	|
|---------------------	|--------------------------------------------------------	|---------------------------------------------------------------	|-----------------------------------------------------------------	|----------	|
| **Release all at once** 	| Provide full-access to all code and model weights  | Open science 	| People may try to reproduce, compounding energy use of training 	| MuseNet 	|
| **Staged release** 	| Gradually release larger scale models 	| See how real perceived risks are before making final decision 	|  	| GPT-2 	|
| **API model** 	| Provide protected access to forward-pass 	| Retain full control over use 	|  	|  	|

### Is release strategy even the right mechanism to use?

Rewinding for a second, the release strategy is not the only, and may not even be the primary lever we want to use to ensure a "safe" language model. To do that we want to 1) 2) and 3).



### How do we mandate this?

Regardless of how we choose to develop and release a model. We should understand what regulatory frameworks exist to 