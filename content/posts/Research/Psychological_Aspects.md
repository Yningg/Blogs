---
title: "Psychological Aspects in Retrieval and Recommendation"
date: 2025-10-24
tags: ["Psychology", "Recommendation Systems", " Information retrieval"]
categories: Psychology
ShowToc: true
TocOpen: true
---

> Some notes on the Paper "Psychological Aspects in Retrieval and Recommendation" published in SIGIR 2025, together with its slides available at: https://github.com/aisocietylab/Psy-IR-RecSys-SIGIR25/tree/main.


The tutorial focuses on three key psychological topics and sheds light on how they influence and manifest in the IR and RS ecosystem: *cognitive architectures, cognitive effects and biases, and personality and affect*.

## Motivation 

Understanding human cognition, decision-making processes, and psychological factors is important to **enable user-centric retrieval and recommendation systems**.

Understanding whether these aspects are also present to some extent in the systems themselves (e.g.,in training data, ranking models, or outputs), or even integrating them in the systems on purpose, can **inform the development of psychology-inspired systems**.


## Cognitive Architectures
> Cognitive architectures aim to model human-like cognitive processes such as perception, memory, learning, and problem-solving.

This paper covers several well-established cognitive architectures, discussing <u>how they model human cognition</u> and <u>how they can be used to design adaptive, user-centric retrieval and recommendation techniques</u>.

### Fundamentals of Human Cognition
**Human Cognition**: set of mental processes involved in acquiring, processing, storing and utilizing information, including perception, attention, memory, learning,
reasoning, decision-making, problem-solving.
-->  Core to how users interact with IR and RS, search perceive results and make choices in IR/RS contexts

![alt text](/Blogs/Figures/IR_RS_cognitive_mapping.png)


### Cognitive Load
+ Cognitive Load Theory (CLT) (Sweller, 1988):
  + Users have limited working memory
  + Performance depends on used capacity of working
memory

+ CLT defines three types of load:
  + Intrinsic: inherent difficulty of task
  + Extraneous: poor interface/irrelevant info
  + Germane load: effort needed to build useful insights("schemas in memory")

### Taxonomy of Cognitive Architectures
![alt text](/Blogs/Figures/cognitive_archi.png)


### Major Cognitive Architectures
+ Manifold cognitive architectures have been proposed to model human cognition
+ Ranging from symbolic to subsymbolic to hybrid and emergent approaches
+ Some are particularly suited for modeling user behavior in IR/Rs:

  + **Adaptive Control of Thought-Rational (ACT-R)**.  ACT-R models human cognition through memory modules and has been used to deliver personalized music recommendations, job recommendations, and model repeat music consumption.
  + **Soar**, which models problem-solving and goal-driven learning, making it particularly useful for modeling long-term effects in RS.
  + **CLARION**, a hybrid architectures that integrate symbolic reasoning with subsymbolic learning.
  + **Learning Intelligent Distribution Agent (LIDA)** architecture can give insights into how attention and novelty influence human decision making and can be used to model serendipitous recommendations and content discovery processes, ensuring that users are exposed to a balanced mix of familiar and novel content.

### Pros and Cons
+ Benefits:
  + Typically, better interpretability - potential for explainability
  + Allow for user-centric modeling
  + Adaptive, cognitive plausible systems

+ Challenges:
  +  Scalability to large datasets and real-time systems
  +  Integration with advanced deep learning models
  +  Explainability vs. accuracy trade-offs
  +  Learning curve for researchers (interdisciplinarity!)

+ Future Research Directions
  + Neuro-symbolic IR and RS
  + Hybrid models combining cognitive models + data-driven machine learning
  + Real-time adaptation based on user cognitive signals
  + Evaluation frameworks based on cognitive plausibility
  + Potential for interpretable and adaptive IR/RS

## Cognitive Effects and Biases

> Human decision-making processes are strongly influenced by cognitive biases, which encompass both <u>systematic individual deviations from rationality</u> and <u>societal prejudices</u> that favor one group's values, norms, and traditions over others.

Human decision making nowadays is often supported, or even replaced, by IR and RS. Given the prevalence of both cognitive biases as well as IR and RS technology in shaping human decisions, an investigation of their interaction is vital.

### Cognitive Biases: Examples
+ **Feature-Positive Effect**: Humans are better at realizing (and put more emphasis on) the presence of a stimulus rather than its absence
  
+ **IKEA Effect**: The more effort a person invested in something, the more they will value it (Human desire to justify their efforts)
  + e.g., Users tend to interact more with playlists they invested effort in, which can be used to increase user experience in sequential recommendation, where  items present in the user's playlists can serve as anchors to retain user engagement within the current listening session.

+ **(Social/Cultural) Homophily**: Humans tend to associate and form connections with others who have similar characteristics (e.g., age, culture, or religion) more often than with people who have different traits
  + e.g., Users with a specific trait (e.g., country, culture, or social group) may prefer content created by producers with the same trait (e.g., domestic vs. foreign music consumption)

+ **Conformity Bias**: Tendency of individuals to align their beliefs, behaviors, and actions with those of a group, often disregarding their own independent judgment
  + e.g., Users are more likely to click on an item if they see that many other users clicked on it 

+ **Declinism**: The perception that the world or society is declining, i.e., things get worse over time. Partly the result of rosy retrospection — humans’ tendency to remember the past as more positive as it actually was.
  + e.g., Can these models be used to adjust outcomes, to counteract (or amplify) declinism?

+ **Primacy/Recency Effects, Position Bias**: Human tendency to easier recall first and last items from a sequence as opposed to the
items from the middle of the sequence 
  + e.g., Users are more likely to interact with items appearing at the beginning (primacy effect) and at the end (recency effect) of a list of recommendations or retrieved documents
  + e.g., Can we counteract this effect by algorithmic in-processing or post-processing techniques (e.g. reranking)?


+ **Halo and Horn Effects**: An individual’s perception of a single attribute (positive or negative) influences their opinion on other unrelated attributes
  + e.g., Visual appeal of the presentation of (some) search results can influence clicking/consumption behavior
 
### Conclusions and Open Challenges
+ Strong evidence of various cognitive biases in retrieval and recommendation processes
+  Most studies face several limitations (e.g., only single or few domains, standard top-N recommendation scenario, ignoring confounding factors)

+ How to (mathematically) formalize accurate models of cognitive biases?
+ Which CoBis are intertwined and how does their entanglement manifest?
+ Which CoBis are important for different stakeholders?
+ What role does the user interface play?
+ How do CoBis manifest in other retrieval and recommendation tasks and domains, e.g., sequential recommendation; video, travel, people?

<u>Need a holistic discussion of both negative and positive effects of cognitive biases, and for new approaches to algorithmic decision making that mitigate the former while leveraging the latter.</u>

## Personality and Affect
> The user enters the interaction with the system with certain preferences, expectations, and experiences a level of satisfaction with the results. Several psychological constructs are related to these aspects of IR and RS.

### States vs. Traits
![alt text](/Blogs/Figures/traits_states.png)

### Personality and Emotions
+ **Mood**: no particular trigger, can be positive/negative
+ **Emotions**: can be triggered

![alt text](/Blogs/Figures/personality.png)

### Emotions vs mood vs sentiment
+ Emotion:
  + brief in duration
  + consist of a coordinated set of responses (verbal, physiological, behavioral, and neural mechanisms)
  + triggered

+ Mood:
  + last longer
  + less intense than emotions
  + no trigger

+ Sentiment
  +  towards an object
  +  positive/negative

### Models of Emotions
Emotions are complex human experiences and will evolve over time. Here just discuss simple models that easy to be incorporated in computers: <u>basic emotions</u> and a <u>dimensional model</u>.

#### Basic Emotions
+ Discrete classes model
+ Ekman definition (6 + neutral): happiness, anger, fear, sadness, disgust, surprise

#### Dimensional model of emotions
+ Includes three continuous dimensions
  + Valance/Pleasure (positive-negative)
  + Arousal (high-low)
  + Dominance (high-low)

#### How to measure emotions
+ Questionnaires
+ Multimodal prediction (affective computing): modalities includes audio, language, visual, and physiology


#### Emotions in RS and IR
For recommendation system:
+ Educational field
  + match task/lesson difficulty to stress
+ Emotions as context
  + recommendations based on current emotions
+ Emotion as feedback
+ Group settings: emotional contagion

For information retrieval, the emotions reframe the IR problem towards emotional relevance, ot just topical relevance

### Personality models
> Personality accounts for individual differences ( = explains the variance in users) in our enduring emotional, interpersonal, experiential, attitudinal, and motivational styles

The Five Factor Model (Big 5): - Extraversion, Agreeableness, Conscientousness, Neuroticism (inverse = Emotional Stability), Openness (to new experiences)

#### How to measure personality?
+ Questionnaires: lengthy, time consuming, intrusive
  + NEO-PI-R: 240 items
  + IPIP-50
  + BFI: 44 items
  + TIPI: 10 items

+ Inference from digital traces
  + Digital traces: such as instagram, twitter, eye tracking data, brainwaves, physiological sensors
  + pretrained models
  + ethical issues

#### Personality in Recommender Systems
+ Cold-start problem: user-user similarity based on personality
+ Diversity: Personality-based diversity adaptation
+ Cross-domain recommendations: personality-based profiles in different domains
+ Group recommender systems: Combining assertiveness and cooperativeness into the aggregation function
+ Social media: followee recommendations

#### Personality in Information Retrieval
+ Few studies: mainly the personality of the system not the user
+ Lots of opportunities


### Open Challenges
+ Data acquisition (technical, legal, and ethical aspects), in particular regarding sensitive user traits.
+ Improving the communication between the relevant research communities, including computer science, artificial intelligence, psychology, and sociology, in order to foster interdisciplinarity.

