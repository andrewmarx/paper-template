---
title: "Really Cool Title"
abstract: "A mind-blowing abstract."
author:
  - First Name
  - Second Name
  - Third Name


# Bibliography settings

bibliography:
  - ./res/bib/bibliography.bib
csl: ./res/csl/ecology.csl
link-citations: true


# Formatting

documentclass: article
fontsize: 12pt
geometry: margin=1.0in
#geometry: "left=3cm,right=3cm,top=2cm,bottom=2cm"
header-includes:
  - \usepackage{times}
  - \usepackage[mathlines,displaymath]{lineno}
  - \linenumbers
urlcolor: blue



# Output

output:
  pdf_document:
    toc: false
    number_sections: false
---

# Introduction

Test citation [@Waples2015]

Second test citation by @Waples2015

Inline math $a^2 + b^2 = c^2$

Math on it's own line: $$a^2 + b^2 = c^2$$

Math on it's own line with automatic numbering: $$a^2 + b^2 = c^2$$ {#eq:description}

Referring to equation @eq:description


# Methods

# Results

# Discussion

# References

*If everything is setup correctly, references are automatically appended to the end of the document*
