---
title: "Can Reasoning Help Large Language Models Capture Human Annotator Disagreement?"
authors:
- "Jingwei Ni"
- "Yu Fan"
- "Vilém Zouhar"
- "Donya Rooein"
- "Alexander Miserlis Hoyle"
- "Mrinmaya Sachan"
- "Markus Leippold"
- "Dirk Hovy"
- "Elliott Ash"
date: 2026-03-01
doi: "10.18653/v1/2026.eacl-long.3"
publishDate: 2026-03-01
publication_types:
- "1"
publication: "Proceedings of the 19th Conference of the European Chapter of the Association for Computational Linguistics (Volume 1: Long Papers)"
publication_short: "EACL 2026"
abstract: >-
  Variation in human annotation (i.e., disagreements) is common in NLP, often reflecting important information
  like task subjectivity and sample ambiguity. Modeling this variation is important for applications that are
  sensitive to such information. Although RLVR-style reasoning (Reinforcement Learning with Verifiable Rewards)
  has improved Large Language Model (LLM) performance on many tasks, it remains unclear whether such reasoning
  enables LLMs to capture informative variation in human annotation. In this work, we evaluate the influence of
  different reasoning settings on LLM disagreement modeling. We systematically evaluate each reasoning setting
  across model sizes, distribution expression methods, and steering methods, resulting in 60 experimental setups
  across 3 tasks. Surprisingly, our results show that RLVR-style reasoning degrades performance in disagreement
  modeling, while naive Chain-of-Thought (CoT) reasoning improves the performance of RLHF LLMs (RL from human
  feedback). These findings underscore the potential risk of replacing human annotators with reasoning LLMs,
  especially when disagreements are important.
summary: ""
tags:
- "Annotator Disagreement"
- "Reasoning"
- "LLMs"
- "Human Annotation"
categories: []
featured: false
url_pdf: "https://aclanthology.org/2026.eacl-long.3.pdf"
url_code: ""
url_dataset: ""
url_poster: ""
url_project: ""
url_slides: ""
url_source: ""
url_video: ""
socialmedia_post: ""
image:
  caption: ""
  focal_point: Center
  preview_only: false
projects: []
slides: ""
---
