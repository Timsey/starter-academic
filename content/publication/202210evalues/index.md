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
publication: Preprint
publication_short:

abstract: We propose E-C2ST, a deep classifier two-sample test for high-dimensional data based on E-values. Unlike the more standard p-value based tests, E-value based tests have *finite sample* type I error guarantees, making them appropriate tools for statistical testing in practice. Our proposed E-C2ST combines ideas from existing work on split likelihood ratio tests and predictive independence testing. The resulting E-values can be used for both standard statistical testing on a fixed data set as well as anytime testing in streaming data settings. We demonstrate the utility of E-C2ST on simulated and real data. In all experiments, we observe that -- as expected -- E-C2ST's type I error stays substantially below the chosen significance level, while the p-value based baseline methods regularly fail to control for type I error appropriately. While E-C2ST has reduced power compared to the baseline methods, power empirically converges to one as dataset size increases in most settings. We further propose an adjusted $\Ev$-value based test in the anytime testing framework that has increased power, while still retaining the finite sample type I error guarantees.

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
