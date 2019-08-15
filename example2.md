---
title: "Manuscript Starting Point"
abstract: "This example is based on the PLOS blog post titled *[A Brief Guide To Writing Your First Scientific Manuscript](https://blogs.plos.org/scicomm/2018/03/07/a-brief-guide-to-writing-your-first-scientific-manuscript/)*. Basic sections are setup with a brief description/questions, and your goal is to create an outline for each one as a starting point for your own manuscript. This is just part of the process described in the article, so check it out for the rest."
author:
  - First Name
  - Second Name
  - Third Name


# Bibliography Settings

bibliography:
  - ./res/bib/bibliography.bib
csl: ./res/csl/ecology.csl
link-citations: true


# Formatting Settings

documentclass: article
fontsize: 12pt
geometry: margin=1.0in
#geometry: "left=3cm,right=3cm,top=2cm,bottom=2cm"
header-includes:
  - \usepackage{times}
  - \usepackage[mathlines,displaymath]{lineno}
  - \linenumbers
urlcolor: blue


# Output Settings

output:
  pdf_document:
    toc: false
    number_sections: false
---


# Introduction

*"What did you study, and why is it important? What is your hypothesis/research question?"*

- Item
    - Sub-item
    - Sub-item
- Item
- Item


# Methods

*"What techniques did you use? Each technique should be its own bullet, with sub-bullets for key details. If you used animal or human subjects, include a bullet on ethics approval. Important methodologies and materials, i.e., blinding for subjective analyses, full names of cell lines/strains/reagents and your commercial/academic sources for them."*

1. Numbered Item
    1. Numbered Sub-item
    1. Numbered Sub-item
1. Numbered Item
    - Sub-item
    - Sub-item
1. Numbered Item


# Results

*"What were your findings? Each major finding should be its own bullet, with sub-bullets going into more detail for each major finding. These bullets should refer to your figures."*

# Discussion

*"Summarize your findings in the context of prior work. Discuss possible interpretations. It is important to include a bullet describing the limitations of the presented work. Mention possible future directions."*
