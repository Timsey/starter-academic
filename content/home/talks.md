---
# An instance of the Pages widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: pages

active: true

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 20

title: 'Talks and media appearances'

content:
  # Page type to display. E.g. post, event, publication...
  page_type: event
  # Choose how many pages you would like to display (0 = all pages)
  count: 5

  # Filter on criteria
  filters:
    author: ""
    category: ""
    tag: ""
    exclude_featured: false
    exclude_future: false
    exclude_past: false
    publication_type: ""
  # Choose how many pages you would like to offset by
  offset: 0
  # Page order: descending (desc) or ascending (asc) date.
  order: desc

design:
  # Choose a view for the listings:
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   4 = Citation (publication only)
  view: 2
---



@inproceedings{bakker2023active,
  title={{Active Learning Policies for Solving Inverse Problems}},
  author={T. Bakker and T. Hehn and T. Orekondy and A. Behboodi and F. Valerio Massoli},
  booktitle={Neural Information Processing Systems Workshop on Adaptive Experimental Design and Active Learning in the Real World},
  month={Dec},
  year={2023},
  abbr={NeurIPS ReALML Workshop},
  pdf={https://openreview.net/pdf?id=eLIk3m5C79},
}

@inproceedings{bakker2023switching,
  title={{Switching policies for solving inverse problems}},
  author={T. Bakker and F. Valerio Massoli and T. Hehn and T. Orekondy and A. Behboodi},
  booktitle={Neural Information Processing Systems Workshop on Deep Learning and Inverse Problems},
  month={Dec},
  year={2023},
  abbr={NeurIPS Deep Inverse Workshop},
  pdf={https://openreview.net/pdf?id=QaIEU0wWj8},
}
