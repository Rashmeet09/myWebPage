---
title: "Learning Context-Sensitive State and Action Abstractions for Reinforcement Learning with Parameterized Actions"
authors:
- Rashmeet Kaur Nayyar
- Naman Shah
- Siddharth Srivastava
date: "2025-02-17T00:00:00Z"
# doi: "10.48550/arXiv.2210.01955"
# Schedule page publish date (NOT publication's date).
publishDate: "2025-02-17T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *RLC Workshop on Finding the Frame, 2025*
publication_short: In *RLC, 2025*

abstract: "Real-world sequential decision making problems often require parameterized action spaces that feature both, decisions regarding discrete actions and decisions about continuous action parameters governing how an action is executed. However, existing approaches exhibit severe limitations when handling such parameterized action spaces---planning algorithms require hand-crafted action models, and reinforcement learning (RL) paradigms focus on either discrete or continuous actions but not both. This paper extends the scope of RL algorithms to settings with mixtures of discrete and continuous parameterized actions through a unified view of continuous-to-discrete context-sensitive state and action abstractions. We present algorithms for online learning and flexible refinement of such abstractions during RL. Empirical results show that learning such abstractions on-the-fly enable Q-learning to significantly outperform state-of-the-art RL approaches in terms of sample efficiency across diverse problem domains with long horizons, continuous states and parameterized actions."

# Summary. An optional shortened abstract.
summary: 

# tags:
# - Source Themes
featured: false

links:
- name: Link
  url: https://openreview.net/pdf?id=PFYJbUFYZW
url_pdf: https://openreview.net/pdf?id=PFYJbUFYZW
#url_code: '#'
#url_dataset: '#'
# url_poster: 'https://drive.google.com/file/d/1DT8KkyJeq5DB8ondSvQ5m9RCspVUZRkL/view'
#url_project: ''
#url_slides: ''
#url_source: '#'
#url_video: '#'

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: ''
  focal_point: ""
  preview_only: true

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
# projects:
# - internal-project

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
# slides: example
---

<!-- {{% alert note %}}
Click the *Cite* button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /alert %}}

{{% alert note %}}
Click the *Slides* button above to demo Academic's Markdown slides feature.
{{% /alert %}}

Supplementary notes can be added here, including [code and math](https://sourcethemes.com/academic/docs/writing-markdown-latex/). -->