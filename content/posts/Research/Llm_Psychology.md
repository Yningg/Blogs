---
title: "Large Language Models Do Not Simulate Human Psychology"
date: 2025-08-18
tags: ["LLM", "Psychology"]
categories: Psychology
ShowToc: true
TocOpen: true
---

> Here are just some notes taken while I was reading.

Recently, some research has suggested that LLMs may even be able to simulate human psychology and can therefore replace human participants in psychological studies. We caution against this approach.

+ First, we provide **conceptual arguments** against the hypothesis that LLMs simulate human psychology.
+ We then present empiric evidence illustrating our arguments by demonstrating that <u>slight changes to wording that correspond to large changes in meaning lead to notable discrepancies between LLMs' and human responses</u>, even for the recent CENTAUR model that was specifically fine-tuned on psychological responses. 
+ Additionally, different LLMs show very different responses to novel items, further illustrating their **lack of reliability**. 

We conclude that **LLMs do not simulate human psychology** and recommend that psychological researchers should **treat LLMs as useful but fundamentally unreliable tools** that need to be validated against human responses for every new application.


## Introduction

The core function of any LLM is to simply predict the probability of each possible next word (more precisely: the next token), randomly select the next word according to the predicted probabilities, and continue until all desired text is generated--<u>with no explicit regard for meaning or truth</u>.

**Task** that particularly related to psychological science: simulating human participants' responses and thus reducing or potentially eliminating the need for such participants.

**The structure of a prompt**
+ A description of a person or a certain participant group the LLM is supposed to simulate  (e.g., US American women over 40)
+ A stimulus, such as a vignette
+ The questionnaire the simulated participants are supposed to answer

> LLMs can, fundamentally, not simulate human psychology when dealing with novel scenarios that go too far beyond the LLMs training data.

## Critiques of LLMs as Simulators of Human Psychology

**Non-Human Reactions to Instructions**: LLMs do not always react to instructions as intended
+ Zhu et al. [2024] empirically investigated LLMs as user simulations in recommender systems and found that recommendations only became accurate if the prompt contained a lot of information about the target user whereas less extensive prompting yielded inaccurate recommendations.
+ Garcia et al. [2024] revealed that LLM moral judgments shifted more dramatically than human judgments depending on framing of moral scenarios.
+ Wang et al. [2025] argue that the textual descriptions in typical prompts are too simplistic to accurately describe a human persona

**Inconsistency Across Simulations**: 
+ Assigning human-like identities to LLMs does not lead to consistent human-like behavior
+ Behaviors are highly sensitive to prompt formulations and model architectures

**Inability to Capture Human Diversity**: LLMs are unable to reproduce the variance and diversity of human responses, even if prompted with different personas

**Biases of LLMs**:  biases tend to be different from human biases because training data is not representative of human diversity

**"Hallucinations"**: Multiple authors report the tendency of LLMs to "hallucinate", meaning the generation of factually incorrect or fictional content that appears superficially convincing
+ a simple explanation is that there is no mechanism inside an LLM that would distinguish between fact or fiction

**Theoretical Arguments**:
+  [Van Rooij et al., 2024] have provided a mathematical proof that it is computationally infeasible to find a computational model (such as an LLM) that responds like humans across all possible inputs, just based on observations

+ The training data containing examples of human-like responses to psychological stimuli does not imply that the trained LLM will also respond human-like to new stimuli – only that the text output will look superficially similar.

## Demonstrations of the Limitations of LLMs

We test whether LLMs simulate human psychology when items are re-worded.

## How can LLMs Support Psychological Research?
+ We recommend that psychologists should refrain from using LLMs as participants for psychological studies.

+  LLMs may be useful in other ways in psychological research, for example as tools for brainstorming, pilot testing, and refining experimental materials, perhaps even automating single, well-validated steps of data annotation. Crucially, however, <u>researchers should remain able to validate all LLM outputs - and this is not possible if the LLMs produce the primary research data</u>.