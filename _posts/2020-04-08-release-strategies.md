---
title: 'Release Strategies and Language Models'
date: 2030-04-08
permalink: /posts/2030/04/release-strategies/
tags:
- openai
---

In February 2019, OpenAI released the language model [GPT-2]([https://openai.com/blog/better-language-models/](https://openai.com/blog/better-language-models/)). Well, they released results from it. The full 1.5 billion parameter model was actually released 9 months later in November. In this post I'll define different release strategies and talk through some of the arguments for and against each. 

### Why is it important to think carefully about your release strategy?

As much as language models have the potential for beneficial use, they can potentially also be used by adversarial actors for example in [generating fake content](http://google.com) or [impersonating different kinds of speech](http://google.com). 

Moreover, as many language models operate as "black boxes," it can be difficult to know exactly how a model will behave under all circumstances, so there are plenty of risks associated with deploying it to different applications before it has been robustly tested on a diverse set of tasks. For example, within 24 hours of Microsoft releasing the chatbot "Tay" on Twitter, the bot devolved into [responding to users with misogynistic and racist language](https://www.theverge.com/2016/3/24/11297050/tay-microsoft-chatbot-racist). 

Carefully thinking about how to release a model is one lever we can use to gradually understand and evaluate the risks of that model in the world.

### What are some options for how to release a model?

I've discussed the "staged release" of GPT-2 a bit above, particularly in contrast to the option of releasing the model all at once. I want to add one more option to the list: an "API" release strategy. 

Think about an old medieval manuscript. You can search and see images of it online, even read what's transcribed and different interpretations by different scholars, but the manuscript itself is held in temperature-controlled libraries, and direct access to the physical copy is limited to scholars with proven expertise by application only. You may go through a metal detector when you enter and exit the room where the manuscript is kept.

Another example would be how we control restricted-access datasets, like census data. You can only access the data through particular machines and after a rigorous . Any results you want to publish using the data goes through a rigorous review process to ensure results can't be de-anonymized.

We can imagine an analogous approach to releasing a language model: an API that gives us access to a restricted number of calls to the forward pass. Tokens would be meted out via a competitive application process and could be revoked for breaking Terms and Conditions.

The benefits of this approach are clear: by maintaining a record of when and how a model was used we could retain full control over potential misuse. The drawbacks are of course that by some definitions it interferes with an open-source science utopia. 

Below, I summarize the three release strategies discussed:

|  	| Def 	| Pros 	| Cons | 
|---------------------	|--------------------------------------------------------	|---------------------------------------------------------------	|-----------------------------------------------------------------	|----------	|
| **Release all at once** 	| - Provide full-access to all code and model weights | - Open science 	| - Miss out on potential beneficial uses <br>- If folks try to reproduce, compound energy use of training 	| MuseNet 	|
| **Staged release** 	| - Gradually release larger scale models 	| - See how real perceived risks are before making final decision 	|  	| GPT-2 	|
| **API model** 	| - Provide protected access to forward-pass 	| - Retain full control over use 	| - Limits who has access to interrogate and utilize parts of model 	|  	|

### Is release strategy even the right mechanism to use?

Rewinding for a second, the release strategy is not the only, and may not even be the primary mechanism we want to use to ensure a "safe" language model. 

If we rely solely on the release stage, it may be too late to ensure a model is safe and the pressure to release may be too high to have an effective debate. We also need levers at other stages of the development process.

A recent paper by [Madaio, et. al (2020)](http://www.jennwv.com/papers/checklists.pdf) puts forward a "checklist" approach for developers to use to benchmark their progress against fairness objectives. The checklist is inspired by the process surgeons go through before, during, and after surgeries and is co-designed with ML practitioners to align with their existing workflows. Fairness is hard, and the fuzzy nature of ethics principles don't always mesh with developers' quantitative approach. By using open-ended questions and engaging practitioners at every step of their design and implementation process, this approach bridges some of the gap between development and end-user stakeholders. 

There certainly are other checklist approaches -- one that springs to mind is the UK Department of Digital Culture, Media, and Sport's [Data Ethics Workbook](https://www.gov.uk/government/publications/data-ethics-workbook) -- but those developed by public-sector organizations often fail to match how machine learning models are actually designed and deployed. For example, the Data Ethics Workbook applies narrowly to what we might call "data science" -- collecting and analyzing data -- and fails to address the particular subtleties of deep learning.

There are also efforts to develop quantitative toolkits developers can deploy, however these are often targeted at the end-product (falling into the "potentially too-late" category) and may not be able to measure all of the nuanced fairness that we want. Moreover, most toolkits aren't capable of capturing every nuanced dimension of fairness, toolkits like [AI Fairness 360](http://aif360.mybluemix.net/) provide lenses to think about racial, gender, and age disparities, but fail to measure [other protected classes](https://www.un.org/ruleoflaw/thematic-areas/human-rights/equality-and-non-discrimination/).

### How do we mandate this?

Regardless of how we choose to develop and release a model, we should understand what regulatory frameworks govern its design and release. As private-sector organizations design processes for meeting these regulations we should incentivize them sharing these systems and practices publicly.