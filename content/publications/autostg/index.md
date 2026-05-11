---
title: "AutoSTG: Neural Architecture Search for Predictions of Spatio-Temporal Graph"

authors:
  - Zheyi Pan
  - me
  - Xiaodu Yang
  - Yuxuan Liang
  - Yong Yu
  - Junbo Zhang
  - Yu Zheng

date: "2021-04-01T00:00:00Z"

publication_types: ["paper-conference"]

publication: "In *Proceedings of the Web Conference 2021 (WWW 2021)*"
publication_short: "In *WWW 2021*"

abstract: "Spatio-temporal graphs are important structures to describe urban sensory data, e.g., traffic speed and air quality. Predicting over spatio-temporal graphs enables many essential applications in intelligent cities, such as traffic management and environment analysis. Recently, many deep learning models have been proposed for spatio-temporal graph prediction and achieved significant results. However, designing neural networks requires rich domain knowledge and expert efforts. To this end, we study automated neural architecture search for spatio-temporal graphs with the application to urban traffic prediction, which meets two challenges: 1) how to define search space for capturing complex spatio-temporal correlations; and 2) how to learn network weight parameters related to the corresponding attributed graph of a spatio-temporal graph. To tackle these challenges, we propose a novel framework, entitled AutoSTG, for automated spatio-temporal graph prediction. In our AutoSTG, spatial graph convolution and temporal convolution operations are adopted in our search space to capture complex spatio-temporal correlations. Besides, we employ the meta learning technique to learn the adjacency matrices of spatial graph convolution layers and kernels of temporal convolution layers from the meta knowledge of the attributed graph. And specifically, such meta knowledge is learned by a graph meta knowledge learner that iteratively aggregates knowledge on the attributed graph. Finally, extensive experiments were conducted on two real-world benchmark datasets to demonstrate that AutoSTG can find effective network architectures and achieve state-of-the-art results. To the best of our knowledge, we are the first to study neural architecture search for spatio-temporal graphs."

tags:
  - Neural Architecture Search
  - Spatio-Temporal Graph
  - Meta Learning
  - Traffic Prediction

featured: true

hugoblox:
  ids:
    doi: "10.1145/3442381.3449816"

links:
  - type: pdf
    url: "http://urban-computing.com/pdf/WWW2021AutoSTG.pdf"
  - type: code
    url: "https://github.com/panzheyi/AutoSTG"

projects: []

slides: ""
---

This paper was published in [WWW 2021](https://www2021.thewebconf.org/).
