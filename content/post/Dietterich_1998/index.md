---
title: 'The MAXQ Method for Hierarchical Reinforcement Learning'
subtitle: ''
summary: ''
authors:
- admin
tags:
- HRL
categories:
- Paper critiques
date: "2021-02-19T00:00:00Z"
lastmod: "2021-02-19T00:00:00Z"
featured: false
draft: false

external_link: http://matt.colorado.edu/teaching/RL/readings/dietterich%201998%20ICML%20maxQ.pdf

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

The authors address the problem of finding recursively optimal policies through methods for hierarchical reinforcement learning (HRL) that are general-purpose, support non-hierarchical execution, preserve the markovian property of subtasks involved, and are not adversely affected by state abstractions. They also address the issue of hierarchical credit assignment often encountered in HRL. 

**Why is that a problem worth solving?**

HRL exploits hierarchical structure within MDPs and has a lot of advantages over flat RL such as improved exploration, faster learning through reusability of subtasks, and fewer trials required to learn due to focus on the relevant features of states. Most of the HRL methods that focus on finding recursively optimal policies are specific to solving particular tasks and suffer from non-markovian tasks at each level in the hierarchy. Thus, newer methods that can overcome these disadvantages will solve more general tasks and learn more easily. Moreover, we need methods that can employ the benefits of state abstraction without suffering from the loss of optimality and also produce better non-hierarchical policies if the learned hierarchical policies are not optimal.
                                                                                                                     
                                                                                            
**Approach:**

The authors introduce the concept of the MAXQ hierarchy that represents the decomposition of an entire MDP into a hierarchy of smaller MDPs. It consists of alternating Max nodes and Q nodes. Max nodes represent either primitive actions or subtasks and Q nodes represent actions used to achieve their parent’s subtasks. Each Max node learns the expected cumulative reward of performing its subtask independent of the context while each Q node learns it depending on the context. This context independence learning of rewards encourages reusability of subtasks. Finally, a hierarchical policy is found by learning a set of policies, one for each Max node.

The MAXQ hierarchy can be interpreted as the value function of a hierarchical policy. Each subtask is considered as a separate MDP and the value function of the complete MDP can be recursively decomposed into the value functions of the subtask MDPs. Thus, the biggest advantage of the proposed approach is derived from parallel execution of each Max node. 

Finally, the authors define a hierarchical Q learning algorithm for the proposed MAXQ hierarchy, prove its convergence, and evaluate it against standard Q learning. 



**Limitations:**

- The biggest limitation of the paper is that it assumes that the hierarchical structure of an MDP is known. Methods to construct task hierarchies automatically require research.
- Extending the MAXQ approach to multi-agent domains is another research area that deserves attention.

**Strengths:**

- I found the idea of improving a learnt hierarchically non-optimal policy using the hierarchical value function to produce a non-hierarchical policy that is provably closer to optimal policy most interesting. 
- I also like that even though recursively optimal policies are weaker than hierarchically optimal policies, they can be learnt without the context of the subtasks unlike the latter.