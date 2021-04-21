---
title: 'Asking the Right Questions:
Learning Interpretable Action Models Through Query Answering'
subtitle: 'The paper addresses the problem of learning action models of black-box autonomous agents (both symbolic and simulator) through query answering.'
summary: ''
authors:
- admin
tags:
- Planning
categories:
- Paper critiques
date: "2021-03-25T00:00:00Z"
lastmod: "2021-03-25T00:00:00Z"
featured: false
draft: false

external_link: https://arxiv.org/pdf/1912.12613.pdf

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
# image:
#   placement: 2
#   caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
#   focal_point: ""
#   preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---


**What is the problem being addressed?**

The paper addresses the problem of learning action models of black-box autonomous agents (both symbolic and simulator) through query answering.

**Why is that a problem worth solving?**

Often, AI systems are not designed by their users and they may not be provided specifications of the models. Due to constant learning and change in the models of the agents, it becomes increasingly difficult to ascertain the safety and reliability of the agent. With the increasing deployment of AI systems, it has become important to develop algorithms for assessing models of arbitrary AI agents in a vocabulary that users understand. A method that does not require large amounts of data to infer the models and provides a running estimate of the models in short time durations will make it useful in the real world. 
                                                                                                                  
                                                                                            
**Approach:**

Problem formulation, input requirement: The proposed method aims to learn the true model of an agent by querying the agent and using query responses. The agent assessment module (AAM) defined for such an agent interrogation task takes as input the user predicate vocabulary, instruction set (set of action headers), a set of queries, and a simulator. It provides a plan as a query to the simulator and receives a query response. The objective is to learn query policies (mapping between sequence of query responses to the next query).

Definitions: A concrete model is a set of palm tuples (a set of single variants of pal tuples), and an abstract model is one that lacks at least one pal tuple. A query is a mapping between model and response, a plan outcome query is in the form of a pair of state and a plan, and the query response is in the form of a pair of the length of plan successfully executed and the final state reached from that execution.

Solving agent interrogation task: At each stage of the interrogation, a pal tuple is added to the set of possible abstract models maintained given the agent’s responses up to that point. The idea is to find a single palm tuple corresponding to the added pal tuple through distinguishing queries. This prunes out other abstract models. To find a useful query, first, whether two abstract models are distinguishable by any query is evaluated. If yes, a model consistent with the agent’s true model is found based on the consistency of the generated query’s responses. 
    (i) Generating queries (a planning problem): The goal is to find a plan using a random initial state that would either lead two models to different states (indicating different effects) or to a state where only one of them can execute the plan further (indicating different preconditions). This plan and the initial state are then used as a plan outcome query.
    (ii) Filtering set of possible models: The query is used to prune out at least one model out of the two by comparing their responses with the agent’s response. 

Finally, the approach is empirically evaluated on relational as well as image-based simulator agents and compared with FAMA.


**Limitations:**

- Pal tuple ordering: If the model is assumed to be changing not static, an informed ordering of the pal tuples may reduce the number of queries and the time required to get an accurate estimate of the model. (In the proposed method, if n is the number of pal tuples, at least n and at most 2*n queries are required to find a model accurately. Thus, for static models and querying-process from scratch, the ordering may not matter as much as the time complexity will be the same.)
- Stochasticity: The models learned are deterministic and as the approach compares the length of plans executed by two models, it can not be extended to stochastic environments.
- Vocabulary mismatch handling: Currently, it is assumed that the predicate vocabulary of the user is the same as that of the agent’s model. But what if the user does not have access to the agent's vocabulary?
- Query type: A single (applicable) action seems enough to find a consistent model out of two abstract models in the same node when the pal tuple is present in the effects (preconditions) in the true model. This may have simplified the formulation (instead of using sequences of actions).
 

**Strengths:**

- Compared to FAMA (the extended approach of Aineto’s paper we discussed), the proposed method is more stable and relaxes assumptions about negative literals in the precondition. 
- The proposed method doesn’t require any data such as traces and can be used to find a running estimate while querying. It can also be used if the model changes. 