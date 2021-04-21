---
title: 'Learning Domain-Independent Planning Heuristics with Hypergraph Networks'
subtitle: 'The authors address developing a framework to learn generalized domain-independent heuristics for planning without using any available heuristics. The goal is to learn heuristics that can generalize not only across problem instances of different sizes, states, and goals but also across unseen domains.'
summary: ''
authors:
- admin
tags:
- Planning
categories:
- Paper critiques
date: "2021-01-29T00:00:00Z"
lastmod: "2021-01-29T00:00:00Z"
featured: false
draft: false

external_link: https://arxiv.org/pdf/1911.13101.pdf

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

The authors address developing a framework to learn generalized domain-independent heuristics for planning without using any available heuristics. The goal is to learn heuristics that can generalize not only across problem instances of different sizes, states, and goals but also across unseen domains.


**Why is that a problem worth solving?**

More often, existing heuristics are improved or combined for learning domain-independent heuristics, and there aren’t any approaches available to learn such heuristics entirely from scratch. Producing high-quality heuristics that can generalize across different unseen domains and problem sizes is significant because it increases the scope of the problem instances that can be solved by large without having the recompute heuristics for those problems.


                                                                                                                     
                                                                                            
**Approach:**


- The paper approaches the problem of learning heuristics that are independent of domains by reformulating the problem as learning a mapping from a hypergraph representation induced by the delete-relaxed planning problem to a heuristic estimate. The authors propose generalized Graph Networks for hypergraphs called as Hypergraph Networks (HGNs) to achieve this as they enable message propagation over the structures. 
- They explain that the core building block of HGN serves as a hypergraph-to-hypergraph function and constitutes a fixed number of update and aggregate functions. These functions are then used to update latent representations of hypergraph input attributes and integrate all the features respectively. They instantiate and compose several HGNs sequentially and repeatedly to generate a STRIPS-HGN architecture containing recurrent encode-process-decode layers aimed at learning heuristics. The number of recurrent layers determines the number of message passing steps making the size of receptive fields flexible.
- The proposed architecture allows learning richer representations of input features and producing generalized heuristic estimates.


**Limitations:**

- The authors talk about the evident advantage of the flexible size of receptive fields in the proposed architecture, however, evaluation of the effect of scaling the number of recurrent layers is limited (they only mention the setting that worked for them). 
- The use of a neural network approach limits our understanding of what the model is really computing/learning as the current research is not advanced enough to analyze that. 
- Another significant limitation of the proposed approach is that even though the architecture is trained on accurate heuristic values, the model often learns non-admissible heuristics leading to the computation of sub-optimal policies. 
- There aren't any theoretical guarantees on the quality of the heuristics learned.
 

**Strengths:**

- I like that the proposed architecture of STRIPS_HGN is agnostic to the way update functions are implemented which makes them quite flexible. 
- Their generalizability to unseen domains and object sets in problems as well as their adaptability to different input features struck out to me the most. 