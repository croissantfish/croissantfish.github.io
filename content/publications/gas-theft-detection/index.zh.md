---
title: "Gas-Theft Suspect Detection Among Boiler Room Users: A Data-Driven Approach"

authors:
  - Xiuwen Yi
  - Xiaodu Yang
  - Yanyong Huang
  - Songyu Ke
  - Junbo Zhang
  - Tianrui Li
  - Yu Zheng

date: "2022-12-01T00:00:00Z"

publication_types: ["article-journal"]

publication: "*IEEE Transactions on Knowledge and Data Engineering*, 34(12), 5796--5808"
publication_short: "*IEEE TKDE* 34(12)"

abstract: "The natural gas tightly correlates with our everyday life. However, driven by gray incomes, some users are prone to stealing gas by refitting the equipment without permission. Especially for the boiler room users in winter, this phenomenon appears more rampant. Traditional gas-theft detection methods highly rely on the on-site inspection, where exists ineffective and randomness. With the rapidly deployed IoT sensors, we can collect real-time gas consumption data to analyze users' behavior patterns, where the gas-theft suspects could be discovered early and accurately. In this paper, we propose a data-driven approach, named SVOC, to detect gas-theft suspects among boiler room users. Our approach consists of a scenario-based data quality detection algorithm, a deformation-based normality detection algorithm, and an One-Class Support Vector Machine (OCSVM) based anomaly detection algorithm. Specifically, considering the temporal proximity between the gas consumption and the outdoor temperature, the normality detection algorithm adopts a similarity-based deformation correlation to detect normal boiler room users out of abnormal ones. Then, we employ OCSVM as the anomaly detection algorithm to capture various features across multiple data sources, aiming to distinguish gas-theft suspects from the remaining irregular users. Here, the detected normal and abnormal users are fed into the OCSVM for training and prediction, respectively, which can overcome the label scarcity problem. We conduct extensive experiments on a real-world dataset during one heating season. The results demonstrate distinct advantages of our approach over various baselines. We have developed a real-time system on the cloud, providing daily gas-theft suspects for gas companies."

tags:
  - Anomaly Detection
  - IoT Data Analysis
  - Urban Computing
  - Data-Driven Approach

featured: true

hugoblox:
  ids:
    doi: "10.1109/TKDE.2021.3110504"

links:
  - type: pdf
    url: "https://ieeexplore.ieee.org/document/9511956"

projects: []

slides: ""
---

This paper was published in [IEEE TKDE](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=69).
