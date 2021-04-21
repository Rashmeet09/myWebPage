---
title: 'Point-based value iteration: An anytime algorithm for POMDPs'
subtitle: 'The paper addresses the problem of solving large partially observable Markov decision processes (POMDPs) in an anytime manner.'
summary: ''
authors:
- admin
tags:
- POMDPs
categories:
- Paper critiques
date: "2021-03-03T00:00:00Z"
lastmod: "2021-03-043T00:00:00Z"
featured: false
draft: false

external_link: http://www.cs.cmu.edu/~ggordon/jpineau-ggordon-thrun.ijcai03.pdf

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

The paper addresses the problem of solving large partially observable Markov decision processes (POMDPs) in an anytime manner.

**Why is that a problem worth solving?**

Most of the real-world problems can be represented as POMDPs and are intractable due to the curse of dimensionality and the curse of history. The current algorithms used for solving POMDPs exactly including value iteration can not scale well to large real-world problems due to an exponential increase in the time complexity. We need POMDP algorithms that can increase the scope of solvable real-world problems (even if approximately) and generalize better to unexplored beliefs using fewer belief points compared to other approximate algorithms.
                                                                                                                    
                                                                                            
**Approach:**

The authors propose an anytime Point-based Value Iteration (PBVI) algorithm for solving POMDPs approximately. 

The method acknowledges that reaching most of the belief points in the space is unlikely due to the sheer size of the state space. It focuses on avoiding the curse of history by selecting a small set of representative belief points from explorative stochastic trajectories. Thus, it concentrates planning on a fixed size of the most probable (hence, the most relevant) beliefs. 

It then iteratively applies value updates, maintains a value hyper-plane, and finds the best action for each belief point. These hyperplanes are piece-wise linear and convex. After h value backups for problems with a finite horizon h, the set of belief points is expanded by adding one new belief from each previous belief which is farthest away from any point already in the set. Thus, the belief set size at most doubles on each expansion. By interleaving VI with belief set expansion, PBVI achieves an anytime behavior and finds a trade-off between the computation time and the solution quality. The paper provides stronger theoretical guarantees on convergence and error bounds. 

Empirical evaluation on the Tag domain suggests that PBVI is able to solve POMDP problems an order of magnitude larger than the problems currently solved in the literature. Its performance is also competitive with QMDP on three well-known POMDPs i.e. Maze33, Hallway, and Hallway2 in terms of goal completion rates, the sum of rewards, policy computation time, and the number of required beliefs. PBVI requires fewer samples for all the domains. PBVI's expansion heuristic also performs the best compared to other belief set expansion methods.


**Limitations:**

- The proposed approach fails to account for the rare highly undesirable events, and thus can not model scenarios that may have catastrophic events.
- The authors do not shed light on how the size of the belief set can be decided.
- The size of the bounded region for each belief point that affects its value function vector needs to be decided. The cost of updating these value function vectors can be increasingly high as the number of states increases. 
- Not that good for sparse domains as it can throw away useful actions. That ends up having to do a lot of reward shaping. 
 

**Strengths:**

- I like that the size of the value function remains constant as it eliminates the need for pruning away value functions, which is generally required when using exact POMDP algorithms. 
- I also like the observation that PBVI performs best when the set of beliefs contain a high number of reachable belief points.