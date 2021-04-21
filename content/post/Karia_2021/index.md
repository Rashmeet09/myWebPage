---
title: 'Learning generalized relational heuristic networks for model-agnostic planning'
subtitle: 'This paper proposes a deep learning approach to learn generalized heuristic generation functions (HGFs) that can scale well to unseen problems with different object names and quantities without the use of symbolic action models.'
summary: ''
authors:
- admin
tags:
- Planning
categories:
- Paper critiques
date: "2021-02-05T00:00:00Z"
lastmod: "2021-02-05T00:00:00Z"
featured: false
draft: false

external_link: https://arxiv.org/pdf/2007.06702.pdf

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

This paper proposes a deep learning approach to learn generalized heuristic generation functions (HGFs) that can scale well to unseen problems with different object names and quantities without the use of symbolic action models.


**Why is that a problem worth solving?**

The struggle of hand-coding the heuristic generation functions in the past decades has led to research in automated synthesis of heuristics from action models. However, existing approaches are limited in their utility as they still require hand-coded action models, and the learned heuristics functions are restricted to fixed object names and quantities. A model agnostic framework would eliminate the need for domain experts. Moreover, generalizable heuristic generating functions would help solve larger problems and problems with different object names.
                                                                                                                     
                                                                                            
**Approach:**


The paper proposes a Generalized Heuristic Network (GHN) to learn heuristic generation functions (HGF) directly from plans without the use of action models.

The proposed framework takes as input planning trajectories, each containing a sequence of states and parameterized actions, a goal formula, and a set of objects. Goal hints are encoded in each state of a trajectory and the transformed state representations are stored as tuples along with the corresponding action and plan length from the state to the goal. Finally, abstract states for each state are computed using canonical abstraction and embedded into the tuples. These tuples form the training data set for the proposed neural network architectures. A set of predicates, roles, actions, and a maximum number of action parameters are also maintained to determine the dimensions of input and output for the networks. 

The two neural network architectures proposed, namely Action Network and Plan Length Network have different goals. One aims at predicting action probability and a set of roles for action parameters, and the other aims at estimating the plan length. The action network uses absolute inputs as they capture the number of objects in a role aiding in the prediction of the plan length, whereas, the plan network uses binned inputs. The authors also use leapfrogging in case of insufficient training data. Finally, they evaluate searching using GHNs against hand-coded HGFs on 13 benchmark domains.


**Limitations:**

* The proposed formulation currently assumes the presence of unary and binary predicates. It also requires compiling the types of objects as unary predicates. However, possible reasons for such requirement to obtain good performance are not stated. A deeper analysis of why higher arity domains perform poorly using canonical abstraction is required. 
* How the set of predicates, roles, actions, and the maximum number of action parameters affect the input-output dimensions of the proposed architectures is not explained.
* Reasons for choice of loss minimization functions for each layer in the architecture is lacking.
* Although the paper focuses on satisficing planning, it lacks an analysis of how suboptimal the plans found by GHN are.
* In my opinion, the proposed approach sections especially on the network architecture needed better and more complete explanations. 
* Even though there is a language difference between the implementations of competition planners (C/C++) and the proposed approach (python), a direct comparison of the average times for both as shown in the plots in spite of the implementation difference is unclear.
 

**Strengths:**

* I like the analysis of the proposed architecture on the spanner domain to understand how well it learns the structure of the problem compared to the competition planners.
* I also like that the approach has soundness and completeness guarantees. 
* In the absence of experts who can design domains, this approach is fruitful. 
* I found the observation concerning a higher network loss for GHN in case of actions affecting only binary predicates insightful. 
