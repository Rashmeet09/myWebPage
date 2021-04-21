---
title: 'Mastering the game of Go without human knowledge '
subtitle: 'The problem of developing a pure reinforcement learning approach (i.e. without the use of any domain knowledge beyond basic game rules) for the game of Go has been addressed.'
summary: ''
authors:
- admin
tags:
- RL
- MCTS
categories:
- Paper critiques
date: "2021-03-18T00:00:00Z"
lastmod: "2021-03-18T00:00:00Z"
featured: false
draft: false

external_link: https://deepmind.com/research/publications/mastering-game-go-without-human-knowledge

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

The problem of developing a pure reinforcement learning approach (i.e. without the use of any domain knowledge beyond basic game rules) for the game of Go has been addressed.

**Why is that a problem worth solving?**

AlphaGo Fan and AlphaGo Lee successfully outperformed the best players of the game of Go in recent years. A limitation of these approaches is that they require extensive knowledge of human expert moves. It can be difficult, or even infeasible, to obtain such data sets for many real-world problems. An approach that learns purely through self-play achieving stable and faster learning would be a huge step in overcoming these limitations. Such an approach would pave the way for solving many real-world games whose datasets are not readily available.  
                                                                                    
                                                                                            
**Approach:**

The proposed approach called AlphaGo Zero (a tabula rasa algorithm) has a single neural network that acts as both a policy network (outputs action probabilities) as well as a value network (outputs action values) as opposed to two separate networks in AlphaGo. It merely uses the positions of white and black stones on the board as input features and basic game rules as domain knowledge without any requirement of human expert moves. 

Given neural network parameters and the current state of the game, Monte-Carlo Tree Search (MCTS) computes a vector of search probabilities and recommends moves to play. In other words, the trained neural network is used to guide MCTS to select the most promising moves. These moves are then used by the neural network to self-play and find the game-winner. The network parameters are updated to maximize the similarity of the neural network’s action probabilities to the search probabilities and to minimize the error between the predicted value and the self-play winner. Thus, the approach represents repeated self-play or a policy iteration procedure with MCTS (without rollouts) improving the policy and the neural network self-play evaluating the policy.

Finally, the authors explain the architecture in detail and suggest through their extensive empirical evaluation of pure RL AlphaGo Zero with previous supervised learning approaches that pure RL can achieve higher move prediction accuracies, learn faster with more stability, and discover novel game strategies. 


**Limitations:**

- The paper uses simulations that exactly emulate a real game of Go. It will be interesting to see how it performs for games with partial or noisy observations.
- The game Go is also fully deterministic. Hence, Go isn’t the most challenging game to claim that pure reinforcement learning is fully feasible for real-world domains. 
- Although labels are being learnt and used to improve the network (closer to supervised learning), that perspective has not been mentioned. Policy iteration has been used which is not RL. But reward function and transition function have not been provided, it’s RL. So its RL + Search (MCTS)
 

**Strengths:**

- I like how the neural network and MCTS are combined in an elegant policy iteration framework to achieve stable learning. 
- The proposed approach eliminates the need for rollouts by using the neural network to evaluate positions. It also uses a single network and doesn’t require any human expert knowledge except for basic game rules. 
- The most notable result that struck out to me is that AlphaGo Zero not only learned existing human knowledge on its own but also discovered novel creative strategies. 