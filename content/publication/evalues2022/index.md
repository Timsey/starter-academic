---
title: "E-Valuating Classifier Two-Sample Tests"

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here 
# and it will be replaced with their full name and linked to their profile.
authors:
- Teodora Pandeva
- admin
- Christian A. Naesseth
- Patrick Forre

# Author notes (optional)
#author_notes:
#- "Equal contribution"
#- "Equal contribution"

date: "2022-10-24"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: ""

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: Under submission at AISTATS 2023.
publication_short:

abstract: We propose E-C2ST, a classifier two-sample test for high-dimensional data based on E-values. Compared to p-values-based tests, tests with E-values have finite sample guarantees for the type I error. E-C2ST combines ideas from existing work on split likelihood ratio tests and predictive independence testing. The resulting E-values incorporate information about the alternative hypothesis. We demonstrate the utility of E-C2ST on simulated and real-life data. In all experiments, we observe that when going from small to large sample sizes, as expected, E-C2ST starts with lower power compared to other methods but eventually converges towards one. Simultaneously, E-C2ST's type I error stays substantially below the chosen significance level, which is not always the case for the baseline methods. Finally, we use an MRI dataset to demonstrate that multiplying E-values from multiple independently conducted studies leads to a combined E-value that retains the finite sample type I error guarantees while increasing the power.

# Summary. An optional shortened abstract.
summary: We propose an E-values based classifier two-sample test that has much stronger finite-sample type-I error control than existing methods.

tags: 
- Hypothesis testing
- E-values

# Display this page in the Featured widget?
featured: false

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: 'https://arxiv.org/pdf/2210.13027.pdf'
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
  caption: ''
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
