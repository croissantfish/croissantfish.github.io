---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2022-10-24
type: landing

sections:
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: me
      text: ''
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      # Use the new Gradient Mesh which automatically adapts to the selected theme colors
      background:
        gradient_mesh:
          enable: true

      # Name heading sizing to accommodate long or short names
      name:
        size: md # Options: xs, sm, md, lg (default), xl

      # Avatar customization
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
  - block: markdown
    content:
      title: '📚 My Research'
      subtitle: ''
      text: |-
        My research lies at the intersection of **spatio-temporal data mining**, **deep learning**, and **urban computing**. I develop intelligent algorithms to model, predict, and understand complex urban phenomena from large-scale sensory and mobility data.

        My recent work focuses on three themes: (1) **spatio-temporal forecasting** — designing efficient neural architectures (e.g., AirFormer, GeoMAN, VQGG) for traffic prediction, air-quality forecasting, and geo-sensory time-series analysis; (2) **automated machine learning for spatio-temporal graphs** — relieving the burden of hand-crafted model design via neural architecture search (AutoSTG / AutoSTG+, EAST) and meta-learning techniques; and (3) **self-supervised representation learning** — learning robust spatio-temporal representations from incomplete or scarce labeled data through masked autoencoders (GeoMAE) and contrastive learning (GSDI, CSST).

        I am also interested in real-world urban applications such as anomaly detection, crowd-flow inference, and purchase prediction. I publish regularly in top-tier venues including *AAAI*, *WWW*, *IJCAI*, *IEEE TKDE*, *Artificial Intelligence*, *Neural Networks*, and *CIKM*. I am always open to collaborations on urban intelligence and spatio-temporal AI — feel free to reach out! 😃
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: Recent Publications
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation
  - block: collection
    id: talks
    content:
      title: Recent & Upcoming Talks
      filters:
        folders:
          - events
    design:
      view: card
  - block: collection
    id: news
    content:
      title: Recent News
      subtitle: ''
      text: ''
      # Page type to display. E.g. post, talk, publication...
      page_type: blog
      # Choose how many pages you would like to display (0 = all pages)
      count: 10
      # Filter on criteria
      filters:
        author: ''
        category: ''
        tag: ''
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ''
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
    design:
      # Choose a layout view
      view: card
      # Reduce spacing
      spacing:
        padding: [0, 0, 0, 0]
---
