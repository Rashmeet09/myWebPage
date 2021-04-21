---
title: 'Heuristic Search Planner 2.0'
subtitle: 'The paper tackles the challenge of developing a general platform for experimenting with the choice of state-space search strategy, search algorithm, and heuristics when solving planning problems. The proposed heuristic search planner implements the family of heuristic search planners, and offers both optimal and near-optimal solution-finding capabilities.'
summary: ''
authors:
- admin
tags:
- Planning
categories:
- Paper critiques
date: "2021-01-22T00:00:00Z"
lastmod: "2021-01-22T00:00:00Z"
featured: false
draft: false

external_link: https://ojs.aaai.org/index.php/aimagazine/article/download/1576/1475/0

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

The paper tackles the challenge of developing a general platform for experimenting with the choice of state-space search strategy, search algorithm, and heuristics when solving planning problems. The proposed heuristic search planner implements the family of heuristic search planners, and offers both optimal and near-optimal solution-finding capabilities.  


**Why is that a problem worth solving?**

The existing planners cope with solving planning problems by mapping them into search problems with suitable state-space and extracting heuristics. However, their performance varies across different domains as they use different search strategies and compute heuristics distinctly. There is a need for thoroughly experimenting with these different variants of search algorithms and combinations of search strategies and heuristics on several domains. To this end, it is essential to create a generalized platform that offers the ability to investigate different configurations of heuristic search planners on several domains. 
                                                                                                                     
                                                                                            
**Approach:**


The authors propose a general heuristic search planner that currently implements WA* algorithm, inputs user-specification about search strategy (progression or regression), heuristics (nonadmissible hadd, admissible hmax, and admissible h2) and W parameter to try out several combinations of planner characteristics. The paper discusses algorithms for computing hadd and hmax heuristics and states reasons for the inadmissibility of hadd. It also describes the computation of a more informative h2 heuristic that takes in either m=1 or m=2 to approximate the cost for achieving a set of atoms C from a state s by the cost of m most costly atoms in C using a Belman-Ford type of algorithm. 

The proposed planner provides several options such as (i) forward with hadd, (ii) backward with hadd, (iii) backward with h2, etc. that can be run concurrently. If the planner fails to find a solution within a stipulated time, it can continue to run the default forward with the hadd option. Such a systematic algorithm allows generating optimal and approximately optimal solutions for different settings. The different settings especially in the use of the W parameter enable to achieve the desired optimality and speed trade-off in planning. 


**Limitations:**

- The paper does not state the reasons or justify the choice of the search algorithm used in HSP 2.0. It implements a single search algorithm WA* and does not shed light on how easy and efficient it will be to integrate other existing heuristic search algorithms with the planner. 
- The authors did not specify all the domains that they experimented with. 
- A close look at the results shows that HSP performed comparatively or better on most of the problems compared to STAN and BLACKBOX except the problem 10-1. However, possible reasons for such large degradation in the quality of the solution are not reported.
 

**Strengths:**

- I like that the proposed planner allows a user to not only experiment with different planner characteristics but also enables to achieve a desired quality of solutions. Often, the optimality of solutions is not as important as finding approximately optimal solutions fast. In such cases, the planner provides a good suite of configurations to experiment with. 
- I found the authors’ analysis about forward/progression search being more robust than backward/regression search strategy interesting. This insight aids in the choice to continue with the forward and the hadd option if other promising options fail to find a solution within a fixed amount of time.
