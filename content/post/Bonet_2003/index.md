---
title: 'Labeled RTDP: Improving the Convergence of Real-Time Dynamic Programming'
subtitle: 'The paper addresses the problem of speeding up the final convergence of RTDP, a heuristic search-DP algorithm to produce optimal policies for fully observable non-deterministic (more specifically, stochastic shortest path) problems faster compared to the existing search algorithms.'
summary: ''
authors:
- admin
tags:
- Planning
categories:
- Paper critiques
date: "2021-02-12T00:00:00Z"
lastmod: "2021-02-12T00:00:00Z"
featured: false
draft: false

external_link: https://ftp.cs.ucla.edu/pub/stat_ser/R319.pdf

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

The paper addresses the problem of speeding up the final convergence of RTDP, a heuristic search-DP algorithm to produce optimal policies for fully observable non-deterministic (more specifically, stochastic shortest path) problems faster compared to the existing search algorithms.


**Why is that a problem worth solving?**

DP algorithms such as Value Iteration and Policy Iteration have to evaluate the entire state space to produce an optimal policy which makes them time-consuming. A heuristic search-DP algorithm called RTDP focuses on reduced state space and produces sub-optimal policies fast through simulated greedy search trials of the state space, but the final convergence is extremely slow. Another such algorithm, LAO* does not have an anytime behavior. To this end, it is essential to research methods that can produce optimal policies orders of magnitude faster than the existing algorithms, while retaining a focused and anytime behavior. 
                                                                                                                     
                                                                                            
**Approach:**


The paper proposes to introduce a labeling scheme into the existing RTDP algorithm to speed up its final convergence and calls it Labeled RTDP.  The RTDP algorithm favors the states with a higher probability of reaching (more relevant states) over the less likely states. However, the less likely states are required to be sampled during the greedy simulations to achieve convergence. Instead of forcing the likely states to be sampled, the authors propose to label the states whose values have converged and avoid visiting them during the trials thereafter. 

To identify such converged states and mark them as solved, the proposed approach finds a greedy envelope for each state s which contains all the states in the greedy policy from the state s obtained from the current value function. If any state with a residual greater than epsilon is found in the envelope, the values for that state and other states above it in the envelope are updated, else the state s is marked as solved. Marked states are avoided for expansion in the further trials and less likely states are sampled thereafter with a higher probability, leading to faster final convergence.

The authors compare the proposed LRTDP algorithm with RTDP, improved LAO*, and value iteration (with different heuristic functions such as h=0 and h_min) and assess their anytime and convergence behavior. 


**Limitations:**

- The computation time for h_min is so large that LRTDP+hmin does not outperform VI+h=0 but only remains competitive in spite of LRTDP’s labeling scheme and focused behavior. In fact, LRTDP+hmin often takes the same time as LRTDP+h=0 (includes heuristic computation time) which indicates that one may prefer using LRTDP without a heuristic to avoid the heuristic computation overhead. Thus, methods for faster computation of such heuristics will bring out significant speedups when using LRTDP. 

- LRTDP does not utilize improved heuristics as much as LAO* does. In other words, LRTDP’s benefits are majorly derived from its labeling scheme and a focussed behavior, and improved heuristics do not help LRTDP as much as it helps LAO*. This is because, in LAO*, heuristics help to prune out some states entirely from consideration, while in LRTDP, heuristics help faster convergence of states but do not prune them away to avoid their expansion. 

- The problem of lower probability transitions not getting sampled persists until the states in other transitions are marked as solved. Further modifications in the labeling procedure to account for these probabilities can be researched.
 

**Strengths:**

- I like that LRTDP outperforms value iteration and even LAO* in terms of convergence even in the absence of an informative heuristic function. This is because LRTDP’s focussed behavior helps it to learn good estimates of heuristic values. 

- The anytime behavior of LRTDP has significant advantages as it delivers good optimal policies fast and continues to explore the state space to eventually deliver an optimal policy. It also wins in terms of the final convergence which makes the algorithm desirable to use. 


<!-- **Create a free website with Academic using Markdown, Jupyter, or RStudio. Choose a beautiful color theme and build anything with the Page Builder - over 40 _widgets_, _themes_, and _language packs_ included!**

[Check out the latest **demo**](https://academic-demo.netlify.com/) of what you'll get in less than 10 minutes, or [view the **showcase**](https://sourcethemes.com/academic/#expo) of personal, project, and business sites.

- 👉 [**Get Started**](#install)
- 📚 [View the **documentation**](https://sourcethemes.com/academic/docs/)
- 💬 [**Ask a question** on the forum](https://discourse.gohugo.io)
- 👥 [Chat with the **community**](https://spectrum.chat/academic)
- 🐦 Twitter: [@source_themes](https://twitter.com/source_themes) [@GeorgeCushen](https://twitter.com/GeorgeCushen) [#MadeWithAcademic](https://twitter.com/search?q=%23MadeWithAcademic&src=typd)
- 💡 [Request a **feature** or report a **bug**](https://github.com/gcushen/hugo-academic/issues)
- ⬆️ **Updating?** View the [Update Guide](https://sourcethemes.com/academic/docs/update/) and [Release Notes](https://sourcethemes.com/academic/updates/)
- :heart: **Support development** of Academic:
  - ☕️ [**Donate a coffee**](https://paypal.me/cushen)
  - 💵 [Become a backer on **Patreon**](https://www.patreon.com/cushen)
  - 🖼️ [Decorate your laptop or journal with an Academic **sticker**](https://www.redbubble.com/people/neutreno/works/34387919-academic)
  - 👕 [Wear the **T-shirt**](https://academic.threadless.com/)
  - :woman_technologist: [**Contribute**](https://sourcethemes.com/academic/docs/contribute/)

{{< figure src="https://raw.githubusercontent.com/gcushen/hugo-academic/master/academic.png" title="Academic is mobile first with a responsive design to ensure that your site looks stunning on every device." >}}

**Key features:**

- **Page builder** - Create *anything* with [**widgets**](https://sourcethemes.com/academic/docs/page-builder/) and [**elements**](https://sourcethemes.com/academic/docs/writing-markdown-latex/)
- **Edit any type of content** - Blog posts, publications, talks, slides, projects, and more!
- **Create content** in [**Markdown**](https://sourcethemes.com/academic/docs/writing-markdown-latex/), [**Jupyter**](https://sourcethemes.com/academic/docs/jupyter/), or [**RStudio**](https://sourcethemes.com/academic/docs/install/#install-with-rstudio)
- **Plugin System** - Fully customizable [**color** and **font themes**](https://sourcethemes.com/academic/themes/)
- **Display Code and Math** - Code highlighting and [LaTeX math](https://en.wikibooks.org/wiki/LaTeX/Mathematics) supported
- **Integrations** - [Google Analytics](https://analytics.google.com), [Disqus commenting](https://disqus.com), Maps, Contact Forms, and more!
- **Beautiful Site** - Simple and refreshing one page design
- **Industry-Leading SEO** - Help get your website found on search engines and social media
- **Media Galleries** - Display your images and videos with captions in a customizable gallery
- **Mobile Friendly** - Look amazing on every screen with a mobile friendly version of your site
- **Multi-language** - 15+ language packs including English, 中文, and Português
- **Multi-user** - Each author gets their own profile page
- **Privacy Pack** - Assists with GDPR
- **Stand Out** - Bring your site to life with animation, parallax backgrounds, and scroll effects
- **One-Click Deployment** - No servers. No databases. Only files.

## Themes

Academic comes with **automatic day (light) and night (dark) mode** built-in. Alternatively, visitors can  choose their preferred mode - click the sun/moon icon in the top right of the [Demo](https://academic-demo.netlify.com/) to see it in action! Day/night mode can also be disabled by the site admin in `params.toml`.

[Choose a stunning **theme** and **font**](https://sourcethemes.com/academic/themes/) for your site. Themes are fully [customizable](https://sourcethemes.com/academic/docs/customization/#custom-theme).

## Ecosystem

* **[Academic Admin](https://github.com/sourcethemes/academic-admin):** An admin tool to import publications from BibTeX or import assets for an offline site
* **[Academic Scripts](https://github.com/sourcethemes/academic-scripts):** Scripts to help migrate content to new versions of Academic

## Install

You can choose from one of the following four methods to install:

* [**one-click install using your web browser (recommended)**](https://sourcethemes.com/academic/docs/install/#install-with-web-browser)
* [install on your computer using **Git** with the Command Prompt/Terminal app](https://sourcethemes.com/academic/docs/install/#install-with-git)
* [install on your computer by downloading the **ZIP files**](https://sourcethemes.com/academic/docs/install/#install-with-zip)
* [install on your computer with **RStudio**](https://sourcethemes.com/academic/docs/install/#install-with-rstudio)

Then [personalize and deploy your new site](https://sourcethemes.com/academic/docs/get-started/).

## Updating

[View the Update Guide](https://sourcethemes.com/academic/docs/update/).

Feel free to *star* the project on [Github](https://github.com/gcushen/hugo-academic/) to help keep track of [updates](https://sourcethemes.com/academic/updates).

## License

Copyright 2016-present [George Cushen](https://georgecushen.com).

Released under the [MIT](https://github.com/gcushen/hugo-academic/blob/master/LICENSE.md) license. -->
