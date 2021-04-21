---
title: 'Value Iteration Networks'
subtitle: 'The paper addresses the problem of exploring better generalizing policy representations mainly in the form of neural networks that can learn planning computations required for goal-directed behavior and solve general unseen tasks.'
summary: ''
authors:
- admin
tags:
- Planning
categories:
- Paper critiques
date: "2021-02-26T00:00:00Z"
lastmod: "2021-02-26T00:00:00Z"
featured: false
draft: false

external_link: https://arxiv.org/pdf/1602.02867.pdf

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

The paper addresses the problem of exploring better generalizing policy representations mainly in the form of neural networks that can learn planning computations required for goal-directed behavior and solve general unseen tasks.


**Why is that a problem worth solving?**

Reactive policies learned through Convolutional Neural Networks with Reinforcement Learning do not have the ability to understand a goal-directed behavior which obstructs their ability to generalize to new unseen tasks. This motivates the idea of studying the connections between planning algorithms and neural networks, specifically, embedding the Value Iteration planning algorithm within neural networks to effectively learn to plan and find better generalizable policies.
                                                                                                                     
                                                                                            
**Approach:**


The paper introduces a Value Iteration Network (VIN) that can learn to represent general policies for an MDP. To this end, the authors propose to construct a new unknown MDP with possibly the same set of states and actions as the original MDP, and the reward and transition probability functions dependent on the observations in the original MDP. A value iteration module that can learn to approximate the value computations is represented by a recurrent convolutional neural network and used to solve this new MDP. To preserve the local connectivity of the MDP so that only a subset of values that are relevant for a state are considered, an attention module is constructed. This module helps reduce the number of network parameters required to be learned and speeds up the network performance. 

The resultant values obtained as an output from the attention module are then added as additional features to the original reactive policy to produce a general optimal policy for the original MDP. Thus, the new MDP is learned, solved, and then used to improve the learning process for solving the original MDP iteratively. Finally, the authors evaluate the generalizability of VIN on the Grid-world, Mars Rover navigation, continuous control, and webnav challenge domains.


**Limitations:**

- The proposed VIN performs value iteration over the entire state space. Thus, it is required that the value vector is not too large. The paper does mention Hierarchical VIN but the notion of using abstraction in VIN to handle complex real-world tasks with large state spaces has not been explored enough. This makes VIN limited in the complexity of tasks that can be solved effectively. 
- The paper uses only 2-dimensional domains to evaluate the VIN architecture. Further research needs to be conducted on the neural network architectures for handling multi-dimensional domains. 
- The loss function used to compute gradients is not specified at all.
 

**Strengths:**

- I like the idea of combining value iteration due to their success in sequential decision-making with neural network architectures for their success in unsupervised learning. I think this paves the way for increased unification of deep learning and planning concepts. 
- I also liked that this paper explored the generalizability of learned policies.  


**Random Questions**
Answers: We’re learning the reward and transition functions for the original MDP. 
Questions: How is this architecture helpful compared to the VI formula? combining VI+RL? also, does the VI module process a single state at a time or all at once?
What is the significance of the new MDP constructed?? How can this approach be compared with RL? Is it even correct to say that this approach is performing RL?
