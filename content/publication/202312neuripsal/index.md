---
title: "Active Learning Policies for Solving Inverse Problems"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- admin
- Thomas Hehn
- Tribhuvanesh Orekondy
- Arash Behboodi
- Fabio Valerio Massoli

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
publication: Accepted paper at *NeurIPS Workshop on Adaptive Experimental Design and Active Learning in the Real World (NeurIPS ReALML Workshop, 2023)*.
publication_short: NeurIPS ReALML Workshop 2023

abstract: In recent years, solving inverse problems for black-box simulators has become a point of focus for the machine learning community due to their ubiquity in science and engineering scenarios. In such settings, the simulator describes a forward process from simulator parameters \psi and input data x to observations y, and the goal of the inverse problem is to optimise \psi to minimise some observation loss. Simulator gradients are often unavailable or prohibitively expensive to obtain, making optimisation of these simulators particularly challenging. Moreover, in many applications, the goal is to solve a family of related inverse problems. Thus, starting optimisation ab-initio/from-scratch may be infeasible if the forward model is expensive to evaluate. In this paper, we propose a novel method for solving classes of similar inverse problems. We learn an active learning policy that guides the training of a surrogate and use the gradients of this surrogate to optimise the simulator parameters with gradient descent. After training the policy, downstream inverse problem optimisations require up to 90% fewer forward model evaluations than the baseline.

# Summary. An optional shortened abstract.
summary: We propose to learn an active learning policy for inverse problem optimisation.

tags: 
- Surrogate models
- Active learning
- Reinforcement learning
- Inverse problems

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: 'https://openreview.net/forum?id=eLIk3m5C79'
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
