---
title: Emergent Abilities of Large Language Models
category: ai
layout: post
excerpt: AIs learn unexpected new skills as they get larger. What does this imply?
issn: 20547390
doi: 10.48550/ARXIV.2206.07682
tags: [large-language-models, artificial-intelligence, emergence]
reference: >
  Wei, J., Tay, Y., Bommasani, R., Raffel, C., Zoph, B., Borgeaud, S., Yogatama, D., Bosma, M., Zhou, D., Metzler, D., Chi, E. H., Hashimoto, T., Vinyals, O., Liang, P., Dean, J., & Fedus, W. (2022). *Emergent Abilities of Large Language Models* (Version 2). arXiv. [https://doi.org/10.48550/ARXIV.2206.07682](https://doi.org/10.48550/ARXIV.2206.07682)
---

### In Brief

Large language models (LLMs), such as GPT-3 that powers [ChatGPT](https://openai.com/blog/chatgpt/) demonstrate *emergent abilities*.  That is: By training models on incrementally more data, they eventually hit a scale where they suddenly “learn” new skills – for example, at a certain size, a LLM becomes capable of translating from one language to another, and below that size it is incapable of doing so.

This paper is primarily a survey of the literature of emergent abilities, it does not propose new methods but draws some interesting conclusions about emergent abilities:

* There currently exists no compelling explanation for why emergent abilities occur in LLMs
* We can’t extrapolate current LLM abilities into the future, it is entirely possible that at increased sizes, LLMs will suddenly pick up the ability to perform more tasks, and we don’t know what those abilities will be.
* "Emergent risks" are every bit as important as emergent abilities, what are LLMs getting better at with scale that is undesirable (e.g. spreading convincing misinformation)

### Important Definitions

This paper discusses emergent abilities in LLMs, so let's start by defining these things, starting with the LLM itself.

An LLM is a type of artificial intelligence (AI) system that has been trained to process and generate natural language text. LLMs are typically trained on vast amounts of text data, such as books, articles, and websites, in order to learn the patterns and structures of human language.  LLMs can be used for a variety of purposes, including translation, summarization, question answering, and text generation. They are able to understand and generate human-like text because they have learned to analyze and predict the structure and content of language based on the examples they were trained on.

At time of writing this summary, there is a huge interest in LLMs primarily because of the public release of ChatGPT, which is a striking, publicly accessible, example of a LLM that can be used by the general public.  ChatGPT sometimes feels remarkably human, which given that an LLM itself is nothing but a statistical model is quite striking, which brings us to the concept of *emergence*

>Emergence is when quantitative changes in a system result in qualitative changes in behavior.

In the case that is relevant here, this means that as we make a *quantitative* change to a LLM (e.g. adding more training data), we are finding *qualitative* changes (e.g. the model suddenly got good at math, or translation), which leads us to our last definition: emergent abilities.

> An ability is emergent if it is not present in smaller models but is present in larger models.

### What They Did

First, the authors demonstrate emergent abilities in five different LLMs, using prompting.  Prompting, or prompt engineering, is how many current LLMs are coaxed into solving different problems.  An LLM is a statistical model trained to look at some text and predict what the next word will be.

By surrounding a user query with text we can cause the LLM to do different things.  For example, if we wanted to summarize an article, we may use the following prompt for the LLM:

```
This is an article followed by a summary:

<INSERT ARTICLE>

In summary:
```

If we insert an article in the designated spot and let the LLM start completing after the text "In summary:", it will begin to summarize the article. If we wanted to build a chatbot (a-la ChatGPT), we may build a prompt like this:

```
This is a conversation between a human (HUMAN)
and a helpful AI (BOT)

HUMAN: What is the capital of England?
BOT: London
HUMAN: <INSERT HUMAN QUESTION>
BOT:
```

And insert a human's question in the designated location, the AI will autocomplete an answer.

In the present paper, the authors pick a few benchmark tasks, and show that all the language models show emergent behaviors, as demonstrated in this figure.

<figure>
  <img alt="Figure 2 from the paper, eight panels showing the performance of different LLMs on problems" src="/assets/images/posts/emergent/fig2.png" />
  <figcaption>
    Fig. 2 from the paper.  Each of the 8 panels represents a different task, and the lines show how good the language model is at that task.  The horizontal red line in each panel is random chance.  Below some scale, models generally perform no better than random chance, and then suddenly they hit a scale where the problem becomes "understood" and they are able to perform it.
  </figcaption>
</figure>

### Interpretation

Emergent abilities are -- by their very definitions -- things that we can't predict that a LLM will learn to do.  Tasks that LLMs currently struggle with are prime candidates for future places to look for emergent abilities (there are dozens of examples listed in appendix E4, including: authorship verification, checkmate in one, language games, mathematical induction, word problems on sets and graphs).  Emergent abilities are not just theoretical, the word-in-context benchmark (a task where the LLM has to distinguish which of the two meanings of the same word it has, given its context) was once outside the realm of what LLMs could handle, but with enough scale, the models became able to solve those problems.

Emergent abilities have prompted a sociological shift in AI research, away from custom-building single-purpose AIs and into an explosion of research and development on general purpose models. The ability for general-purpose models to perform unseen tasks given only a few examples has also led to
many new applications of language models outside the research community. For instance, language models have been used via prompting to translate natural language instructions into actions executable by robots, interact with users, and facilitate multi-modal reasoning. Large language models have also been deployed in the real-world both in products, such as GitHub CoPilot.

#### Emergent Risks

Emergent abilities appear in LLMs without explicitly being trained in (for example, the ability to translate from one language to another was not targeted, but just "dropped out" of the model).  Is it possible that larger language models actually become *worse* at certain things?  For example, truthfulness, bias and toxicity.  There exists the [inverse scaling prize](https://github.com/inverse-scaling/prize), which is offering cash rewards for the strongest examples of tasks that show this behavior.
