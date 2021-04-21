---
title: 'Foundations for Restraining Bolts:Reinforcement Learning with LTLf/LDLf restraining specifications'
subtitle: 'The paper investigates methods for solving reinforcement learning while conforming to LTL restraining specifications, such that, the restraining bolt accounts for features of the world distinct from the RL agent.'
summary: 'The paper investigates methods for solving reinforcement learning while conforming to LTL restraining specifications, such that, the restraining bolt accounts for features of the world distinct from the RL agent.'
authors:
- admin
tags:
- RL
categories:
- Paper critiques
date: "2021-04-02T00:00:00Z"
lastmod: "2021-04-02T00:00:00Z"
featured: false
draft: false

external_link: http://www.diag.uniroma1.it/degiacom/papers/2019/icaps19dfip.pdf

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

The paper investigates methods for solving reinforcement learning while conforming to LTL restraining specifications, such that, the restraining bolt accounts for features of the world distinct from the RL agent.

**Why is that a problem worth solving?**

When deploying learning agents in the real world with humans, it becomes crucial to perform RL effectively in the presence of the humans and their specifications. Moreover, often the RL agents and the humans model different aspects of the same world, that is, their representations of the world are distinct. In such scenarios, finding solutions that conform to the specifications of the bolts can be difficult and necessitates the investigation of RL in the presence of restraining bolts. 
                                                                                                                     
                                                                                            
**Approach:**

The proposed method uses restraining bolt specifications in the form of Linear Temporal Logic (LTL) formulas. These specifications assume features distinct from the features of the RL agent. The LTL formulas also contain a reward structure and can be transformed into a deterministic finite-state automaton (DFA). The method keeps a track of the automaton state while the RL agent is executing. This helps to track the stage of satisfaction of the LTL formula specification. The cross product of the state of the automaton and the state of the RL agent allows for transforming the original Non-markovian reward decision process (NMRDP) into an equivalent MDP. On satisfaction of the specification, rewards from LTL formulas are provided to the RL agent in the form of additional rewards for reward shaping of the environment. Such exploitation of the reward structure from the DFA speeds up learning.

The authors evaluate the method on breakout, sapientino, cocktail party, and Minecraft domains.

**Limitations:**

- The approach assumes strictly that the state of the automaton is known at every time step. However, if the restraining bolt itself has noisy sensors, it needs to account for the confidence levels of its state.
- The paper doesn’t shed light on whether the formulation would change if the features of the restraining bolt overlap with the features of the RL agent. as humans may be able to see certain features exactly as an RL agent does. Thus, instead of strict distinction between the features of an RL agent and restraining bolt, the assumption needs to be relaxed. 
- Although, the authors explicitly specify that they do not guarantee the hard satisfaction of constraints, the paper lacks conditions in which such a guarantee can be provided. A study of soft and hard constraints with respect to the restraining bolt is required.

 

**Strengths:**

- I like that the method doesn’t require the restraining bolt to have any information about the RL agent. This reduces the burden on humans using an AI agent. It also helps to specify safety constraints easily. 
- I also like the idea of using LTLs to provide reward structure.