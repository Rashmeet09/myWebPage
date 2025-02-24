---
title: "Autonomous Option Invention for Continual Hierarchical Reinforcement Learning and Planning"
authors:
- Rashmeet Kaur Nayyar
- Siddharth Srivastava
date: "2025-02-17T00:00:00Z"
doi: "10.48550/arXiv.2412.16395"
# Schedule page publish date (NOT publication's date).
publishDate: "2025-02-17T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *The Thirty-Ninth AAAI Conference on Artificial Intelligence, 2025*
publication_short: In *AAAI, 2025*

abstract: "Abstraction is key to scaling up reinforcement learning (RL). However, autonomously learning abstract state and action representations to enable transfer and generalization remains a challenging open problem. This paper presents a novel approach for inventing, representing, and utilizing options, which represent temporally extended behaviors, in continual RL settings. Our approach addresses streams of stochastic problems characterized by long horizons, sparse rewards, and unknown transition and reward functions. 

Our approach continually learns and maintains an interpretable state abstraction, and uses it to invent high-level options with abstract symbolic representations. These options meet three key desiderata: (1) composability for solving tasks effectively with lookahead planning, (2) reusability across problem instances for minimizing the need for relearning, and (3) mutual independence for reducing interference among options. Our main contributions are approaches for continually learning transferable, generalizable options with symbolic representations, and for integrating search techniques with RL to efficiently plan over these learned options to solve new problems. Empirical results demonstrate that the resulting approach effectively learns and transfers abstract knowledge across problem instances, achieving superior sample efficiency compared to state-of-the-art methods."

# Summary. An optional shortened abstract.
summary: 

# tags:
# - Source Themes
featured: false

links:
- name: Link
  url: https://aair-lab.github.io/Publications/rkn_aaai25.pdf
url_pdf: https://aair-lab.github.io/Publications/rkn_aaai25.pdf
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