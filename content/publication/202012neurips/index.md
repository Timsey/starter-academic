---
title: "Experimental design for MRI by greedy policy search"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- admin
- Herke van Hoof
- Max Welling

# Author notes (optional)
#author_notes:
#- "Equal contribution"
#- "Equal contribution"

date: "2020-12-06"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: ""

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *Advances in Neural Information Processing Systems 33 (NeurIPS, 2020)*
publication_short: NeurIPS 2020, **Spotlight**

abstract: In today’s clinical practice, magnetic resonance imaging (MRI) is routinely accelerated through subsampling of the associated Fourier domain. Currently, the construction of these subsampling strategies - known as experimental design - relies primarily on heuristics. We propose to learn experimental design strategies for accelerated MRI with policy gradient methods. Unexpectedly, our experiments show that a simple greedy approximation of the objective leads to solutions nearly on-par with the more general non-greedy approach. We offer a partial explanation for this phenomenon rooted in greater variance in the non-greedy objective’s gradient estimates, and experimentally verify that this variance hampers non-greedy models in adapting their policies to individual MR images. We empirically show that this adaptivity is key to improving subsampling designs.

# Summary. An optional shortened abstract.
summary: We use policy gradient methods to learn active acquisition policies for improving MRI reconstruction.

tags: 
- Active sensing
- Medical imaging (MRI)
- Reinforcement learning

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: 'https://proceedings.neurips.cc/paper/2020/hash/daed210307f1dbc6f1dd9551408d999f-Abstract.html'
url_code: 'https://github.com/Timsey/pg_mri'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: 'https://videos.neurips.cc/search/experimental%20design/video/slideslive-38938021'
url_source: ''
url_video: 'https://videos.neurips.cc/search/experimental%20design/video/slideslive-38938021'

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'MRI experimental design'
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
