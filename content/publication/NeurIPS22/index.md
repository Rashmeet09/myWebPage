---
title: "Learning Generalized Policy Automata for Relational Stochastic Shortest Path Problems"
authors:
- Rushang Karia
- Rashmeet Kaur Nayyar
- Siddharth Srivastava
date: "2022-03-24T00:00:00Z"
doi: "10.48550/arXiv.2203.13236"
# Schedule page publish date (NOT publication's date).
publishDate: "2022-03-24T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *The Conference on Neural Information Processing Systems, 2022*
publication_short: In *NeurIPS, 2022*

abstract: "Several  goal-oriented  problems  in  the  real-worldcan  be  naturally  expressed  as  Stochastic  ShortestPath Problems (SSPs). However,  the  computa-tional  complexity  of  solving  SSPs  makes  findingsolutions  to  even  moderately  sized  problems  in-tractable.  Currently, existing state-of-the-art plan-ners and heuristics often fail to exploit knowledgelearned  from  solving  other  instances.   This  paperpresents an approach for learningGeneralized Pol-icy Automata(GPA): non-deterministic partial poli-cies that can be used to catalyze the solution pro-cess.   GPAs  are  learned  using  relational,  feature-based  abstractions,  which  makes  them  applicableon broad classes of related problems with differentobject names and quantities.  Theoretical analysisof this approach shows that it guarantees complete-ness and hierarchical optimality.  Our experimentsshow that this approach effectively learns broadlyapplicable policy knowledge in a few-shot fashionand  significantly  outperforms  state-of-the-art  SSPsolvers  on  test  problems  whose  object  counts  arefar greater than those used during training."

# Summary. An optional shortened abstract.
summary: 

# tags:
# - Source Themes
featured: false

links:
- name: Link
  url: https://ojs.aaai.org/index.php/AAAI/article/download/21223/version/19510/20972
#url_pdf: http://eprints.soton.ac.uk/352095/1/Cushen-IMV2013.pdf
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
  preview_only: false

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