---
title: "Differential Assessment of Black-Box AI Agents"
authors:
- Rashmeet Kaur Nayyar
- Pulkit Verma
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
publication: In *The Thirty-Sixth AAAI Conference on Artificial Intelligence, 2022*
publication_short: In *AAAI, 2022*

abstract: "Much  of  the  research  on  learning  symbolic  models  of  AIagents  focuses  on  agents  with  stationary  models.  This  as-sumption  fails  to  hold  in  settings  where  the  agent’s  capa-bilities  may  change  as  a  result  of  learning,  adaptation,  orother post-deployment modifications. Efficient assessment ofagents in such settings is critical for learning the true capabil-ities of an AI system and for ensuring its safe usage. In thiswork,  we  propose  a  novel  approach  todifferentiallyassessblack-box AI agents that have drifted from their previouslyknown models. As a starting point, we consider the fully ob-servable and deterministic setting. We leverage sparse obser-vations  of  the  drifted  agent’s  current  behavior  and  knowl-edge of its initial model to generate an active querying pol-icy  that  selectively  queries  the  agent  and  computes  an  up-dated model of its functionality. Empirical evaluation showsthat our approach is much more efficient than re-learning theagent model from scratch. We also show that the cost of dif-ferential assessment using our method is proportional to theamount of drift in the agent’s functionality."

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