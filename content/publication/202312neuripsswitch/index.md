---
title: "Switching policies for solving inverse problems"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- admin
- Fabio Valerio Massoli
- Thomas Hehn
- Tribhuvanesh Orekondy
- Arash Behboodi

# Author notes (optional)
#author_notes:
#- "Equal contribution"
#- "Equal contribution"

date: "2023-10-27"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: ""

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: Accepted paper at *NeurIPS Workshop on Deep Learning and Inverse Problems (NeurIPS Deep Inverse Workshop, 2023)*.
publication_short: NeurIPS Deep Inverse Workshop 2023

abstract: In recent years, inverse problems for black-box simulators have enjoyed increased focus of the machine learning community due to their prevalence in science and engineering domains. Such simulators describe a forward process f (\psi, x) \rightarrow y. Here the intent is to optimise simulator parameters \psi to minimise some observation loss on y, under some input distribution on x. Optimisation of such objectives is often challenging, since it is not trivial to estimate simulator gradients accurately. In settings where multiple related inverse problems need to be solved simultaneously, from-scratch/ab-initio optimisation of each may be infeasible if the forward model is expensive to evaluate. In this paper, we propose a novel method for solving such families of inverse problems with reinforcement learning. We train a policy to guide the optimisation by selecting between gradients estimated numerically from the simulator and gradients estimated from a pre-trained surrogate model. After training the surrogate and the policy, downstream inverse problem optimisations require 10%-70% fewer simulator evaluations. Moreover, the policy does successful optimisations on functions where using just simulator gradient estimates fails.


# Summary. An optional shortened abstract.
summary: We propose to learn a switching policy for inverse problem optimisation.

tags: 
- Surrogate models
- Reinforcement learning
- Inverse problems

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: 'https://openreview.net/forum?id=QaIEU0wWj8'
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Optimising the ThreeHump problem.'
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []
#- example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: []  
#example
---
